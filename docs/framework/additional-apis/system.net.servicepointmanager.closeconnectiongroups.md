---
description: '詳細については、次を参照してください: ServicePointManager. CloseConnectionGroups メソッド'
title: ServicePointManager. CloseConnectionGroups メソッド (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 8cd1a1f0f4dbdaeaee117e6a7ae4219680363a6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699559"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a>ServicePointManager. CloseConnectionGroups メソッド

すべてのサービスポイントを反復処理し、指定された名前の接続グループを閉じます。

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> このメソッドは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="parameters"></a>パラメーター

`connectionGroupName` <xref:System.String>

閉じる接続グループの名前。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)
