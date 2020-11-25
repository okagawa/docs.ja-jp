---
title: ICLRRuntimeInfo::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
ms.openlocfilehash: 34f996f4efe9c0db4c3f0f5277e30f53e91ec47f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696792"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString メソッド

指定した [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスに関連付けられている共通言語ランタイム (CLR) のバージョン情報を取得します。  
  
 このメソッドは、次の関数を置き換えます。  
  
- [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md)  
  
- [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pwzBuffer`  
 入出力.NET Framework のコンパイルバージョンを "v *A*" という形式で指定します。*B*[.*X*] " *A*、 *B*、および *X* は、メジャーバージョン、マイナーバージョン、およびビルド番号に対応する10進数です。 *X* は省略可能です。 *X* が存在しない場合、末尾のピリオドはありません。  
  
> [!NOTE]
> このパラメーターは、C:\Windows\Microsoft.NET\Framework. の下に表示される .NET Framework バージョンのディレクトリ名と一致する必要があります。  
  
 値の例としては、"v v1.0.3705"、"v 1.1.4322"、"v v2.0.50727"、および "v4.0" があります。*x*"。ここで *x* は、インストールされているビルド番号に依存します。 "V" プレフィックスが必須であることに注意してください。  
  
 `pchBuffer`  
 [入力、出力] `pwzBuffer` バッファーオーバーランを回避するためののサイズを指定します。 `pwzBuffer`がの場合、は、割り当てを `null` `pchBuffer` 許可するために必要なサイズを返し `pwzBuffer` ます。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pwzBuffer` または `pchBuffer` が null です。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeInfo インターフェイス](iclrruntimeinfo-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
- [.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [ホスティング](index.md)
