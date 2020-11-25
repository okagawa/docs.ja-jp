---
title: ICorProfilerInfo::GetModuleMetaData メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 74df0fb412e7fb3d9f779391ec84f07a0379a2cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724118"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData メソッド

指定したモジュールにマップされるメタデータインターフェイスインスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>パラメーター  

 `moduleId`  
 からインターフェイスインスタンスのマップ先となるモジュールの ID。  
  
 `dwOpenFlags`  
 からマニフェストファイルを開くモードを指定する [Coropenflags](../metadata/coropenflags-enumeration.md) 列挙体の値。 、、 `ofRead` およびの各 `ofWrite` ビットのみ `ofNoTransform` が有効です。  
  
 `riid`  
 からインスタンスを取得するメタデータインターフェイスの参照 ID (GUID)。 インターフェイスの一覧については、「 [メタデータインターフェイス](../metadata/metadata-interfaces.md) 」を参照してください。  
  
 `ppOut`  
 入出力メタデータインターフェイスインスタンスのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 メタデータを読み取り/書き込みモードで開くように要求することはできますが、メタデータに対して行われた変更はコンパイラからのものとして最適化できないため、プログラムのメタデータ実行が遅くなります。  
  
 一部のモジュール (リソースモジュールなど) にはメタデータがありません。 このような場合、 `GetModuleMetaData` は S_FALSE の HRESULT 値を返し、* では null を返し `ppOut` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
