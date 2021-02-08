---
description: '詳細情報: CreateCordbObject 関数'
title: CreateCordbObject 関数
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: b6a585fc89f780b22f842127e1923414dbb8230f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801476"
---
# <a name="createcordbobject-function"></a>CreateCordbObject 関数

リモートプロセスでマネージデバッグセッションをインスタンス化する機能を提供するデバッガーインターフェイス ([ICorDebug](icordebug-interface.md)) を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `iDebuggerVersion`  
 [in] ターゲット プロセスのデバッガー バージョン。 リモート デバッグの場合、このパラメーターは CorDebugVersion_2_0 である必要があります。  
  
 `ppCordb`  
 入出力 [ICorDebug](icordebug-interface.md) インターフェイスにキャストされて返されるオブジェクトへのポインターへのポインター。  
  
## <a name="return-value"></a>戻り値  

 S_OK  
 プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。  
  
 E_INVALIDARG  
 `ppCordb` が null であるか、または `iDebuggerVersion` が CorDebugVersion_2_0 ではありません。  
  
 E_OUTOFMEMORY  
 `ppCordb` 用に十分なメモリを割り当てることができません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 その他のエラーが発生しました。  
  
## <a name="remarks"></a>解説  

 で返される [ICorDebug](icordebug-interface.md) インターフェイスは、 `ppCordb` すべてのマネージデバッグサービスの最上位レベルのデバッグインターフェイスです。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Coreclrremoteデバッグインターフェイス .h  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET Framework のバージョン:** 3.5 SP1
