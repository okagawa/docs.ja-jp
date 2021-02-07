---
description: '詳細情報: 部分信頼のベストプラクティス'
title: 部分信頼のベスト プラクティス
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: abdc0fbbb84581b302bca8d514a5f8f5cc2703e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733555"
---
# <a name="partial-trust-best-practices"></a>部分信頼のベスト プラクティス

このトピックでは、Windows Communication Foundation (WCF) を部分信頼環境で実行する場合のベストプラクティスについて説明します。

## <a name="serialization"></a>シリアル化

部分信頼アプリケーションで <xref:System.Runtime.Serialization.DataContractSerializer> を使用する場合は、次の方法を適用します。

- すべてのシリアル化可能な型は、`[DataContract]` 属性で明示的にマークする必要があります。 次の手法は、部分信頼環境ではサポートされていません。

- シリアル化するクラスを <xref:System.SerializableAttribute> でマークする。

- クラスでシリアル化プロセスを制御できるように <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する。

### <a name="using-datacontractserializer"></a>DataContractSerializer の使用

- `[DataContract]` 属性でマークされたすべての型は、パブリックである必要があります。 部分信頼環境では、非パブリック型はシリアル化できません。

- シリアル化できる `[DataContract]` 型のすべての `[DataContract]` メンバーは、パブリックである必要があります。 部分信頼環境では、非パブリック `[DataMember]` 型はシリアル化できません。

- `OnSerializing`、`OnSerialized`、`OnDeserializing`、`OnDeserialized` などのシリアル化イベントを処理するメソッドは、パブリックとして宣言する必要があります。 ただし、明示的および暗黙的な <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> の実装は、いずれもサポートされています。

- `[DataContract]` は、逆シリアル化の間に新しくインスタンス化されたオブジェクトのコンストラクターを呼び出さないため、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> でマークされて、アセンブリで実装された <xref:System.Runtime.Serialization.DataContractSerializer> 型は、型コンストラクターでセキュリティ関連の操作を実行することはできません。 特に、`[DataContract]` 型では、次の一般的なセキュリティ手法の使用を避ける必要があります。

- 型のコンストラクターを内部またはプライベートにすることにより、部分信頼アクセスを制限する。

- 型のコンストラクターに `[LinkDemand]` を追加することにより、型へのアクセスを制限する。

- オブジェクトが正常にインスタンス化されたため、コンストラクターが強制するチェックがすべて正常に終了したと仮定する。

### <a name="using-ixmlserializable"></a>IXmlSerializable の使用

<xref:System.Xml.Serialization.IXmlSerializable> を実装し、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化される型に適用されるベスト プラクティスを次に示します。

- 静的 <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> メソッドの実装は、`public` とする必要があります。

- <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装するインスタンス メソッドは、`public` とする必要があります。

## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>部分信頼の呼び出し元から呼び出せる完全信頼のプラットフォーム コードで WCF を使用する

WCF 部分信頼セキュリティモデルでは、WCF のパブリックメソッドまたはプロパティの呼び出し元が、ホストアプリケーションのコードアクセスセキュリティ (CAS) コンテキストで実行されていることを前提としています。 また、WCF では、それぞれに対して1つのアプリケーションセキュリティコンテキストのみが存在 <xref:System.AppDomain> し、このコンテキストが信頼されたホストによって作成時に確立されることを前提としてい <xref:System.AppDomain> ます (たとえば、 <xref:System.AppDomain.CreateDomain%2A> または ASP.NET アプリケーションマネージャーによるまたはの呼び出しによって)。

このセキュリティ モデルは、信頼性が "中" の ASP.NET アプリケーションで実行されているユーザー コードなど、追加の CAS アクセス許可をアサートできないユーザー記述のアプリケーションに適用されます。 ただし、完全に信頼されたプラットフォームコード (たとえば、グローバルアセンブリキャッシュにインストールされ、部分信頼コードからの呼び出しを受け入れるサードパーティアセンブリ) は、部分的に信頼されたアプリケーションに代わって WCF を呼び出すときに、アプリケーションレベルのセキュリティの脆弱性が発生しないように、明示的に注意する必要があります。

完全信頼コードでは <xref:System.Security.PermissionSet.Assert%2A> 、 <xref:System.Security.PermissionSet.PermitOnly%2A> 部分的に信頼された <xref:System.Security.PermissionSet.Deny%2A> コードの代わりに WCF api を呼び出す前に、、、またはを呼び出して、現在のスレッドの CAS アクセス許可セットを変更しないようにする必要があります。 アプリケーション レベルのセキュリティ コンテキストに依存しないスレッド固有のアクセス許可コンテキストのアサート、拒否、または作成により、予期しない動作が発生することがあります。 アプリケーションによっては、この動作がアプリケーション レベルのセキュリティの脆弱性となることがあります。

スレッド固有のアクセス許可コンテキストを使用して WCF を呼び出すコードは、次のような状況に対処できるように準備する必要があります。

- スレッド固有のセキュリティ コンテキストを処理の期間全体にわたっては保持できない場合があり、このときセキュリティの例外が発生する可能性があります。

- 内部 WCF コードおよびユーザーが指定したコールバックは、呼び出し元が開始されたものとは異なるセキュリティコンテキストで実行される場合があります。 次のようなコンテキストが含まれます。

  - アプリケーションのアクセス許可コンテキスト。

  - 現在実行中のの有効期間中に WCF を呼び出すために使用された他のユーザースレッドによって以前に作成された、スレッド固有のアクセス許可コンテキスト。 <xref:System.AppDomain>

WCF パブリック Api を呼び出す前に、完全に信頼されたコンポーネントによってアサートされる場合を除き、部分信頼コードで完全信頼のアクセス許可を取得することはできません。 ただし、完全信頼をアサートした効果が特定のスレッド、操作、またはユーザー操作として隔離されることは保証されません。

<xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.PermitOnly%2A>、または <xref:System.Security.PermissionSet.Deny%2A> を呼び出すことにより、スレッド固有のアクセス許可コンテキストを作成しないことをお勧めします。 代わりに、<xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.Deny%2A>、または <xref:System.Security.PermissionSet.PermitOnly%2A> が不要となるように、アプリケーション自体に特権を付与するか、特権を拒否します。

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
