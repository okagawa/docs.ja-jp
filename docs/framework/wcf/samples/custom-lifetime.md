---
description: '詳細情報: カスタム有効期間'
title: カスタム有効期間
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 24845aaa20e60f92e2add568c81ab3d6502ebedf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732476"
---
# <a name="custom-lifetime"></a>カスタム有効期間

このサンプルでは、Windows Communication Foundation (WCF) 拡張機能を記述して、共有 WCF サービスインスタンスにカスタムの有効期間サービスを提供する方法を示します。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、この記事の最後を参照してください。

## <a name="shared-instancing"></a>共有インスタンス化

WCF には、サービスインスタンスに対して複数のインスタンス化モードが用意されています。 この記事で説明されている共有インスタンス化モードでは、複数のチャネル間でサービスインスタンスを共有する方法を提供します。 クライアントは、サービスのファクトリメソッドに接続して、通信を開始するための新しいチャネルを作成できます。 次のコードスニペットは、クライアントアプリケーションが既存のサービスインスタンスへの新しいチャネルを作成する方法を示しています。

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

他のインスタンス化モードとは異なり、共有インスタンス化モードでは、独特の方法でサービス インスタンスを解放します。 既定では、すべてのチャネルがに対して閉じられると、 <xref:System.ServiceModel.InstanceContext> WCF サービスランタイムは、サービスがまたはに構成されているかどうかを確認し、 <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerCall> インスタンスを解放してリソースを要求するかどうかを確認し <xref:System.ServiceModel.InstanceContextMode.PerSession> ます。 カスタム <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> が使用されている場合、WCF は、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> インスタンスを解放する前に、プロバイダーの実装のメソッドを呼び出します。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>がを返した場合、 `true` インスタンスは解放されます。それ以外の場合、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、 `Dispatcher` コールバックメソッドを使用してアイドル状態のに通知を行います。 これは、プロバイダーのメソッドを呼び出すことによって行われ <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> ます。

このサンプルでは、 <xref:System.ServiceModel.InstanceContext> アイドルタイムアウトが20秒のの解放を遅延させる方法を示します。

## <a name="extending-the-instancecontext"></a>InstanceContext の拡張

WCF で <xref:System.ServiceModel.InstanceContext> は、はサービスインスタンスとの間のリンクです `Dispatcher` 。 WCF では、拡張可能なオブジェクトパターンを使用して新しい状態または動作を追加することで、このランタイムコンポーネントを拡張できます。 拡張可能オブジェクトパターンは、既存のランタイムクラスを新しい機能で拡張するか、オブジェクトに新しい状態機能を追加するために WCF で使用されます。 拡張可能オブジェクト パターンには、<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601>、および <xref:System.ServiceModel.IExtensionCollection%601> の 3 つのインターフェイスがあります。

インターフェイスは、 <xref:System.ServiceModel.IExtensibleObject%601> 機能をカスタマイズする拡張を可能にするために、オブジェクトによって実装されます。

<xref:System.ServiceModel.IExtension%601> インターフェイスは、`T` 型のクラスの拡張が可能なオブジェクトによって実装されます。

最後に、 <xref:System.ServiceModel.IExtensionCollection%601> インターフェイスは、 <xref:System.ServiceModel.IExtension%601> <xref:System.ServiceModel.IExtension%601> 型によっての実装を取得できるようにする実装のコレクションです。

したがって、を拡張するには、 <xref:System.ServiceModel.InstanceContext> インターフェイスを実装する必要があり <xref:System.ServiceModel.IExtension%601> ます。 このサンプルプロジェクトでは、 `CustomLeaseExtension` クラスにこの実装が含まれています。

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<xref:System.ServiceModel.IExtension%601> インターフェイスには、<xref:System.ServiceModel.IExtension%601.Attach%2A> と <xref:System.ServiceModel.IExtension%601.Detach%2A> の 2 つのメソッドが含まれています。 名前が示すように、これらの 2 つのメソッドは、ランタイムが <xref:System.ServiceModel.InstanceContext> クラスのインスタンスに拡張機能を関連付けるときと関連付けを解除するときに呼び出されます。 このサンプルでは、`Attach` メソッドを使用して、拡張機能の現在のインスタンスに属する <xref:System.ServiceModel.InstanceContext> オブジェクトを追跡します。

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

また、有効期間の延長をサポートするには、必要な実装を拡張機能に追加する必要があります。 したがって、 `ICustomLease` インターフェイスは目的のメソッドを使用して宣言され、クラスに実装され `CustomLeaseExtension` ます。

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> が実装でメソッドを呼び <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 出すと、この呼び出しはのメソッドにルーティングされ <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `CustomLeaseExtension` ます。 次に、はその `CustomLeaseExtension` プライベート状態をチェックして、がアイドル状態かどうかを確認し <xref:System.ServiceModel.InstanceContext> ます。 アイドル状態の場合は、を返し `true` ます。 それ以外の場合は、延長された指定の有効期間のタイマーが開始されます。

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

タイマーのイベントで `Elapsed` は、別のクリーンアップサイクルを開始するために、ディスパッチャーのコールバック関数が呼び出されます。

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

インスタンスをアイドル状態に移行するために新しいメッセージが到着したときに、実行中のタイマーを更新する方法はありません。

このサンプルでは、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドの呼び出しを受け取って <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> にルーティングするために `CustomLeaseExtension` を実装します。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、`CustomLifetimeLease` クラスに含まれています。 メソッドは、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF がサービスインスタンスを解放しようとしているときに呼び出されます。 ただし、ServiceBehavior の `ISharedSessionInstance` コレクションに存在する特定の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装のインスタンスは 1 つだけです。 つまり、WCF によって <xref:System.ServiceModel.InstanceContext> メソッドがチェックされるときにが閉じられているかどうかを知る方法はありません <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 。 したがって、このサンプルでは、スレッドロックを使用して、メソッドに要求をシリアル化し <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> ます。

> [!IMPORTANT]
> シリアル化はアプリケーションのパフォーマンスに大きな影響を及ぼす可能性があるので、スレッド ロックは使用しないことをお勧めします。

プライベートメンバーフィールドは、 `CustomLifetimeLease` アイドル状態を追跡するためにクラスで使用され、メソッドによって返され <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> ます。 メソッドが呼び出されるたびに、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `isIdle` フィールドが返され、にリセットされ `false` ます。  ディスパッチャーが `false` メソッドを呼び出すようにするには、この値を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> に設定する必要があります。

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> を返す場合 `false` 、ディスパッチャーはメソッドを使用してコールバック関数を登録し <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> ます。 このメソッドは、解放される <xref:System.ServiceModel.InstanceContext> への参照を受け取ります。 このため、サンプルコードでは、型拡張に対してクエリを実行し、拡張され `ICustomLease` た状態のプロパティを確認でき `ICustomLease.IsIdle` ます。

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

プロパティをチェックする前に `ICustomLease.IsIdle` 、コールバックプロパティを設定する必要があります。これは、が `CustomLeaseExtension` アイドル状態になったときにディスパッチャーに通知するために必要です。 `ICustomLease.IsIdle` が `true` を返す場合は、`isIdle` プライベート メンバーが `CustomLifetimeLease` で単に `true` に設定され、コールバック メソッドが呼び出されます。 コードはロックを保持しているため、他のスレッドがこのプライベートメンバーの値を変更することはできません。 次にディスパッチャーがを呼び出すときに、を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> 返し、ディスパッチャーがインスタンスを解放できるようにし `true` ます。

これでカスタム拡張機能の基礎が完成したので、この拡張機能をサービス モデルにフックする必要があります。 実装をにフックするために、WCF には `CustomLeaseExtension` <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> のブートストラップを実行するためのインターフェイスが用意されて <xref:System.ServiceModel.InstanceContext> います。 このサンプルでは、`CustomLeaseInitializer` クラスでこのインターフェイスを実装し、`CustomLeaseExtension` のインスタンスを唯一のメソッドの初期化から得られる <xref:System.ServiceModel.InstanceContext.Extensions%2A> コレクションに追加します。 このメソッドは、<xref:System.ServiceModel.InstanceContext> の初期化中にディスパッチャーによって呼び出されます。

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 最後に、実装を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 使用して、サービスモデルに実装をフックし <xref:System.ServiceModel.Description.IServiceBehavior> ます。 この実装は、`CustomLeaseTimeAttribute` クラスに配置されています。また、<xref:System.Attribute> 基本クラスから派生してこの動作を属性として公開します。

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

この動作は、`CustomLeaseTime` 属性を使用して注釈を付けることにより、サンプル サービス クラスに追加できます。

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。

### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。

2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。

3. サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
