---
description: '詳細について: ICorDebugILFrame2:: EnumerateTypeParameters メソッド'
title: ICorDebugILFrame2::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 34f305b7793e4909318ae2301d72e2af7c12f2c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791292"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters メソッド

このフレームのパラメーターを格納している、テキスト型の型の列挙体オブジェクトを取得し <xref:System.Type> ます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppTyParEnum`  
 型パラメーターの列挙を可能にする、テキスト型のインターフェイスオブジェクトのアドレスへのポインター。  
  
 型パラメーターの一覧には、クラス型パラメーター (存在する場合) と、その後にメソッド型パラメーター (存在する場合) が含まれます。  
  
## <a name="remarks"></a>解説  

 [IMetaDataImport2:: EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md)メソッドを使用して、このリストに含まれるクラス型パラメーターとメソッド型パラメーターの数を確認します。  
  
 型パラメーターは常に使用できるとは限りません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
