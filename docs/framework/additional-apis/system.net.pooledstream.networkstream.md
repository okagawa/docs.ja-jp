---
description: 詳細については、次を参照してください。 PooledStream. NetworkStream プロパティ
title: PooledStream. NetworkStream プロパティ (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 8a4f1d6bd9297028e763ef73bf96f85cbbfdafd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699637"
---
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream プロパティ

ソケットのネットワークストリームを取得または設定し `PooledStream` ます。

## <a name="syntax"></a>構文

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>プロパティ値

<xref:System.Net.Sockets.NetworkStream>  
ソケットのネットワークストリーム `PooledStream` 。

## <a name="remarks"></a>解説

> [!WARNING]
> `PooledStream.NetworkStream`プロパティは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
