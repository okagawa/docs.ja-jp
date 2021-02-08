---
description: '詳細については、次を参照してください: WriteableMetadataUpdateMode 列挙型'
title: WriteableMetadataUpdateMode 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: b8136963e315c429643bd0ebf4bdb509d5173bec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800514"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode 列挙型

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 メモリ内のメタデータ更新をデバッガーに対して可視にするかどうかを指定する値を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー名|説明|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|メモリ内のメタデータ更新を可視にするときに、.NET Framework の以前のバージョンとの互換性を保持します。 詳細については、次の「解説」を参照してください。|  
|`AlwaysShowUpdates`|メモリ内のメタデータ更新をデバッガーに対して可視にします。|  
  
## <a name="remarks"></a>解説  

 列挙体のメンバーを `WriteableMetadataUpdateMode` [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) メソッドに渡して、ターゲットプロセス内のメタデータに対するメモリ内更新がデバッガーに表示されるかどうかを制御できます。  
  
 `LegacyCompatPolicy` オプションは、4.5.2 より前の .NET Framework のバージョンと同じ動作を適用します。 これは多くの場合、メタデータの更新が可視でないことを意味します。 しかし、多数のデバッグ メソッドを呼び出すとデバッガーは明示的に強制変換し、更新を可視にします。 たとえば、デバッガーが、メソッドの元のメタデータに見つからない変数のインデックス [を渡すと](icordebugilframe-getlocalvariable-method.md) 、そのモジュールのすべてのメタデータが、プロセスの現在の状態と一致するスナップショットに更新されます。 言い換えれば、`LegacyCompatPolicy` オプションでは、メタデータの更新によりアンマネージ デバギング API のその他の部分がどのように使用されているかによって、使用可能なメタデータ更新がデバッガーに対して全く可視でない場合、一部が可視になる場合、すべてが可視になる場合があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙体のデバッグ](debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode メソッド](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
