---
title: NextMethod 関数 (アンマネージ API リファレンス)
description: NextMethod 関数は、列挙体の次のメソッドを取得します。
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726770"
---
# <a name="nextmethod-function"></a>NextMethod 関数

[BeginMethodEnumeration](beginmethodenumeration.md)の呼び出しで始まる列挙体の次のメソッドを取得します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
からこのパラメーターは使用されていません。

`ptr`  
から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lFlags`  
[in] 予約されています。 このパラメーターには0を指定する必要があります。

`pName`  
入出力 `null` 呼び出しの前を指すポインター。 関数から制御が戻るときに、メソッド名を含む新しいのアドレスを返し `BSTR` ます。

`ppSignatureIn`  
入出力メソッドのパラメーターを格納している [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) へのポインターを受け取るポインター `in` 。

`ppSignatureOut`  
入出力メソッドのパラメーターを格納している [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) へのポインターを受け取るポインター `out` 。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | 関数の呼び出しがありませんでした [`BeginEnumeration`](beginenumeration.md) 。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙体にはそれ以上のプロパティがありません。 |
  
## <a name="remarks"></a>注釈

この関数は、 [IWbemClassObject:: nextmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) メソッドの呼び出しをラップします。

呼び出し元は、 [BeginMethodEnumeration](beginmethodenumeration.md) 関数を呼び出すことによって列挙シーケンスを開始し、関数が戻るまで [nextmethod] 関数を呼び出し `WBEM_S_NO_MORE_DATA` ます。 必要に応じて、呼び出し元は [EndMethodEnumeration](endmethodenumeration.md)を呼び出すことによってシーケンスを終了します。 呼び出し元は、いつでも [EndMethodEnumeration](endmethodenumeration.md) を呼び出すことによって、列挙を早期に終了する場合があります。

## <a name="example"></a>例

C++ の例については、 [IWbemClassObject:: nextmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) メソッドを参照してください。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils .idl  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
