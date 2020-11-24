---
title: 暗号化と復号化のためのキーの生成
description: .NET で暗号化と復号化を行うための対称キーと非対称キーを作成して管理する方法について説明します。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 2af54cef4f233b7bcae5c476f1aa49fdbf7ef2fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689720"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>暗号化と復号化のためのキーの生成

キーの作成と管理は、暗号プロセスの重要な部分です。 対称アルゴリズムでは、キーと初期化ベクター (IV) を作成する必要があります。 キーは、データの暗号化解除を許可しないユーザーに対しては秘密にする必要があります。 IV は秘密にする必要はありませんが、セッションごとに変更する必要があります。 非対称アルゴリズムでは、公開キーと秘密キーを作成する必要があります。 公開キーはだれに公開してもかまいせんが、秘密キーを知らせる相手は、公開キーで暗号化されたデータを復号化する人だけにします。 このセクションでは、対称アルゴリズムと非対称アルゴリズムの両方について、キーを作成して管理する方法を説明します。  
  
## <a name="symmetric-keys"></a>対称キー  

 .NET によって提供される対称暗号化クラスでは、データを暗号化および復号化するために、キーと新しい初期化ベクター (IV) が必要です。 パラメーターなしのメソッドを使用して、いずれかのマネージ対称暗号化クラスの新しいインスタンスを作成するたびに、 `Create()` 新しいキーと IV が自動的に作成されます。 自分のデータを復号化できるようにする相手は、自分と同じキーおよび IV を所有し、同じアルゴリズムを使用する必要があります。 一般に、キーと IV はセッションごとに新しく作成する必要があり、キーも IV も格納して後のセッションで使用することは望ましくありません。  
  
 通常、共通キーと IV を離れた場所にいる人へ送信するためには、非対称暗号化方式を使用して共通キーを暗号化します。 これらの値を暗号化せずに安全でないネットワーク経由で送信することは、値を傍受した人ならだれでもデータを暗号化解除できるようになるため危険です。  
  
 次の例は、アルゴリズムの既定の実装クラスの新しいインスタンスを作成する方法を示して <xref:System.Security.Cryptography.Aes> います。  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 上記のコードを実行すると新しいキーと IV が生成され、それぞれ **Key** プロパティと **IV** プロパティに設定されます。  
  
 複数のキーを生成する必要が生じることもあります。 このような状況では、対称アルゴリズムを実装するクラスの新しいインスタンスを作成し、次に **GenerateKey** および **GenerateIV** メソッドを呼び出すことによって新しいキーと IV を作成します。 次のコード例は、対称暗号化クラスの新しいインスタンスが作成された後に、新しいキーと Iv を作成する方法を示しています。  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 上記のコードを実行すると、 **Aes** の新しいインスタンスが作成されるときにキーと IV が生成されます。 **GenerateKey** メソッドと **GenerateIV** メソッドを呼び出すと、別のキーと IV が作成されます。
  
## <a name="asymmetric-keys"></a>非対称キー

 .NET には、 <xref:System.Security.Cryptography.RSA> 非対称暗号化用のクラスが用意されています。 このクラスは、パラメーターなしのメソッドを使用して新しいインスタンスを作成するときに、公開キーと秘密キーのペアを作成し `Create()` ます。 非対称キーは、複数のセッションで使用できるように格納したり、1 つのセッション専用として生成したりできます。 公開キーは一般に公開できますが、秘密キーは厳密に保護する必要があります。  
  
 非対称アルゴリズム クラスの新しいインスタンスを作成すると、公開キーと秘密キーのペアが常に生成されます。 クラスの新しいインスタンスが作成された後、キー情報を <xref:System.Security.Cryptography.RSA.ExportParameters%2A> 保持する構造体を返すメソッドを使用して、キー情報を抽出でき <xref:System.Security.Cryptography.RSAParameters> ます。 メソッドは、公開キー情報だけを返すか、公開キーと秘密キーの両方の情報を返すかを示すブール値を受け取ります。

また、次のような重要な情報を抽出するためのメソッドもあります。

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

**RSA** インスタンスは、メソッドを使用して、 **RSAParameters** 構造体の値に初期化でき <xref:System.Security.Cryptography.RSA.ImportParameters%2A> ます。 または、メソッドを使用して新しいインスタンスを作成し <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> ます。  
  
 非対称秘密キーは、ローカル コンピューターにそのまま平文として保存しないでください。 秘密キーを格納する必要がある場合は、キー コンテナーを使用することをお勧めします。 秘密キーをキーコンテナーに格納する方法の詳細については、「 [方法: キーコンテナーに非対称キーを格納](how-to-store-asymmetric-keys-in-a-key-container.md)する」を参照してください。  
  
 次のコード例では、 **RSA** クラスの新しいインスタンスを作成し、公開キーと秘密キーのペアを作成して、公開キー情報を **RSAParameters** 構造体に保存します。  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>関連項目

- [データの暗号化](encrypting-data.md)
- [データの復号化](decrypting-data.md)
- [Cryptographic Services](cryptographic-services.md)
- [方法: キー コンテナーに非対称キーを格納する](how-to-store-asymmetric-keys-in-a-key-container.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- [データ保護の ASP.NET Core](/aspnet/core/security/data-protection/introduction)
