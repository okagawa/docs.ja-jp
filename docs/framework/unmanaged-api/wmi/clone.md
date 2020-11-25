---
title: Clone 関数 (アンマネージ API リファレンス)
description: Clone 関数は、現在のオブジェクトの完全な複製である新しいオブジェクトを返します。
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: aecbf750b42626629dcb5aef369978a2e2bd002a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708115"
---
# <a name="clone-function"></a>Clone 関数

現在のオブジェクトの完全な複製である新しいオブジェクトが返されます。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`ppCopy`  
入出力完全な唯一のオブジェクトである新しいオブジェクト `ptr` 。 `null`現在のオブジェクトのコピーを受け取った場合、この引数をにすることはできません。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `null` がパラメーターとして指定されましたが、この使用法では有効ではありません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | オブジェクトを複製するのに十分なメモリがありません。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>注釈

この関数は、 [IWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) メソッドの呼び出しをラップします。

複製されたオブジェクトは、参照カウントが1の COM オブジェクトです。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
