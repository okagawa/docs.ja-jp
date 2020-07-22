---
title: 暗号スキームの作成
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288421"
---
# <a name="creating-a-cryptographic-scheme"></a>暗号スキームの作成
.NET Framework の暗号化コンポーネントを組み合わせて、データの暗号化と復号化を行うさまざまなスキームを作成することができます。  
  
 データの暗号化と復号化の単純な暗号スキームでは、次の手順を指定することがあります。  
  
1. 暗号化側と復号化側は、公開キーと秘密キーのペアを生成する。  
  
2. 暗号化側と復号化側は、公開キーを交換する。  
  
3. 暗号化側と復号化側は、たとえば TripleDES 暗号化の秘密キーを生成する。続いて、相手側の公開キーを使用して新規作成されたキーを暗号化する。  
  
4. 暗号化側と復号化側は、相手側にデータを送信し、特定の順序で相手側の秘密キーを自分の秘密キーと組み合わせて、新しい秘密キーを作成する。  
  
5. 暗号化側と復号化側は、対称暗号化を使って会話を開始する。  
  
 暗号スキームの作成は簡単なタスクではありません。
  
## <a name="see-also"></a>関連項目

- [暗号化サービス](cryptographic-services.md)
