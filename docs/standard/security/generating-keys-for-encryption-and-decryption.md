---
title: 暗号化と復号化のためのキーの生成
description: .NET で暗号化と復号化を行うための対称キーと非対称キーを作成して管理する方法について説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: f8c3633d18e200037235502487d0d91d42083241
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661810"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>暗号化と復号化のためのキーの生成
キーの作成と管理は、暗号プロセスの重要な部分です。 対称アルゴリズムでは、キーと初期化ベクター (IV) を作成する必要があります。 キーは、データの暗号化解除を許可しないユーザーに対しては秘密にする必要があります。 IV は秘密にする必要はありませんが、セッションごとに変更する必要があります。 非対称アルゴリズムでは、公開キーと秘密キーを作成する必要があります。 公開キーはだれに公開してもかまいせんが、秘密キーを知らせる相手は、公開キーで暗号化されたデータを復号化する人だけにします。 このセクションでは、対称アルゴリズムと非対称アルゴリズムの両方について、キーを作成して管理する方法を説明します。  
  
## <a name="symmetric-keys"></a>対称キー  
 .NET Framework に用意されている対称暗号化クラスでは、データを暗号化および復号化するために、キーと新しい初期化ベクター (IV) が必要になります。 パラメーターなしのコンストラクターを使用して、いずれかのマネージ対称暗号化クラスの新しいインスタンスを作成するたびに、新しいキーと IV が自動的に作成されます。 自分のデータを復号化できるようにする相手は、自分と同じキーおよび IV を所有し、同じアルゴリズムを使用する必要があります。 一般に、キーと IV はセッションごとに新しく作成する必要があり、キーも IV も格納して後のセッションで使用することは望ましくありません。  
  
 通常、共通キーと IV を離れた場所にいる人へ送信するためには、非対称暗号化方式を使用して共通キーを暗号化します。 これらの値を暗号化せずに安全でないネットワーク経由で送信することは、値を傍受した人ならだれでもデータを暗号化解除できるようになるため危険です。 暗号化を使用したデータ交換の詳細については、「 [暗号スキームの作成](creating-a-cryptographic-scheme.md)」を参照してください。  
  
 TripleDES アルゴリズムを実装する <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> クラスの新しいインスタンスの作成方法を次の例に示します。  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 上記のコードを実行すると新しいキーと IV が生成され、それぞれ **Key** プロパティと **IV** プロパティに設定されます。  
  
 複数のキーを生成する必要が生じることもあります。 このような状況では、対称アルゴリズムを実装するクラスの新しいインスタンスを作成し、次に **GenerateKey** および **GenerateIV** メソッドを呼び出すことによって新しいキーと IV を作成します。 次のコード例は、対称暗号化クラスの新しいインスタンスが作成された後に、新しいキーと Iv を作成する方法を示しています。  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 上記のコードを実行すると、 **TripleDESCryptoServiceProvider** の新しいインスタンスの作成時にキーと IV が生成されます。 **GenerateKey** メソッドと **GenerateIV** メソッドを呼び出すと、別のキーと IV が作成されます。  
  
## <a name="asymmetric-keys"></a>非対称キー  
 .NET Framework には、非対称暗号化方式のための <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスと <xref:System.Security.Cryptography.DSACryptoServiceProvider> クラスが用意されています。 これらのクラスは、パラメーターなしのコンストラクターを使用して新しいインスタンスを作成するときに、公開キーと秘密キーのペアを作成します。 非対称キーは、複数のセッションで使用できるように格納したり、1 つのセッション専用として生成したりできます。 公開キーは一般に公開できますが、秘密キーは厳密に保護する必要があります。  
  
 非対称アルゴリズム クラスの新しいインスタンスを作成すると、公開キーと秘密キーのペアが常に生成されます。 クラスの新しいインスタンスを作成したら、次の 2 つの方法のどちらかを使ってキー情報を取得できます。  
  
- <xref:System.Security.Cryptography.RSA.ToXmlString%2A> メソッド。キー情報の XML 表現を返します。  
  
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> メソッド。キー情報を保持する <xref:System.Security.Cryptography.RSAParameters> 構造体を返します。  
  
 どちらのメソッドにも、公開キー情報だけを返すのか、または公開キー情報と秘密キー情報の両方を返すのかを示すブール値を渡すことができます。 **メソッドを使用すると、** RSACryptoServiceProvider **クラスを初期化して** RSAParameters <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> 構造体の値を設定できます。  
  
 非対称秘密キーは、ローカル コンピューターにそのまま平文として保存しないでください。 秘密キーを格納する必要がある場合は、キー コンテナーを使用することをお勧めします。 秘密キーをキー コンテナーに格納する方法の詳細については、「 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)」を参照してください。  
  
 次のコード例では、 **RSACryptoServiceProvider** クラスの新しいインスタンスを作成し、公開キーと秘密キーのペアを作成して、公開キー情報を **RSAParameters** 構造体に保存します。  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>関連項目

- [データの暗号化](encrypting-data.md)
- [データの復号化](decrypting-data.md)
- [暗号化サービス](cryptographic-services.md)
- [方法: キー コンテナーに非対称キーを格納する](how-to-store-asymmetric-keys-in-a-key-container.md)
