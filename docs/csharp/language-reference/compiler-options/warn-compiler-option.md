---
description: -warn (C# コンパイラ オプション)
title: -warn (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: d59274423e6f9844d3ab22f3ac513ba1a05d7f07
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171352"
---
# <a name="-warn-c-compiler-options"></a>-warn (C# コンパイラ オプション)

**-warn** オプションは、コンパイラが表示する警告レベルを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>引数  

 `option`  
 コンパイルで表示する警告レベル: 数値が小さいほど重要度が高い警告のみが表示され、数値が大きいほど多くの警告が表示されます。 この値は、ゼロまたは正の整数である必要があります。

|警告レベル|意味|
|-------------------|-------------|
|0|すべての警告メッセージの出力をオフにします。|
|1|重大な警告メッセージを表示します。|  
|2|レベル 1 の警告に加え、クラス メンバーの非表示に関する警告など、より重大度の低い特定の警告を表示します。|  
|3|レベル 2 の警告に加え、常に `true` または `false` に評価される式に関する警告など、より重大度の低い特定の警告を表示します。|  
|4 (既定)|レベルの 3 の警告に加え、情報のための警告を表示します。|
|5|レベル 4 の警告に加え、C# 9.0 に含まれているコンパイラの[追加の警告](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md)を表示します。|
|5 より大きい|5 より大きいすべての値は、5 として扱われます。 コンパイラが新しい警告レベルで更新された場合に、必ずすべての警告が使用されるように、一般に任意の大きな値 (`9999` など) を指定します。|
  
## <a name="remarks"></a>注釈  

 エラーまたは警告に関する情報を取得するには、ヘルプの索引でエラー コードを検索することができます。 エラーまたは警告に関する情報を取得する他の方法については、「[C# コンパイラ エラー](../compiler-messages/index.md)」を参照してください。  
  
 すべての警告をエラーとして扱う場合は [-warnaserror](./warnaserror-compiler-option.md) を使用します。 特定の警告を無効にするには、[-nowarn](./nowarn-compiler-option.md) を使用します。  
  
 **-w** は **-warn** の省略形です。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1. プロジェクトの **[プロパティ]** ページを開きます。  
  
2. **[ビルド]** プロパティ ページをクリックします。  
  
3. **警告レベル** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>」を参照してください。  
  
## <a name="example"></a>例  

 `in.cs` をコンパイルして、コンパイラにレベル 1 の警告のみを表示させます。  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](./index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
