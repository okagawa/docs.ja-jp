---
description: '詳細については、次のページを参照してください: \n Datatの説明:: ReadVirtual メソッド'
title: ICorDebugDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
ms.openlocfilehash: 4525ba1e5dc685813d963dab96879b886987f38f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710609"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual メソッド

指定したアドレスを開始位置として連続したメモリのブロックを取得し、指定したバッファー内でそれを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a>パラメーター  

 `address`  
 から要求されたメモリの開始アドレス。  
  
 `pbuffer`  
 入出力メモリが格納されるバッファー。  
  
 `bytesRequested`  
 からターゲットアドレスから取得するバイト数。  
  
 `pBytesRead`  
 入出力ターゲットアドレスから実際に読み取られたバイト数。 これはよりも小さくなる可能性があり `bytesRequested` ます。  
  
## <a name="remarks"></a>解説  

 最初のバイト (指定した開始アドレス) を読み取ることができる場合、呼び出しは成功を返します (null で終わる文字列など、自己記述型の長さを持つデータ構造の効率的な読み取りをサポートするため)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget インターフェイス](icordebugdatatarget-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
