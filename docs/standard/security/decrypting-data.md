---
title: データの復号化
description: 対称アルゴリズムまたは非対称アルゴリズムを使用して、.NET でデータを復号化する方法について説明します。
ms.date: 07/16/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: cf286eeca8a9372c6532c56701e4775d5e09d786
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831105"
---
# <a name="decrypting-data"></a>データの復号化

復号化は、暗号化の逆の操作です。 秘密キーの暗号化では、データの暗号化に使用されたキーと IV の両方を把握しておく必要があります。 公開キーの暗号化では、公開キー (データが秘密キーで暗号化された場合) または秘密キー (データが公開キーで暗号化された場合) のいずれかを把握しておく必要があります。

## <a name="symmetric-decryption"></a>対称復号化

対称アルゴリズムで暗号化されたデータの復号化は、対称アルゴリズムでデータを暗号化する際に使用するプロセスと似ています。 クラスは、 <xref:System.Security.Cryptography.CryptoStream> 任意のマネージストリームオブジェクトから読み取られたデータの暗号化を解除するために .net によって提供される対称暗号化クラスと共に使用されます。

次の例は、アルゴリズムの既定の実装クラスの新しいインスタンスを作成する方法を示してい <xref:System.Security.Cryptography.Aes> ます。 インスタンスは、オブジェクトの復号化を実行するために使用され <xref:System.Security.Cryptography.CryptoStream> ます。 この例では、まず、実装クラスの新しいインスタンスを作成し <xref:System.Security.Cryptography.Aes> ます。 このメソッドは、マネージストリーム変数から初期化ベクター (IV) 値を読み取り `myStream` ます。 次 <xref:System.Security.Cryptography.CryptoStream> に、オブジェクトをインスタンス化し、インスタンスの値に初期化し `myStream` ます。 <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType>インスタンスのメソッドに <xref:System.Security.Cryptography.Aes> は、IV の値と、暗号化に使用されたキーが渡されます。

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

次の例は、ストリームの作成、ストリームの復号化、ストリームからの読み取り、およびストリームを閉じるプロセス全体を示しています。 *TestData.txt* という名前のファイルを読み取るファイルストリームオブジェクトが作成されます。 ファイルストリームは、 **CryptoStream** クラスと **Aes** クラスを使用して復号化されます。 この例では、 [データを暗号化](encrypting-data.md)するための対称暗号化の例で使用されるキー値を指定します。 これらの値の暗号化および転送に必要なコードは示されていません。

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

前の例では、 [データを暗号化](encrypting-data.md)するために、対称暗号化の例で使用されているのと同じキーとアルゴリズムを使用しています。 この例で作成された *TestData.txt* ファイルの暗号化を解除し、元のテキストをコンソールに表示します。

## <a name="asymmetric-decryption"></a>非対称復号化

通常は、パーティ (パーティ A) は、公開キーと秘密キーの両方を生成し、メモリ内、または暗号化キー コンテナーのいずれかに格納します。 パーティ A は公開キーを別のパーティ (パーティ B) に送信します。 パーティ B は、公開キーを使用してデータを暗号化し、データをパーティ A に送り返します。パーティ A は、データを受信した後、対応する秘密キーを使用して復号化します。 復号化は、パーティ B がデータの暗号化に使用した公開キーに対応する秘密キーをパーティ A が使用する場合にのみ成功します。

セキュリティで保護された暗号化キー コンテナーに非対称キーを格納する方法と、その後非対称キーを取得する方法については、「 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)」を参照してください。

次の例は、対称キーと IV を表す 2 つのバイト配列の復号化を示しています。 第三者に簡単に送信できる形式で <xref:System.Security.Cryptography.RSA> オブジェクトから非対称の公開キーを抽出する方法については、「 [Encrypting Data](encrypting-data.md)というマネージ ストリームの値に初期化します。

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a>関連項目

- [暗号化と復号化のためのキーの生成](generating-keys-for-encryption-and-decryption.md)
- [データの暗号化](encrypting-data.md)
- [Cryptographic Services](cryptographic-services.md)
- [暗号モデル](cryptography-model.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- [パディングを使用した CBC モードの対称復号化に関するタイミングの脆弱性](vulnerabilities-cbc-mode.md)
- [データ保護の ASP.NET Core](/aspnet/core/security/data-protection/introduction)
