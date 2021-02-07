---
description: ワークフローの詳細情報 <behaviors>
title: <behaviors> ワークフローの
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 5154a389aded34065cc7bdb11d1c73d71ca9f9f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698194"
---
# <a name="behaviors-of-workflow"></a>\<behaviors> ワークフローの

この要素には、 **Servicebehaviors** コレクションが含まれます。  コレクション内の各要素は、ワークフロー サービスによって使用されるそれぞれの動作要素を定義します。 各動作要素は、一意の **name** 属性によって識別されます。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|この構成セクションは、特定のワークフロー サービスに対して定義されたすべての動作を表します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|すべてのワークフロー構成要素のルート要素。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [動作を使用したランタイムの構成と拡張](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
