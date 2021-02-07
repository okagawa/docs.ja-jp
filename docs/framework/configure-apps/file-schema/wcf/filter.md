---
description: '詳細情報: <filter>'
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 993d2265ac3a714475e8cbe9e8a2c3f93c46bde2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664679"
---
# \<filter>

受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) の種類、 <xref:System.ServiceModel.Dispatcher.MessageFilter> およびフィルターに必要なサポートデータまたはパラメーターを決定するルーティングフィルターを定義します。

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

| 属性  | 説明 |
| ---------- | ----------- |
| customType | フィルターとして使用されるカスタム型の完全修飾型名を示す文字列。 `filterType`がに設定されている場合 `custom` 、この属性には作成するクラスの完全修飾型名が含まれます。  `filterData` には、カスタム型フィルターの評価時に使用される値を含めることもできます。 |
| filterData | フィルター データを示す文字列。 この属性を指定する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| filterType | フィルターの種類を示す文字列。 この属性は <xref:System.ServiceModel.Routing.Configuration.FilterType> 型です。  `filterData` 属性を使用する方法の詳細については、「<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>」を参照してください。 |
| name       | フィルター要素の一意の名前を示す文字列。 |

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

| 要素 | 説明 |
| ------- | ----------- |
| [\<routing>](routing.md) | 一連のルーティングフィルターを定義するための構成セクション <xref:System.ServiceModel.Dispatcher.MessageFilter> 。受信メッセージを評価するときに使用する Windows Communication Foundation (WCF) の種類を決定します。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
