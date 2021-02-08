---
description: '詳細について: ICorDebugILFrame4:: GetCodeEx メソッド'
title: ICorDebugILFrame4::GetCodeEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: 1d17dfa531354b8a4b0dd3c0d3d2eb47206900cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791232"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx メソッド

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 このスタック フレームが実行中のコードに対するポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `flags`  
 からプロファイラーの ReJIT 要求によって定義された中間言語 (IL) がフレームに含まれるかどうかを指定する [Ilcodekind](ilcodekind-enumeration.md) 列挙体のメンバー。  
  
 `ppCode`  
 入出力このスタックフレームが実行しているコードを表す "テキストコード" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 このメソッドは、必要に応じて、プロファイラーの ReJIT 要求によって定義されたコードにアクセスする点を除いて、 [GetCode](icordebugframe-getcode-method.md) メソッドに似ています。 の値を指定してこのメソッドを呼び出す `flags` `ILCODE_ORIGINAL_IL` ことは、 [GetCode](icordebugframe-getcode-method.md)を呼び出すことと同じです。メソッドがインストルメント化されている場合、その IL にアクセスすることはできません。 `ILCODE_REJIT_IL` を使用するとデバッガーは、プロファイラーの ReJIT 要求で定義された IL にアクセスできます。 IL がインストルメント化されていない場合、 `ppCode` は **null** であり、メソッドはを返し `S_OK` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [ReJIT: How-To ガイド](/archive/blogs/davbr/rejit-a-how-to-guide)
