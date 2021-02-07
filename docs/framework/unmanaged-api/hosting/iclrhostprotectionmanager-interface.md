---
description: 詳細については、「ICLRHostProtectionManager インターフェイス」を参照してください。
title: ICLRHostProtectionManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 60d27a8c1a24720bbfdcde52a5495425279d5ac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689248"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager インターフェイス

ホストが、部分的に信頼されたコードで実行される特定のマネージクラス、メソッド、プロパティ、およびフィールドをブロックできるようにします。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|致命的な共通言語ランタイム (CLR) エラーを引き起こす可能性のあるまれな競合状態が発生しないことを保証します。|  
|[SetProtectedCategories メソッド](iclrhostprotectionmanager-setprotectedcategories-method.md)|部分的に信頼されたコードでの実行をブロックする必要がある、マネージ型とメンバーのカテゴリを指定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EApiCategories 列挙型](eapicategories-enumeration.md)
- [ICLRControl インターフェイス](iclrcontrol-interface.md)
