---
title: QualifierSet_EndEnumeration 関数 (アンマネージ API リファレンス)
description: QualifierSet_EndEnumeration 関数は、列挙体を終了します。
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2739003fc9c1f93d379e4a59338cbef7a1a0f135
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726744"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration 関数

[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)関数の呼び出しで開始された列挙体を終了します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr` から [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) インスタンスへのポインター。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>注釈

この関数は、 [IWbemQualifierSet:: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) メソッドの呼び出しをラップします。

この呼び出しは推奨されますが、必須ではありません。 列挙に関連付けられているリソースを直ちに解放します。

## <a name="requirements"></a>要件  

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
**ヘッダー:** WMINet_Utils .idl  
  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
