---
title: QualifierSet_Delete 関数 (アンマネージ API リファレンス)
description: QualifierSet_Delete 関数は、修飾子を名前で削除します。
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721154"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete 関数

名前によって指定した修飾子が削除されます。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr` から [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) インスタンスへのポインター。

`wszName` から削除する修飾子の名前。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` パラメーターが正しくありません。 |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | この修飾子の削除は無効です。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定された修飾子が見つかりませんでした。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | ローカルオーバーライドが削除され、親オブジェクトからの元の修飾子がスコープを再開しました。 |

## <a name="remarks"></a>注釈

この関数は、 [IWbemQualifierSet::D e)](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) メソッドの呼び出しをラップします。

修飾子の伝達規則により、特定の修飾子が別のオブジェクトから継承され、現在のクラスまたはインスタンスで単にオーバーライドされている可能性があります。 この場合、メソッドは、 `QualifierSet_Delete` 修飾子を元の継承された値にリセットします。 この場合の関数は、ステータスコードを返し `WBEM_S_RESET_TO_DEFAULT` ます。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
