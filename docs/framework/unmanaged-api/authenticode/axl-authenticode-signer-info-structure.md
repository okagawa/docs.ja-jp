---
title: AXL_AUTHENTICODE_SIGNER_INFO 構造体
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 1bb6df4aa82f8dfc367083732af2065aba9d07b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679989"
---
# <a name="axl_authenticode_signer_info-structure"></a>AXL_AUTHENTICODE_SIGNER_INFO 構造体

Authenticode の署名者情報を定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`cbSize`|この構造のサイズ。|  
|`dwError`|エラー コード。|  
|`algHash`|ハッシュアルゴリズム。|  
|`pwszHash`|ハッシュです。|  
|`pwszDescription`|説明です。|  
|`pwszDescriptionUrl`|説明の URL。|  
|`pChainContext`|署名者のチェーン コンテキスト。 [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context)構造を参照してください。|  
  
## <a name="see-also"></a>関連項目

- [Authenticode](index.md)
