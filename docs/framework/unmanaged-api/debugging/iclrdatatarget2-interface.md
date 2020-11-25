---
title: ICLRDataTarget2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: dee5108439610b67c3397cebcd8ee5f84d4eacea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723637"
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2 インターフェイス

ターゲットプロセスの仮想メモリ領域を操作するためにデータアクセスサービス層によって使用される [ICLRDataTarget](iclrdatatarget-interface.md) のサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AllocVirtual メソッド](iclrdatatarget2-allocvirtual-method.md)|ターゲットプロセスのアドレス空間にメモリを割り当てます。|  
|[FreeVirtual メソッド](iclrdatatarget2-freevirtual-method.md)|ターゲットプロセスのアドレス空間で以前に割り当てられたメモリを解放します。|  
  
## <a name="remarks"></a>注釈  

 API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。 たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。 ターゲットは、メモリ領域の変更をサポートしない可能性があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
