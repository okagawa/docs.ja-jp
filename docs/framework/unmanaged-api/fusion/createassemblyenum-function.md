---
description: CreateAssemblyEnum 関数の詳細について説明します。
title: CreateAssemblyEnum 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
ms.openlocfilehash: 47177fcf0cd9e1b492fa89b9fb80c5cdaaced689
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761142"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum 関数

指定された[IAssemblyName](iassemblyname-interface.md)を持つアセンブリ内のオブジェクトを列挙できる[iassemblyenum](iassemblyenum-interface.md)インスタンスへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>パラメーター  

 `pEnum`  
 入出力要求されたポインターを格納しているメモリ位置へのポインター `IAssemblyEnum` 。  
  
 `pUnkReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pUnkReserved` null 参照である必要があります。  
  
 `pName`  
 から `IAssemblyName` 要求されたアセンブリの。 この名前は、列挙をフィルター処理するために使用されます。 グローバルアセンブリキャッシュ内のすべてのアセンブリを列挙するには null を指定できます。  
  
 `dwFlags`  
 から列挙子の動作を変更するためのフラグ。 このパラメーターには、 [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) 列挙体とのビットが1つだけ含まれます。  
  
 `pvReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pvReserved` null 参照である必要があります。  
  
## <a name="remarks"></a>解説  

 パラメーターには `dwFlags` 、列挙体のビットが1つだけ含まれ `ASM_CACHE_FLAGS` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyEnum インターフェイス](iassemblyenum-interface.md)
- [IAssemblyName インターフェイス](iassemblyname-interface.md)
- [Fusion グローバル静的関数](fusion-global-static-functions.md)
