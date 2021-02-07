---
description: '詳細については、次を参照してください: のクラスインターフェイス'
title: ICorDebugClass インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 5ded26a8b3a98bd273bbfe1bfa9efd1bb70d5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711506"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass インターフェイス

基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetModule メソッド](icordebugclass-getmodule-method.md)|このクラスを定義するモジュールを取得します。|  
|[GetStaticFieldValue メソッド](icordebugclass-getstaticfieldvalue-method.md)|指定された静的フィールドの値を取得します。|  
|[GetToken メソッド](icordebugclass-gettoken-method.md)|`TypeDef`このクラスのメタデータトークンを取得します。|  
  
## <a name="remarks"></a>解説  

 インターフェイスは、 `ICorDebugClass` インスタンスジェネリック型を表します。 は、インスタンス化されたジェネリック型を表します。 たとえば、は `Hashtable<K, V>` で表されますが、は `ICorDebugClass` `Hashtable<Int32, String>` によって表さ `ICorDebugType` れます。  
  
 非ジェネリック型は、との両方で表され `ICorDebugClass` `ICorDebugType` ます。 後者のインターフェイスは、型のインスタンス化を処理するために .NET Framework バージョン2.0 で導入されました。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
