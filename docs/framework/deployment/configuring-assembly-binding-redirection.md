---
title: アセンブリ バインディングのリダイレクトの構成
description: アプリケーション構成ファイルの assemblyBinding 要素にある appliesTo 属性を使用して、.NET でアセンブリ バインディング リダイレクトを構成する方法を説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 8f3e2270d92e11ea467d6cefc2b19b4faff563b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621731"
---
# <a name="configuring-assembly-binding-redirection"></a>アセンブリ バインディングのリダイレクトの構成
既定では、アプリケーションは、アプリケーションのコンパイルに使用したランタイム バージョンと共に出荷された .NET Framework アセンブリのセットを使用します。 アプリケーション構成ファイルの [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 要素にある **appliesTo** 属性を使用して、アセンブリ バインディング参照を特定のバージョンの .NET Framework アセンブリにリダイレクトすることができます。 このオプションの属性は、.NET Framework のバージョン番号を使用して、どのバージョンに適用するのかを示します。 **appliesTo** 属性が指定されていない場合、 **\<assemblyBinding>** 要素は、すべてのバージョンの .NET Framework に適用されます。  
  
 **appliesTo** 属性は .NET Framework Version 1.1 で導入されたものであり、.NET Framework Version 1.0 では無視されます。 つまり、**appliesTo** 属性が指定されている場合でも、.NET Framework バージョン1.0 を使用しているときは、すべての **\<assemblyBinding>** 要素が適用されます。  
  
> [!NOTE]
> **appliesTo** 属性は、アセンブリ バインディングのリダイレクトをランタイムの特定のバージョンに制限するために使用します。  
  
 たとえば、.NET Framework Version 1.0 アセンブリのアセンブリ バインディングをリダイレクトするには、アプリケーション構成ファイルに次の XML コードを追加します。  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<assemblyBinding>** 要素では順序が区別されます。 最初に .NET Framework Version 1.0 のアセンブリのアセンブリ バインディング リダイレクト情報を入力し、その次に .NET Framework Version 1.1 のアセンブリのアセンブリ バインディング リダイレクト情報を入力します。 最後に、 **appliesTo** 属性を使用せず、すべてのバージョンの .NET Framework に適用される .NET Framework アセンブリ リダイレクトのアセンブリ バインディング リダイレクト情報を入力します。 リダイレクトで矛盾が発生した場合は、構成ファイル内で最初に一致したリダイレクト ステートメントが使用されます。  
  
 たとえば、ある参照を .NET Framework Version 1.0 のアセンブリにリダイレクトし、別の参照を .NET Framework Version 1.1 のアセンブリにリダイレクトするには、次の擬似コードに示すパターンを使用します。  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">
  <!-- .NET Framework version 1.0 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">
  <!-- .NET Framework version 1.1 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="...">
  <!-- Redirects meant for all versions of the .NET Framework. -->
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a>構成ファイル エラーのデバッグ  
 ランタイムは、アプリケーション ドメインが作成されるときに構成ファイルを一度解析し、コードをアプリケーション ドメインに読み込みます。 共通言語ランタイムは、エントリを無視することによって構成ファイルに含まれるエラーを処理します。 構成ファイルに不正な XML が含まれる場合、ランタイムは構成ファイル全体を無視します。 無効な XML に対しては、無効なセクションだけを無視します。  
  
 アセンブリ バインディングのリダイレクトが発生しているかどうかを調べることによって、構成ファイルが使用されているかどうかを判断できます。 [アセンブリ バインディング ログ ビューアー (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) を使用して、読み込まれたアセンブリを調べます。 すべてのアセンブリ バインドを見るには、レジストリで **ForceLog** のエントリを設定する必要があります。  
  
## <a name="see-also"></a>関連項目

- [方法: 自動バインディング リダイレクトを有効/無効にする](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
