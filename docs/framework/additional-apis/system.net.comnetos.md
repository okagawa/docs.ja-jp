---
description: '詳細情報: ComNetOS クラス'
title: ComNetOS クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 7376fe4a5e02818907cb71573451fffb3a3667cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802529"
---
# <a name="comnetos-class"></a>ComNetOS クラス

バージョンやインストールの種類 (クライアントまたはサーバー) など、現在のオペレーティングシステムに関する情報を提供します。 このクラスは継承できません。
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> このクラスは内部的なものであり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。

## <a name="iswin7orlater-field"></a>IsWin7orLater フィールド

オペレーティングシステムのバージョンが Windows 7 以降であるかどうかを指定します。

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)
