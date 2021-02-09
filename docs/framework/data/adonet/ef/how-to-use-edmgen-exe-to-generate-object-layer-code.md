---
description: '詳細情報: 方法:EdmGen.exe を使用してオブジェクトレイヤー コードを生成する'
title: '方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1c1f614247f10c8819709b9494fb1ec04271b634
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697466"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する

このトピックでは、[EDM ジェネレーター (EdmGen.exe)](edm-generator-edmgen-exe.md) ツールを使用して、.csdl ファイルに基づくオブジェクトレイヤー コードを生成する方法について説明します。  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe を使用して Visual Basic プロジェクト用の School モデルのオブジェクトレイヤー コードを生成するには  
  
1. School データベースを作成します。 詳細については、「[School サンプル データベースの作成](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))」を参照してください。  
  
2. School モデルを生成するか、School.csdl ファイルを取得します。 詳細については、[EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。  
  
3. コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen.exe を使用して C# プロジェクト用の School モデルのオブジェクトレイヤー コードを生成するには  
  
1. School データベースを作成します。 詳細については、「[School サンプル データベースの作成](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))」を参照してください。  
  
2. School モデルを生成するか、School.csdl ファイルを取得します。 詳細については、[EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。  
  
3. コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>関連項目

- [モデリングとマッピング](modeling-and-mapping.md)
- [方法: Entity Framework プロジェクトを手動で構成する](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET Entity Data Model ツール](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [方法: ビューを事前に生成してクエリ パフォーマンスを向上させる](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
