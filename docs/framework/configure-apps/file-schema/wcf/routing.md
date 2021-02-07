---
description: '詳細情報: <routing>'
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 62222b527a14310b66015d4fdc4503e6cff25c8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683347"
---
# \<routing>

一連のルーティングフィルターを定義するための構成セクションを表します。これにより、受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) の種類、 <xref:System.ServiceModel.Dispatcher.MessageFilter> およびフィルターが一致したときにメッセージを送信するターゲットエンドポイントを定義するルーティングテーブルが決定されます。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし

### <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | 受信メッセージを評価するときに使用される Windows Communication Foundation (WCF) MessageFilter の種類を決定するルーティングフィルターのセットを格納します。 |
| [**\<filterTables>**](filtertables.md) | ルーティング フィルターとターゲット エンドポイントとのマッピングを格納します。フィルターが一致したときにエンドポイントを指定するために使用されます。 |

### <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| **\<system.ServiceModel>** | すべての WCF 構成要素のルート要素です。 |

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
