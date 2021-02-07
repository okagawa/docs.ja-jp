---
description: 詳細については、「IAssemblyName インターフェイス」を参照してください。
title: IAssemblyName インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: fb5949572adc533bab5ed26ee969267f430f36ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760707"
---
# <a name="iassemblyname-interface"></a>IAssemblyName インターフェイス

アセンブリの一意の id を記述および操作するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](iassemblyname-clone-method.md)|このオブジェクトの簡易コピーを作成し `IAssemblyName` ます。|  
|[Finalize メソッド](iassemblyname-finalize-method.md)|このオブジェクトが、 `IAssemblyName` デストラクターが呼び出される前にリソースを解放し、その他のクリーンアップ操作を実行できるようにします。|  
|[GetDisplayName メソッド](iassemblyname-getdisplayname-method.md)|このオブジェクトによって参照されるアセンブリの、人間が判読できる名前を取得し `IAssemblyName` ます。|  
|[GetName メソッド](iassemblyname-getname-method.md)|このオブジェクトによって参照されるアセンブリの単純な、暗号化されていない名前を取得し `IAssemblyName` ます。|  
|[GetProperty メソッド](iassemblyname-getproperty-method.md)|指定したによって参照されるプロパティへのポインターを取得し `PropertyId` ます。|  
|[GetVersion メソッド](iassemblyname-getversion-method.md)|このオブジェクトによって参照されるアセンブリのバージョン情報を取得し `IAssemblyName` ます。|  
|[IsEqual メソッド](iassemblyname-isequal-method.md)|指定した `IAssemblyName` `IAssemblyName` 比較フラグに基づいて、指定したオブジェクトがこのと等しいかどうかを判断します。|  
|[SetProperty メソッド](iassemblyname-setproperty-method.md)|指定したによって参照されるプロパティの値を設定 `PropertyId` します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IAssemblyEnum インターフェイス](iassemblyenum-interface.md)
