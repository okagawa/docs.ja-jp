---
description: 詳細については <add> 、 <entries>
title: <add> の <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 0be24fb9d2327d411368dd05afc21156dfaf3d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803972"
---
# <a name="add-of-entries"></a>\<add> の \<entries>

以前に定義されたクライアント エンドポイントにフィルターをマップするルーティング エントリを表します。 このフィルターに一致するメッセージは、この宛先に送信されます。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|backupList|エンドポイントのバックアップ リストへの参照を指定する文字列。|  
|endpoint|`filterName` 属性で指定されたフィルターに一致するメッセージを受信するクライアント エンドポイントへの参照を指定する文字列。|  
|filterName|フィルター要素への参照を指定する文字列。|  
|priority|このエントリの優先順位を指定する整数。<br /><br /> ルーティング テーブルのエントリは、優先順位に基づいて評価されます。0 が最下位の優先順位です。 特定の優先順位について、すべてのエントリが同時に評価されます。現在の優先順位について一致するエントリが見つからない場合は、次の優先順位が評価されます。<br /><br /> この値は省略可能です。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<routing>](routing.md)|ルーティング マッピング エントリを含む構成セクション。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
