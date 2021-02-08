---
description: 詳細については、「SqlStreamChars. Dispose (Boolean) メソッド」を参照してください。
title: SqlStreamChars. Dispose (Boolean) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ce24cc885d87a3ff0bbcdbea7992ca78ee592454
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802607"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars. Dispose (Boolean) メソッド

派生クラスでオーバーライドされると、ストリームによって使用されるリソースを解放します。 このメソッドを含むアセンブリには、SQLAccess.dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>パラメーター

`disposing`\
マネージド リソースとアンマネージド リソースの両方を解放する場合は `true`。アンマネージド リソースだけを解放する場合は `false`。

## <a name="remarks"></a>解説

> [!WARNING]
> `SqlStreamChars.Dispose`メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (System.Data.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
