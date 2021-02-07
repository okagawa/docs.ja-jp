---
description: '詳細情報: TlsStream.m_Worker フィールド'
title: TlsStream.m_Worker フィールド (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.TlsStream.m_Worker
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: d929b0b1949bc1902425c016bfd770d4c66a3257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699520"
---
# <a name="tlsstreamm_worker-field"></a>TlsStream.m_Worker フィールド

SSL ストリームの状態を表します。

## <a name="syntax"></a>構文

```csharp
private SslState m_Worker;
```

## <a name="field-value"></a>フィールド値

`System.Net.Security.SslState`  
SSL ストリームの状態。

## <a name="remarks"></a>解説

> [!WARNING]
> `TlsStream.m_Worker`フィールドはプライベートであり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのフィールドの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
