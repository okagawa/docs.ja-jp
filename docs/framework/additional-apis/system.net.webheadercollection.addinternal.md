---
description: 詳細については、「WebHeaderCollection. AddInternal メソッド」を参照してください。
title: WebHeaderCollection. AddInternal メソッド (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 7bc84f84e6656dba5230b627fe9decfc4e0b4746
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699481"
---
# <a name="webheadercollectionaddinternal-method"></a>WebHeaderCollection. AddInternal メソッド

指定された名前と値を持つ新しいヘッダーをコレクションに追加し、チェックをバイパスします。

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> このメソッドは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="parameters"></a>パラメーター

- `name` <xref:System.String>

  ヘッダーの名前。

- `value` <xref:System.String>

  ヘッダーの値です。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)
