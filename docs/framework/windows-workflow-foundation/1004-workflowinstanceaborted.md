---
description: '詳細情報: 1004-WorkflowInstanceAborted'
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: 4aaa0899da9b0b8510684a13537a8cb8f9117ee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755619"
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted

## <a name="properties"></a>プロパティ

|||
|-|-|
|id|1004|
|Keywords|WFRuntime|
|Level|Information|
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|

## <a name="description"></a>説明

ワークフローインスタンスが例外で中止されたことを示します。

## <a name="message"></a>Message

WorkflowInstance ID: '%1' は例外により中止されました。

## <a name="details"></a>詳細

|データ項目名|データ項目の型|説明|
|--------------------|--------------------|-----------------|
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|
|例外|`xs:string`|例外の詳細|
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
