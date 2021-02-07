---
description: 詳細については、「Sslstate プロパティ」を参照してください。
title: SslState. Sslstate プロパティ (システム .Net. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: b0b9bebf23fcd8d643d06f1cff10c260c77a7c08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699624"
---
# <a name="sslstatesslprotocol-property"></a>SslState. Sslstate プロパティ

SSL プロトコルのバージョンを取得します。

## <a name="syntax"></a>構文

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>プロパティ値

<xref:System.Security.Authentication.SslProtocols>  
SSL プロトコルのバージョンを指定する列挙値のビットごとの組み合わせ。

## <a name="remarks"></a>解説

> [!WARNING]
> `SslState.SslProtocol`プロパティは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net.Security>

**アセンブリ:** システム (System.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
