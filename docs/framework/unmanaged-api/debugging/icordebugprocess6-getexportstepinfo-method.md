---
description: '詳細について: ICorDebugProcess6:: GetExportStepInfo メソッド'
title: ICorDebugProcess6::GetExportStepInfo メソッド
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: e14b5e66d90fb2ece91991b3634fc2ad86fac895
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722010"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo メソッド

マネージド コードのステップ実行に役立つランタイム エクスポート関数の情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>パラメーター  

 pszExportName  
 [入力] PE エクスポート テーブルに書き込まれるランタイム エクスポート関数の名前。  
  
 invokeKind  
 入出力エクスポートされた関数がマネージコードを呼び出す方法を記述する [Cordebugcodeinvokekind](cordebugcodeinvokekind-enumeration.md) 列挙体のメンバーへのポインター。  
  
 invokePurpose  
 入出力エクスポートされた関数がマネージコードを呼び出す理由を示す [Cordebugcodeinvokepurpose](cordebugcodeinvokepurpose-enumeration.md) の列挙体のメンバーへのポインター。  
  
## <a name="return-value"></a>戻り値  

 メソッドは、次の表に記載されている値を返す場合があります。  
  
|戻り値|説明|  
|------------------|-----------------|  
|`S_OK`|メソッド呼び出しに成功しました。|  
|`E_POINTER`|`pInvokeKind` または `pInvokePurpose` が **null** です。|  
|その他の失敗した `HRESULT` 値。|必要に応じて。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
