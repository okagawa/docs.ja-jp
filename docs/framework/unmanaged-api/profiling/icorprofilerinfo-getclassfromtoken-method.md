---
description: '詳細について: ICorProfilerInfo:: GetClassFromToken メソッド'
title: ICorProfilerInfo::GetClassFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 0460a9b767f29f108a2b290b848f4cc6b6394ecb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647753"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a>ICorProfilerInfo::GetClassFromToken メソッド

メタデータトークンを指定して、クラスの ID を取得します。 このメソッドは .NET Framework バージョン2.0 では廃止されています。 代わりに [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) を使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a>パラメーター  

 `moduleID`  
 からクラスを含むモジュールの ID。  
  
 `typeDef`  
 から `mdTypeDef` クラスを参照するメタデータトークン。  
  
 `cTypeArgs`  
 入出力クラス ID へのポインター。  
  
## <a name="remarks"></a>解説  

 このメソッドは互換性のために残されています。代わりに、 `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` すべての型に対してを使用します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** 1.0、1.1  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
