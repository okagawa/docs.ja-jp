---
title: 実行可能インスタンス検出期間
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: aefde2726bb2ccc15f9e68009e5e141602b13b10
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245771"
---
# <a name="runnable-instances-detection-period"></a>実行可能インスタンス検出期間

SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なインスタンスを永続性データベースで検出します。 SQL Workflow Instance Store の "実行可能 **インスタンス検出期間** " プロパティは、前の検出サイクルの後に、Sql Workflow instance store が永続性データベースで実行可能またはアクティブ化可能なワークフローインスタンスを検出する検出タスクを実行するまでの期間を指定します。  
  
 このプロパティの間隔を短く設定すると、ワークフロー インスタンスに関連付けられたタイマーの期限切れと、イベントのシグナリングおよび後続のインスタンスの読み込みの間の時間が短くなります。 ただし、ホストにかかる処理の負荷も増えるため、永続的なタイマーやホスト エラーがまれなシナリオでは望ましくない場合があります。 プロパティの型は TimeSpan で、プロパティの値は hh:mm:ss の形式です。 このプロパティの最小値は 00:00:01 です。 プロパティの既定値は 00:00:05 です。  
  
 実行可能およびアクティブ化可能なワークフローインスタンスの検出とアクティブ化の詳細については、「 [インスタンスのアクティブ化](instance-activation.md)」を参照してください。
