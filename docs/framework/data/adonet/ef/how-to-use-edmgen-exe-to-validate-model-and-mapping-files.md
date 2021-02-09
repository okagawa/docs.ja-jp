---
description: '詳細情報: 方法:EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する'
title: '方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: e729ea36b7ff17dc318f4488a669b968161aea8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697349"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する

このトピックでは、[EDM ジェネレーター (EdmGen.exe)](edm-generator-edmgen-exe.md) ツールを使用してモデル ファイルとマッピング ファイルを検証する方法を示します。 詳細については、「[Entity Data Model](../entity-data-model.md)」を参照してください。  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>EdmGen.exe を使用して School モデルを検証するには  
  
1. School データベースを作成します。 詳細については、「[School サンプル データベースの作成](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))」を参照してください。  
  
2. School モデルを生成します。 詳細については、[EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。  
  
3. コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>関連項目

- [方法: Entity Framework プロジェクトを手動で構成する](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET Entity Data Model ツール](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [方法: ビューを事前に生成してクエリ パフォーマンスを向上させる](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
