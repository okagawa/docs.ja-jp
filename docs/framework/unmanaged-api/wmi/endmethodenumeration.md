---
title: EndMethodEnumeration 関数 (アンマネージ API リファレンス)
description: EndMethodEnumeration 関数は、メソッドの列挙体シーケンスを終了します。
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 82f50530967699427d8a00b1c9f518b639273626
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708063"
---
# <a name="endmethodenumeration-function"></a>EndMethodEnumeration 関数

[BeginMethodEnumeration 関数](beginmethodenumeration.md)の呼び出しで開始された列挙シーケンスを終了します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101d | An internal error occurred. |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
  
## <a name="remarks"></a>注釈

この関数は、 [IWbemClassObject:: EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) メソッドの呼び出しをラップします。

呼び出し元は、 [BeginMethodEnumeration 関数](beginmethodenumeration.md)を使用して列挙シーケンスを開始し、メソッドがを返すまで [nextmethod 関数](nextmethod.md )を呼び出し `WBEM_S_NO_MORE_DATA` ます。 呼び出し元は、を呼び出すことによって、シーケンスを終了する必要が `EndMethodEnumeration` あります。 呼び出し元は、いつでもを呼び出すことによって、列挙を早期に終了する場合があり `EndMethodEnumeration` ます。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
