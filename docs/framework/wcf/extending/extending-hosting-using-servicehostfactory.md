---
description: 詳細については、「ServiceHostFactory を使用したホスティングの拡張」をご覧ください。
title: ServiceHostFactory を使用したホストの拡張
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: cd7749a153f23586bbf570eaf97f5ae849fc522d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735141"
---
# <a name="extending-hosting-using-servicehostfactory"></a>ServiceHostFactory を使用したホストの拡張

<xref:System.ServiceModel.ServiceHost>Windows Communication Foundation (wcf) でサービスをホストするための標準 API は、wcf アーキテクチャの機能拡張ポイントです。 ユーザーは、この <xref:System.ServiceModel.ServiceHost> の派生型として独自のホスト クラスを定義できます。通常は、<xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> を使用するために <xref:System.ServiceModel.Description.ServiceDescription> をオーバーライドして、これにより、サービスを開く前に、強制的に既定のエンドポイントを追加したり、動作を変更することができます。  
  
 自己ホスト環境では、カスタムの <xref:System.ServiceModel.ServiceHost> を作成する必要はありません。ホストをインスタンス化し、インスタンス化の後で <xref:System.ServiceModel.ICommunicationObject.Open> を呼び出すコードを記述するので、 この 2 つのステップの間に任意の処理を記述できます。 たとえば、新しい <xref:System.ServiceModel.Description.IServiceBehavior> を次のように追加できます。  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 この方法は再利用できません。 説明を操作するコードはホスト プログラム (この場合は Main() 関数) に記述されているので、このロジックを別のコンテキストで使用するのは困難です。 このような強制コードを記述することなく、<xref:System.ServiceModel.Description.IServiceBehavior> を追加する方法もあります。 <xref:System.ServiceModel.ServiceBehaviorAttribute> から派生した属性をサービス実装型に組み込む方法や、カスタム動作の詳細を構成できるようにしておき、構成を使用して動的に組み込む方法が考えられます。  
  
 ただし、サンプル コードを少し修正して問題を解決することもできます。 1 つの方法として、ServiceBehavior を追加するコードを `Main()` 内に記述する代わりに、<xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> から派生した <xref:System.ServiceModel.ServiceHost> メソッドに記述することができます。  
  
```csharp
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 `Main()` 内には、次のように記述できます。  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 このようにカスタム ロジックをカプセル化、抽象化すると、さまざまなホスト アプリケーションで再利用できます。  
  
 カスタムの <xref:System.ServiceModel.ServiceHost> を Internet Information Services (IIS) や Windows Process Activation Service (WAS) で使用する方法は、それほど単純ではありません。 アプリケーションの代わりにホスティング環境が <xref:System.ServiceModel.ServiceHost> をインスタンス化するという点で、これらの環境は、自己ホスト環境と異なっています。 IIS および WAS ホスティング インフラストラクチャは、<xref:System.ServiceModel.ServiceHost> のカスタム派生物については何も認識しません。  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> は、独自に定義した <xref:System.ServiceModel.ServiceHost> の派生クラスに、IIS または WAS からアクセスする手段として設計されました。 <xref:System.ServiceModel.ServiceHost> から派生したカスタム ホストは、動的に構成され、種類もさまざまであるため、ホスト環境でこれを直接インスタンス化することはありません。 代わりに、WCF はファクトリパターンを使用して、ホスト環境とサービスの具象型の間に間接レイヤーを提供します。 特に指定しなければ、<xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す、<xref:System.ServiceModel.ServiceHost> の既定の実装が使用されます。 ただし、ディレクティブでファクトリ実装の CLR 型名を指定することによって、派生ホストを返す独自のファクトリを指定することもできます @ServiceHost 。  
  
 基本的なケースでは、独自のファクトリは容易に実装できます。 派生 <xref:System.ServiceModel.Activation.ServiceHostFactory> を返す、カスタムの <xref:System.ServiceModel.ServiceHost> の例を次に示します。  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 既定のファクトリの代わりにこのファクトリを使用するには、次のようにディレクティブに型名を指定し @ServiceHost ます。  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <xref:System.ServiceModel.ServiceHost> から返す <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A> で行う処理について、技術的には制限はありませんが、ファクトリ実装はできるだけ単純にしておくことをお勧めします。 多くのカスタムロジックがある場合は、そのロジックをファクトリ内部ではなくホスト内に配置して、再利用できるようにすることをお勧めします。  
  
 ここで、ホスティング API にはもう 1 つのレイヤーがあることを知っておく必要があります。 また、WCF にはともあります。このとは、 <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> <xref:System.ServiceModel.ServiceHost> それぞれとを派生させたもの <xref:System.ServiceModel.Activation.ServiceHostFactory> です。 これらは、メタデータ システムの大部分がカスタム コードに置き換わるような、高度なシナリオを想定して用意されています。
