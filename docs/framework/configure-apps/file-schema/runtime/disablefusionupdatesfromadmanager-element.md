---
title: <disableFusionUpdatesFromADManager> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117446"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> 要素
アプリケーション ドメインの構成設定をランタイム ホストがオーバーライドする既定の動作を無効化するかどうかを指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> Fusion 設定をオーバーライドする既定の機能が無効になっているかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|0|Fusion の設定をオーバーライドする機能を無効にしないでください。 これは、.NET Framework 4 から始まる既定の動作です。|  
|1|Fusion の設定をオーバーライドする機能を無効にします。 これにより、.NET Framework の以前のバージョンの動作に戻ります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|Description|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 .NET Framework 4 以降の既定の動作では、 <xref:System.AppDomainManager> <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> のサブクラスで、メソッドの実装に渡されるオブジェクトのプロパティまたはメソッドを使用して、オブジェクトが構成設定をオーバーライドできるようにし <xref:System.AppDomainManager> ます。 既定のアプリケーションドメインでは、変更した設定によって、アプリケーション構成ファイルで指定された設定が上書きされます。 他のアプリケーションドメインで <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> は、メソッドまたはメソッドに渡された構成設定がオーバーライドされ <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> ます。  
  
 新しい構成情報を渡すか、null ( `Nothing` Visual Basic) を渡して、渡された構成情報を削除することができます。  
  
 プロパティとメソッドの両方に構成情報を渡さないでください <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 。 構成情報を両方に渡すと、プロパティに渡す情報 <xref:System.AppDomainSetup.ConfigurationFile%2A> は無視されます。これは、メソッドによって <xref:System.AppDomainSetup.SetConfigurationBytes%2A> アプリケーション構成ファイルの構成情報がオーバーライドされるためです。 プロパティを使用する場合 <xref:System.AppDomainSetup.ConfigurationFile%2A> は、メソッドに null ( `Nothing` Visual Basic) を渡して、メソッド <xref:System.AppDomainSetup.SetConfigurationBytes%2A> またはメソッドの呼び出しで指定された構成バイトを削除でき <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> ます。  
  
 構成情報に加えて、、、、、、、、、、、、、 <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> および <xref:System.AppDomainSetup.ShadowCopyFiles%2A> の各メソッドの実装に渡されるオブジェクトの次の設定を変更できます。  
  
 要素を使用する代わりに `<disableFusionUpdatesFromADManager>` 、レジストリ設定を作成するか、環境変数を設定することによって、既定の動作を無効にすることができます。 レジストリで、またはの下にという名前の DWORD 値を作成 `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` し、値を `HKLM\Software\Microsoft\.NETFramework` 1 に設定します。 コマンドラインで、環境変数を `COMPLUS_disableFusionUpdatesFromADManager` 1 に設定します。  
  
## <a name="example"></a>例  
 要素を使用して Fusion 設定をオーバーライドする機能を無効にする方法を次の例に示し `<disableFusionUpdatesFromADManager>` ます。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [ランタイムがアセンブリを検索する方法](../../../deployment/how-the-runtime-locates-assemblies.md)
