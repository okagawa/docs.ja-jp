---
description: 詳細については、「WF でのランタイムアクティビティ」を参照してください。
title: WF のランタイム アクティビティ
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 5ff164539b9efd7b2b8a4e7cffd5239eae6145fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792636"
---
# <a name="runtime-activities-in-wf"></a>WF のランタイム アクティビティ

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] には、永続化や終了などのワークフロー ランタイムの機能にアクセスするために、システムによって提供されるアクティビティがいくつか用意されています。  
  
|アクティビティ|説明|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|ワークフローがその状態を永続化するように明示的に要求します。|  
|<xref:System.Activities.Statements.TerminateWorkflow>|実行中のワークフロー インスタンスを終了します。|  
|<xref:System.Activities.Statements.NoPersistScope>|子アクティビティの永続化を防ぐコンテナー アクティビティ。|
