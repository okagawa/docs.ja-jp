---
title: ICorProfilerInfo::GetFunctionInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 6aaa02d72dd10fe72d773246d55216143786dabb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722540"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>ICorProfilerInfo::GetFunctionInfo メソッド

指定された関数の親クラスとメタデータトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>パラメーター  

 `functionId`  
 から親クラスおよびメタデータトークンを取得する対象の関数の ID。  
  
 `pClassId`  
 [out] 関数の親クラスへのポインター。  
  
 `pModuleId`  
 [out] 関数の親クラスが定義されているモジュールへのポインター。  
  
 `pToken`  
 [out] 関数のメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>注釈  

 プロファイラーコードは、 [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) を呼び出して、指定されたモジュールのメタデータインターフェイスを取得できます。 `pToken` が参照している場所に返されるメタデータ トークンを使用すると、関数のメタデータにアクセスできます。  
  
 `ClassID`ジェネリッククラスの関数は、関数の使用に関するコンテキスト情報がないと取得できない可能性があります。 この場合、 `pClassId` は0になります。 プロファイラーコードでは、 [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) と COR_PRF_FRAME_INFO 値を使用して、より多くのコンテキストを提供する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
