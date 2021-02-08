---
description: '詳細情報: HttpStatusDescription クラス'
title: HttpStatusDescription クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa135a6421397ce6b7be2af05d66aa8e81beafb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802503"
---
# <a name="httpstatusdescription-class"></a>HttpStatusDescription クラス

標準の HTTP 状態の説明を提供します。 このクラスは継承できません。

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> このクラスは内部的なものであり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。

## <a name="get-method"></a>Get メソッド

指定された HTTP ステータスコードに関連付けられている説明を返します。

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a>パラメーター

`code` <xref:System.Int32>

HTTP 状態コード (など) `404` 。

### <a name="return-value"></a>戻り値

<xref:System.String?displayProperty=nameWithType>

HTTP 状態の説明。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)
