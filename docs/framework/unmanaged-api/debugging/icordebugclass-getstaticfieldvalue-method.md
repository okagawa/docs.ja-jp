---
description: '詳細については、次を参照してください: のクラス:: GetStaticFieldValue メソッド'
title: ICorDebugClass::GetStaticFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: a5406e44491ce89030731c35752066e4943cebfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711522"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue メソッド

指定された静的フィールドの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `fieldDef`  
 から `Def` 取得するフィールドを参照するフィールドトークン。  
  
 `pFrame`  
 からスレッド、コンテキスト、またはアプリケーションドメインの静的を区別するために使用されるフレームを表す、テキストフレームオブジェクトへのポインター。  
  
 静的フィールドがスレッド、コンテキスト、またはアプリケーションドメインに対する相対パスである場合、フレームによって適切な値が決定されます。  
  
 `ppValue`  
 入出力静的フィールドの値を表す ICorDebugValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 パラメーター化された型の場合、静的フィールドの値は、特定のインスタンス化に対する相対値になります。 したがって、クラスコンストラクターが型のパラメーターを受け取る場合は、では <xref:System.Type> なく、の [型](icordebugtype-getstaticfieldvalue-method.md) を呼び出す必要があり `ICorDebugClass::GetStaticFieldValue` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
