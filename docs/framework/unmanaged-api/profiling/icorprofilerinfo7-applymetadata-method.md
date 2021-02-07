---
description: '詳細について: ICorProfilerInfo7:: ApplyMetaData メソッド'
title: 'ICorProfilerInfo7:: ApplyMetaData メソッド'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 3a4554357ede85d936e8bf9c87c6b9c096dab188
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737130"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7:: ApplyMetaData メソッド

[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 メソッドによって新たに定義されたメタデータ `IMetadataEmit::Define*` を、指定したモジュールに適用します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `moduleID`  
 からメタデータが変更されたモジュールの識別子。  
  
## <a name="remarks"></a>解説  

 [Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md)コールバックの後にメタデータの変更が行われた場合は、新しいメタデータを使用する前にこのメソッドを呼び出す必要があります。  
  
 `ApplyMetaData` では、次の種類のメタデータの追加のみがサポートされています。  
  
- `AssemblyRef`[IMetaDataAssemblyEmit::D efineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md)を呼び出すことによって作成するレコード。 メソッドをオーバーライドします。  
  
- `TypeRef`[IMetaDataEmit::D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md)メソッドを呼び出すことによって作成するレコード。  
  
- `TypeSpec` レコード。 [IMetaDataEmit:: GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) メソッドを呼び出すことによって作成します。  
  
- `MemberRef`[IMetaDataEmit::D efinememberref](../metadata/imetadataemit-definememberref-method.md)メソッドを呼び出すことによって作成するレコード。  
  
- `MemberSpec`[IMetaDataEmit2::D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md)メソッドを呼び出すことによって作成するレコード。  
  
- `UserString` レコード。 [IMetaDataEmit::D efineUserString](../metadata/imetadataemit-defineuserstring-method.md) メソッドを呼び出すことによって作成します。  

.NET Core 3.0 以降では、 `ApplyMetaData` 次の型もサポートしています。

- `TypeDef`[IMetaDataEmit::D efineTypeDef](../metadata/imetadataemit-definetypedef-method.md)メソッドを呼び出すことによって作成するレコード。

- `MethodDef`[IMetaDataEmit::D efinemethod](../metadata/imetadataemit-definemethod-method.md)メソッドを呼び出すことによって作成するレコード。 ただし、既存の型に仮想メソッドを追加することはサポートされていません。 仮想メソッドは、 [Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) コールバックの前に追加する必要があります。

## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo7 インターフェイス](icorprofilerinfo7-interface.md)
