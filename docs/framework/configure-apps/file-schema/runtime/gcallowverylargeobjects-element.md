---
description: '詳細情報: <gcAllowVeryLargeObjects> 要素'
title: gcAllowVeryLargeObjects 要素
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: ff8380a13c4284cc24178e185344207c3b9a39b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787020"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllowVeryLargeObjects> 要素

64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列を有効にします。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a>属性
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列が有効であるかどうかを指定します。|  
  
### <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|合計サイズが 2 GB を超える配列は有効ではありません。 既定値です。|  
|`true`|64 ビット プラットフォームで、合計サイズが 2 GB を超える配列が有効になっています。|  
  
## <a name="child-elements"></a>子要素  

なし。  
  
## <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>解説  

 アプリケーション構成ファイルで次の要素を使用すると 2 GB を超えるサイズの配列が有効になりますが、オブジェクトのサイズや配列のサイズに対するその他の制限は変更されません。  
  
- 配列の要素の最大数は <xref:System.UInt32.MaxValue?displayProperty=nameWithType> です。  
  
- 1つの次元の最大サイズは、バイト配列と1バイト構造の配列の場合は 2147483591 (0x7FFFFFC7)、他の型を含む配列の場合は 2146435071 (0X7FEFFFFF) です。  
  
- 文字列およびその他の非配列オブジェクトの最大サイズは変更されません。  
  
> [!CAUTION]
> この機能を有効にする前に、すべての配列のサイズが 2 GB よりも小さいことを前提としたアンセーフ コードがアプリケーションに含まれていないことを確認します。 たとえば、配列をバッファーとして使用するアンセーフコードは、配列が 2 GB を超えることを想定して記述されている場合、バッファーオーバーランの影響を受ける可能性があります。  
  
## <a name="example"></a>例  

 アプリケーションでこの機能を有効にする方法を次の例に示します。  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>サポート対象 :

.NET Framework 4.5 以降のバージョン

## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
