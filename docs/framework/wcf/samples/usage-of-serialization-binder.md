---
description: 詳細については、「シリアル化バインダーの使用」を参照してください。
title: シリアル化バインダーの使用
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: ee00d8049ae644525f8013801dc7c453b9ad5aeb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798174"
---
# <a name="usage-of-serialization-binder"></a>シリアル化バインダーの使用

このサンプルでは、<xref:System.Runtime.Serialization.SerializationBinder> を使用して、ジェネリック型のバージョンをシリアル化する際に変更する方法を示します。  
  
## <a name="demonstrates"></a>対象  

 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>ディスカッション  

 このサンプルでは、異なるバージョンの .NET Framework を対象とする2つのエンティティが、バイナリフォーマッタとシリアル化バインダーを使用して通信できるようにする方法を示します。  
  
このサンプルは、.NET リモート処理を使用して開発されました。 これは、.NET Framework 4 を対象とするサーバーで構成されます。このサーバーは、ジェネリック型のコントラクトと2つの異なるクライアント (1 つは 2.0 .NET Framework、もう1つは .NET Framework 4) を実装します。  
  
 このサーバーは、シリアル化の際に型のバージョンを相応に変更できるようにするために、<xref:System.Runtime.Serialization.SerializationBinder> をバイナリ フォーマッタにアタッチします。これにより、両方のクライアントで、これらの型を適切に逆シリアル化できるようになります。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルを設定、ビルド、および実行するには  
  
1. クライアントを実行するには、ソリューション SBGenericsVTS を右クリックし、[ **プロパティ**] を選択します。  
  
2. [ **共通プロパティ**] で、[ **スタートアッププロジェクト**] を選択し、[ **マルチスタートアッププロジェクト**] を選択します。  
  
3. [ **サーバー** ]、[ **Client20** ]、[ **Client40**] の順に選択します。 これら3つのプロジェクトに対して [ **開始** ] アクションを選択し、残りの設定を [ **なし**] のままにします。  
  
4. [ **OK]** をクリックし、F5 キーを押してサンプルを実行します。
