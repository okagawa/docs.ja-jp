---
title: カスタム ストリームのアップグレード
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: 3ef0f59a5d63c24188b29cb7a38db2d6323d80ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295582"
---
# <a name="custom-stream-upgrades"></a>カスタム ストリームのアップグレード

TCP、名前付きパイプなど、ストリーム指向のデータ伝送機構 (トランスポート) が扱うのは、クライアントとサーバーの間を流れる、連続的なバイト ストリームです。 このストリームを実際に作り出すのは <xref:System.IO.Stream> オブジェクトです。 ストリーム アップグレードでは、クライアントは、オプションのプロトコル階層をチャネル スタックに追加する場合に、相手側の通信チャネルにも同じことをするよう要求します。 ストリーム アップグレードは、<xref:System.IO.Stream> オブジェクトをアップグレードされたものに置き換える形で実施します。  
  
 たとえば、トランスポート ストリームのすぐ上に圧縮ストリームを作成することができます。 この場合、元のトランスポート <xref:System.IO.Stream> を、それを圧縮 <xref:System.IO.Stream> でラップしたものに置き換えます。  
  
 オブジェクトを順にラップしていくことにより、ストリーム アップグレードを多重に適用できます。  
  
## <a name="how-stream-upgrades-work"></a>ストリーム アップグレードの動作  

 ストリーム アップグレード処理には 4 つのコンポーネントが関与します。  
  
1. アップグレードストリームの *イニシエーター* は、プロセスを開始します。実行時には、接続の相手側に要求を開始してチャネルトランスポート層をアップグレードできます。  
  
2. アップグレードストリーム *アクセプタ* は、アップグレードを実行するときに、他のコンピューターからのアップグレード要求を受信します。可能な場合は、アップグレードを受け入れます。  
  
3. アップグレード *プロバイダー* によって、クライアント上の *イニシエーター* と、サーバー上の *アクセプタ* が作成されます。  
  
4. ストリームアップグレードの *バインド要素* がサービスとクライアントのバインディングに追加され、実行時にプロバイダーが作成されます。  
  
 なお、多重にアップグレードを適用する場合、イニシエーターとアクセプタはステート マシンをカプセル化して、適切な適用順序になるようにします。  
  
## <a name="how-to-implement-a-stream-upgrade"></a>ストリーム アップグレードの実装方法  

 Windows Communication Foundation (WCF) には、実装できる4つのクラスが用意され `abstract` ています。  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 カスタム ストリーム アップグレードを実装する手順を以下に示します。 これは、クライアント側、サーバー側双方に、ごく単純なストリーム アップグレード処理を組み込む場合の手順です。  
  
1. <xref:System.ServiceModel.Channels.StreamUpgradeInitiator> を実装するクラスを作成します。  
  
    1. <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> メソッドをオーバーライドして、ストリームを入力すると、それをアップグレードしたストリームが返されるようにします。 これは同期型のメソッドですが、これに似た非同期型のメソッドもあります。  
  
    2. <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> メソッドをオーバーライドして、追加のアップグレードがないか確認するようにします。  
  
2. <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor> を実装するクラスを作成します。  
  
    1. <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> メソッドをオーバーライドして、ストリームを入力すると、それをアップグレードしたストリームが返されるようにします。 これは同期型のメソッドですが、これに似た非同期型のメソッドもあります。  
  
    2. <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> メソッドをオーバーライドして、アップグレード処理中のこの時点で、このアップグレード アクセプタがアップグレード要求に応じることができるかどうかを判断するようにします。  
  
3. <xref:System.ServiceModel.Channels.StreamUpgradeProvider> を実装するクラスを作成します。 <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> メソッドおよび <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> メソッドをオーバーライドして、手順 1. および 2. で定義したアクセプタとイニシエーターのインスタンスをそれぞれ返すようにします。  
  
4. <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> を実装するクラスを作成します。  
  
    1. クライアント側の <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> メソッドとサービス側の <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> メソッドをオーバーライドします。  
  
    2. クライアント側の <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> メソッドとサービス側の <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> メソッドをオーバーライドして、アップグレード バインド要素を <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A> に追加するようにします。  
  
5. サーバー側とクライアント側のバインディングに、新しいストリーム アップグレード バインド要素を追加します。  
  
## <a name="security-upgrades"></a>セキュリティ アップグレード  

 ストリーム アップグレードの特別な場合として、セキュリティ アップグレードがあります。  
  
 WCF には、ストリームセキュリティをアップグレードするためのバインド要素が既に2つ用意されています。 トランスポート レベルのセキュリティ構成は、<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> および <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> にカプセル化されており、これらの要素を構成して、カスタム バインドに追加することができます。 この 2 つのバインド要素は、クライアント側およびサーバー側のストリーム アップグレード プロバイダーを構築する <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> クラスを拡張したものです。 これらのバインド要素には、セキュリティ ストリーム アップグレード専用のプロバイダー クラスを作成するメソッドが定義されています。これらのメソッドは `public` ではないので、いずれの場合もバインド要素をバインディングに追加するだけでセキュリティ アップグレードが可能です。  
  
 上記の 2 つのバインド要素では対応できないセキュリティ上の要求に備え、既述のイニシエーター、アクセプタ、プロバイダーの各基底クラスから派生した `abstract` クラスが 3 つ定義されています。  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 セキュリティ ストリーム アップグレードを実装する手順も、以上 3 つのクラスから派生することを除き、一般のストリーム アップグレードと同様です。 これらのクラスには実行時にセキュリティ情報をやり取りするためのプロパティが追加されているので、これをオーバーライドしてください。  
  
## <a name="multiple-upgrades"></a>多重アップグレード  

 追加のアップグレード要求を作成するには、前述の手順を繰り返して、追加の <xref:System.ServiceModel.Channels.StreamUpgradeProvider> およびバインド要素の拡張を作成し、 これをバインディングに追加します。 各バインド要素は、バインディングに追加した順に処理されます。 各アップグレード プロバイダーは、<xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> および <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> で、既存のアップグレード バインディング パラメーターに、どのように自分自身を積み重ねるかを指定できます。 次に、既存のアップグレード バインディング パラメーターを、新しい複合アップグレード バインディング パラメーターに置き換えます。  
  
 あるいは、単一のアップグレード プロバイダーで、多重のアップグレードに対応することも可能です。 たとえば、セキュリティと圧縮の両方に対応するカスタム ストリーム アップグレード プロバイダーを実装できます。 手順は次のとおりです。  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> のサブクラスとして、イニシエーターおよびアクセプタを生成するプロバイダー クラスを作成します。  
  
2. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> のサブクラスを作成し、<xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> メソッドをオーバーライドして、圧縮ストリーム、セキュリティ ストリームの順にコンテンツ タイプを返すようにします。  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> のサブクラスを作成し、<xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> メソッドをオーバーライドして、独自のコンテンツ タイプに応じた処理をするようにします。  
  
4. ストリームは、<xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> および <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> をそれぞれ呼び出した後にアップグレードされます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
