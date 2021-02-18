---
description: '詳細情報: -nologo (Visual Basic)'
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 370889fbd5d4e499ba27ff8bee4adc16a7a71876
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434889"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)

コンパイル中に著作権情報のバナーおよび情報メッセージが表示されません。  
  
## <a name="syntax"></a>構文  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Remarks  

 `-nologo` を指定すると、コンパイラで著作権情報のバナーが表示されません。 既定では、`-nologo` は無効です。  
  
> [!NOTE]
> `-nologo` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。  
  
## <a name="example"></a>例  

 次のコードでは `T2.vb` がコンパイルされ、著作権のバナーは表示されません。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
