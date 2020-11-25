---
title: DeleteMethod 関数 (アンマネージ API リファレンス)
description: DeleteMethod 関数は、指定されたメソッドを CIM クラス定義から削除します。
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8ca58ed3510360b20577890055e4284869d1bf94
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708102"
---
# <a name="deletemethod-function"></a>DeleteMethod 関数

指定したメソッドを CIM クラス定義から削除します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`wszName`  
からクラステーブルから削除するメソッドの名前。 `wszName` は、有効なへのポインターである必要があり `LPCWSTR` ます。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドは存在しません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了させるための十分なメモリがありません。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |

## <a name="remarks"></a>注釈

この関数は、 [IWbemClassObject::D eletemethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) メソッドの呼び出しをラップします。

CIM インスタンスを指す [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ポインターでは、メソッドの削除はサポートされていません。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
