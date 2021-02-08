---
description: '詳細について: ICorProfilerInfo9:: GetCodeInfo4 メソッド'
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 765f3dfee6c56148eb7807b0606e79d4b3a2e7a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783808"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9:: GetCodeInfo4 メソッド

ネイティブコードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。

## <a name="syntax"></a>構文

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>パラメーター

- `pNativeCodeStartAddress`

  \[) ネイティブ関数の先頭へのポインター。

- `cCodeInfos`

  \[in] 配列のサイズ `codeInfos` 。

- `pcCodeInfos`

  \[out] 使用可能な [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体の総数へのポインター。

- `codeInfos`

  \[out] 呼び出し元が指定したバッファー。 メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。

## <a name="remarks"></a>解説

メソッドは、 `GetCodeInfo4` メソッドのさまざまなネイティブバージョンのコード情報を検索できる点を除いて、 [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)に似ています。

> [!NOTE]
> `GetCodeInfo4` ガベージコレクションをトリガーできます。

エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。

が返された後 `GetCodeInfo4` 、バッファーが `codeInfos` すべての [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造を格納するのに十分な大きさであったことを確認する必要があります。 これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。 `cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)構造体のサイズで除算されたがより小さい場合は `pcCodeInfos` 、大きいバッファーを割り当て、を `codeInfos` `cCodeInfos` 新しい大きいサイズに更新して、を `GetCodeInfo4` 再度呼び出します。

別の方法として、最初に `GetCodeInfo4` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。 次に、 `codeInfos` バッファーサイズをで返された値に設定し、 `pcCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズを乗算して、を `GetCodeInfo4` 再度呼び出します。

## <a name="requirements"></a>要件

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 インターフェイス](ICorProfilerInfo9-interface.md)
