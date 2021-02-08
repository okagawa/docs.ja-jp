---
description: 詳細については、「Coeesの Tdowncom 関数」を参照してください。
title: CoEEShutDownCOM 関数
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
ms.openlocfilehash: 4f1ac8107c9a121ebf52ef21a5f2c9006880914f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799864"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM 関数

共通言語ランタイム (CLR) に対して、ランタイム呼び出し可能ラッパー (RCW) 内に保持されているすべてのインターフェイスポインターを強制的に解放します。 これにより、すべての RCW キャッシュが解放されます。 このグローバル関数は .NET Framework 4 では非推奨とされます。 代わりに、特定のランタイムのエントリポイントを使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>解説  

 この関数は、最初にすべての `CoEEShutDownCOM` コンテキストのすべての rcw とすべてのキャッシュを解放してから、セットアップに存在するすべての破棄通知を削除します。 DLL のアンロードは行われません。  
  
> [!CAUTION]
> この関数は、プロセスに読み込まれるすべてのランタイムに影響します。  
  
 .NET Framework 4 から、影響を与える特定のランタイムに対して、この関数のエントリポイントを呼び出します。 エントリポイントを取得するには、 [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) メソッドを呼び出し、"Coees Tdowncom" を指定します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ グローバル静的関数](../metadata/metadata-global-static-functions.md)
