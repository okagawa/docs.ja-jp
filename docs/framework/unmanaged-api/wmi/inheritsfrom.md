---
title: InheritsFrom 関数 (アンマネージ API リファレンス)
description: InheritsFrom 関数は、クラスまたはインスタンスが特定の親クラスから派生しているかどうかを判断します。
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3cfe3388dc808335e6d3daaf7ec949108e95f52e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726794"
---
# <a name="inheritsfrom-function"></a>InheritsFrom 関数

指定した親クラスから現在のクラスまたはインスタンスが派生しているかどうかが判定されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`wszAncestor`  
からクラスの名前。 `wszAncestor` は有効なを指している必要があり `LPCWSTR` ます。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | 現在のオブジェクトはを継承 `wszAncestor` します。  |
| `WBEM_S_FALSE` | 1 | 現在のオブジェクトはを継承しません `wszAncestor` 。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` が `null`です。 |
  
## <a name="remarks"></a>注釈

この関数は、 [IWbemClassObject:: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) メソッドの呼び出しをラップします。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
