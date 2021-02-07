---
description: '詳細情報: WriteStartHeaders メソッド'
title: WriteStartHeaders メソッド (System.servicemodel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 20cadf5f1eecf6d8e02c5dc4597889abaef4ec36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699364"
---
# <a name="messagewritestartheaders-method"></a>WriteStartHeaders メソッド

メソッドを呼び出すことによって、開始ヘッダーを XML ファイルに書き込み <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> ます。

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>パラメーター

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  開始ヘッダーを XML ファイルに書き込むために使用するライター。

## <a name="remarks"></a>解説

> [!WARNING]
> `Message.WriteStartHeaders`メソッドは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.ServiceModel.Channels>

**アセンブリ:** System.ServiceModel.dll

**.NET Framework のバージョン:** 3.0 以降で使用できます。
