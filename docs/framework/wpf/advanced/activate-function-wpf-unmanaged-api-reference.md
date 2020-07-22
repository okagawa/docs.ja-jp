---
title: Activate 関数 - WPF アンマネージ API リファレンス
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734514"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate 関数 (WPF アンマネージ API リファレンス)

この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしますが、独自に作成したコードから直接使用するためのものではありません。

ウィンドウの管理のために Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。

## <a name="syntax"></a>構文

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>パラメーター

`pParameters`\
ウィンドウのアクティベーション パラメーターへのポインター。

`ppInner`\
<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> オブジェクトへのポインターを含む単一要素バッファーのアドレスへのポインター。

## <a name="requirements"></a>必要条件

**プラットフォーム:** 「[.NET Framework システム要件](../../get-started/system-requirements.md)」を参照してください。

**DLL:**

.NET Framework 3.0 および 3.5 の場合:PresentationHostDLL.dll

.NET Framework 4 以降の場合:PresentationHost_v0400.dll

**.NET Framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>関連項目

- [WPF のアンマネージ API リファレンス](wpf-unmanaged-api-reference.md)
