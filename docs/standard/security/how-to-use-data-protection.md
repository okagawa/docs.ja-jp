---
title: '方法: データ保護の使用'
description: .NET でデータ保護 API (DPAPI) にアクセスしてデータ保護を使用する方法について説明します。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: ed1b18e2c6456b53559e8fb7e989f148fefd35c7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820099"
---
# <a name="how-to-use-data-protection"></a>方法: データ保護の使用

> [!NOTE]
> この記事は、Windows に適用されます。
>
> ASP.NET Core の詳細については、「 [データ保護の ASP.NET Core](/aspnet/core/security/data-protection/introduction)」を参照してください。

.NET では、データ保護 API (DPAPI) にアクセスできます。これにより、現在のユーザーアカウントまたはコンピューターの情報を使用してデータを暗号化することができます。  DPAPI を使用すると、暗号化キーを明示的に生成および格納するという困難な問題を軽減できます。  
  
バイト配列のコピーを暗号化するには、<xref:System.Security.Cryptography.ProtectedData> クラスを使用します。 この機能は、.NET Framework、.NET Core、.NET 5 で使用できます。  現在のユーザー アカウントによって暗号化されたデータは、同じユーザー アカウントによってのみ復号化できることを指定できます。あるいは、現在のユーザー アカウントによって暗号化されたデータは、コンピューター上の任意のアカウントによって復号化できることを指定できます。  <xref:System.Security.Cryptography.ProtectedData> オプションの詳しい説明については、「<xref:System.Security.Cryptography.DataProtectionScope> 列挙型」を参照してください。  
  
## <a name="encrypt-data-to-a-file-or-stream-using-data-protection"></a>データ保護を使用してデータをファイルまたはストリームに暗号化する  
  
1. ランダム エントロピを作成します。  
  
2. 暗号化するバイト配列、エントロピ、およびデータ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedData.Protect%2A> メソッドを呼び出します。  
  
3. ファイルまたはストリームに暗号化されたデータを書き込みます。  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>データ保護を使用してファイルやストリームからデータを復号化するには  
  
1. ファイルまたはストリームから暗号化されたデータを読み取ります。  
  
2. 復号化するバイト配列およびデータ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> メソッドを呼び出します。  
  
## <a name="example"></a>例

次のコード例は、暗号化と復号化の 2 つの形式を示しています。  最初に、コード例では、メモリ内のバイト配列を暗号化してから復号化します。  次に、コード例では、バイト配列のコピーを暗号化し、ファイルに保存して、そのファイルからデータを読み込み、その後データを復号化しています。  例では、元のデータ、暗号化されたデータ、および復号化されたデータが表示されます。

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  

この例は、.NET Framework を対象とし、Windows で実行している場合にのみ、コンパイルして実行します。

- `System.Security.dll` への参照を含めます。  
  
- <xref:System>、<xref:System.IO>、<xref:System.Security.Cryptography>、および <xref:System.Text> 名前空間を含めます。  
  
## <a name="see-also"></a>関連項目

- [暗号モデル](cryptography-model.md)
- [Cryptographic Services](cryptographic-services.md)
- [クロスプラットフォーム暗号化](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [データ保護の ASP.NET Core](/aspnet/core/security/data-protection/introduction)
