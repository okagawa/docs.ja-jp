---
title: <source> 要素
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153296"
---
# <a name="source-element"></a>\<source> 要素
トレース メッセージを開始するトレース ソースを指定します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a>構文  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|省略可能な属性です。<br /><br /> トレースソースの名前を指定します。|  
|`switchName`|省略可能な属性です。<br /><br /> アプリケーションのトレーススイッチインスタンスの名前を指定します。 スイッチが要素で識別されない場合は、 `<switches>` スイッチのレベルを値で指定します。|  
|`switchType`|省略可能な属性です。<br /><br /> トレーススイッチの種類を指定します。 存在する場合、型は有効なクラス名である必要があり、空の文字列にすることはできません。|  
|`extraAttribute`|省略可能な属性です。<br /><br /> トレースソースに対してメソッドによって識別される、トレースソース固有の属性の値を指定し <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> ます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|Description|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|メッセージを収集、格納、およびルーティングするリスナーを格納します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|Description|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
  
## <a name="remarks"></a>解説  
 この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例では、要素を使用してトレースソースを追加し、と `<source>` `mySource` いう名前のソーススイッチのレベルを設定する方法を示し `sourceSwitch` ます。 トレース情報をコンソールに書き込むコンソールトレースリスナーが追加されます。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース スイッチ](../../../debug-trace-profile/trace-switches.md)
