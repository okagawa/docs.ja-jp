---
description: 詳細については、「ICorDebugAssembly3 インターフェイス」を参照してください。
title: ICorDebugAssembly3 インターフェイス
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 3a8cabf41dffa75d82c2b6fde53dff2ede4838e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791505"
---
# <a name="icordebugassembly3-interface"></a>ICorDebugAssembly3 インターフェイス

コンテナーのアセンブリとそれらに含まれるアセンブリのサポートを提供するために、ICorDebugAssembly インターフェイスを論理的に拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateContainedAssemblies メソッド](icordebugassembly3-enumeratecontainedassemblies-method.md)|このアセンブリに含まれているアセンブリの列挙子を取得します。|  
|[GetContainerAssembly メソッド](icordebugassembly3-getcontainerassembly-method.md)|この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは .NET ネイティブでのみ使用可能です。 インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
