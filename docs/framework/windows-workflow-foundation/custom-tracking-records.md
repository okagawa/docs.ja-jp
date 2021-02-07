---
description: 詳細については、「カスタム追跡レコード」を参照してください。
title: カスタム追跡レコード
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 9d6988465fa3afca4302c86e0c2cad2778f2beae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742694"
---
# <a name="custom-tracking-records"></a>カスタム追跡レコード

このトピックではカスタム追跡レコードを作成し、出力されたデータをレコードと一緒に読み込む方法を示します。

## <a name="emitting-custom-tracking-records"></a>カスタム追跡レコードの出力

次の例に示すように、カスタム追跡レコードはコード アクティビティから出力できます。

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<xref:System.Activities.Tracking.CustomTrackingRecord> 上で <xref:System.Activities.NativeActivityContext.Track%2A> メソッドを呼び出すことで、`ActivityContext` をコード アクティビティに出力できます。

## <a name="see-also"></a>関連項目

- [Windows Server App Fabric の監視](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric を使用したアプリケーションの監視](/previous-versions/appfabric/ee677276(v=azure.10))
