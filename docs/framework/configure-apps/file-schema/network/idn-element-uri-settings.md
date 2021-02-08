---
description: '詳細情報: <idn> 要素 (Uri 設定)'
title: <idn> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: a53afd59b713a804d5b969521f468000dbbad6e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802477"
---
# <a name="idn-element-uri-settings"></a>\<idn> 要素 (Uri 設定)

国際化ドメイン名 (IDN) の解析がドメイン名に適用されるかどうかを指定します。
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a>構文  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

|**要素**|**説明**|  
|-----------------|---------------------|  
|`enabled`|国際化ドメイン名 (IDN) の解析がドメイン名に適用されるかどうかを指定します。既定値は none です。|  

### <a name="child-elements"></a>子要素

なし
  
### <a name="parent-elements"></a>親要素

|**要素**|**説明**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|.NET Framework が、uniform resource identifier (Uri) を使用して表された web アドレスを処理する方法を指定する設定が含まれます。|  

## <a name="remarks"></a>解説

既存の <xref:System.Uri> クラスは .NET Framework 3.5 で拡張されています。 3.0 SP1 および 2.0 SP1 (国際リソース識別子 (IRI) と国際化ドメイン名 (IDN) をサポート)。 現在のユーザーには、IRI と IDN のサポートを明示的に有効にしない限り、.NET Framework 2.0 の動作からの変更は表示されません。 これにより、.NET Framework の以前のバージョンとのアプリケーションの互換性を保証します。

IRI のサポートを有効にするには、次の2つの変更が必要です。

1. 次の行を、.NET Framework 2.0 ディレクトリの下の machine.config ファイルに追加します。
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. 国際化ドメイン名 (IDN) の解析をドメイン名に適用するかどうか、および IRI 解析規則を適用するかどうかを指定します。 これは、machine.config ファイルまたは app.config ファイルで指定できます。

 IDN には、使用する DNS サーバーに応じて、次の3つの値を指定できます。

- idn enabled = すべて  

     この値は、Unicode のドメイン名があれば、それを等価の Punycode (IDN 名) に変換します。

- idn enabled = AllExceptIntranet

     この値を指定すると、ローカルイントラネット上にないすべての Unicode ドメイン名が、Punycode に相当する (IDN 名) を使用するように変換されます。 この場合は、イントラネットで使用される DNS サーバーが Unicode 名前解決をサポートする必要があります。

- idn enabled = なし

     この値は、どの Unicode のドメイン名も、Punycode を使用するように変換しません。 これは、.NET Framework 2.0 の動作と一貫した既定値です。

 IDN を有効にすると、ドメイン名に含まれるすべての Unicode のラベルが Punycode のラベルに変換されます。 Punycode 名には ASCII 文字のみが含まれ、常に xn-- プレフィックスで始まります。 この理由は、ほとんどの DNS サーバーは ASCII 文字しかサポートしていないため、インターネットで既存の DNS サーバーをサポートするためです (RFC 3940 を参照)。

### <a name="configuration-files"></a>構成ファイル

この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。

## <a name="example"></a>例

次の例は、 <xref:System.Uri> IRI 解析と IDN 名をサポートするためにクラスによって使用される構成を示しています。

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a>関連項目

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)
