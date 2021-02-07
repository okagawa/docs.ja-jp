---
description: '詳細情報: CoUninitializeEE 関数'
title: CoUninitializeEE 関数
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: e356135ea027bd52520eff9084ad2f7f09e1fe0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746166"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE 関数

`CoUninitializeEE` は互換性のために残されており、機能を提供しません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>解説  

 共通言語ランタイムの実行エンジンをプロセスからアンロードできません。 実行エンジンをシャットダウンするには、 [CorExitProcess](corexitprocess-function.md)を呼び出します。  
  
## <a name="see-also"></a>関連項目

- [CoInitializeEE 関数](coinitializeee-function.md)
- [メタデータ グローバル静的関数](../metadata/metadata-global-static-functions.md)
