---
description: '詳細情報: s_isDebuggerCheckDisabledForTestPurposes フィールド'
title: s_isDebuggerCheckDisabledForTestPurposes フィールド
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: a71235c13a7a35872bcf5374be8077bafad5ff9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802659"
---
# <a name="s_isdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes フィールド

クラスのこのプライベートフィールド `System.Windows.Diagnostics.VisualDiagnostics` は、アクティブなデバッガーの内部チェックが実行されるかどうかを判断するために Visual Studio によって使用されます。

## <a name="syntax"></a>構文

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> クラスの Api `System.Windows.Diagnostics.VisualDiagnostics` は、アプリケーションがデバッガーで実行されている場合にのみ使用できます。 `s_isDebuggerCheckDisabledForTestPurposes` `true` デバッガーの外部で api にアクセスするには、をに設定します。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのフィールドの使用はサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Windows.Diagnostics>

**アセンブリ:** プレゼンテーションコア (PresentationCore.dll)

**.NET Framework のバージョン:** 4.6 以降で使用できます。
