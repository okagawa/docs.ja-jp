---
description: 詳細については、Silverlight 用の CreateDebuggingInterfaceFromVersion 関数に関するページを参照してください。
title: CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 8c61593f2e912260ecca65efce9f905ce56e88dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801450"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)

[Createversionstringfrommodule 関数](createversionstringfrommodule-function.md)から返される共通言語ランタイム (CLR) のバージョン文字列を受け取り、対応するデバッガーインターフェイス (通常は[ICorDebug](icordebug-interface.md)) を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szDebuggeeVersion`\
 から [Createversionstringfrommodule 関数](createversionstringfrommodule-function.md)によって返される、ターゲットデバッグ対象の CLR のバージョン文字列。  
  
 `ppCordb`\
 [out] COM オブジェクト (`IUnknown`) へのポインターのポインター。 このオブジェクトは、返される前に [ICorDebug](icordebug-interface.md) オブジェクトにキャストされます。  
  
## <a name="return-value"></a>戻り値

 `S_OK`\
 `ppCordb`[ICorDebug インターフェイス](icordebug-interface.md)インターフェイスを実装する有効なオブジェクトを参照します。  
  
 `E_INVALIDARG`\
 `szDebuggeeVersion` または `ppCordb` が null です。  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 CLR デバッグに必要なコンポーネントが見つかりません。 _mscordbi.dll_ または _mscordaccore.dll_ のいずれかがターゲット CoreCLR.dll と同じディレクトリに見つかりませんでした。  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 mscordbi.dll または mscordaccore.dll が対象の CoreCLR.dll と同じバージョンではありません。  
  
 `E_FAIL` (またはその他の `E_` リターンコード) \
 [ICorDebug インターフェイス](icordebug-interface.md)を返すことができません。  
  
## <a name="remarks"></a>解説

 返されるインターフェイスは、対象のプロセス内の CLR にアタッチして CLR が実行しているマネージド コードをデバッグする機能を提供します。  
  
## <a name="requirements"></a>要件

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** dbgshim. h  
  
 **ライブラリ:** dbgshim.dll  
  
 **.NET Framework のバージョン:** 3.5 SP1
