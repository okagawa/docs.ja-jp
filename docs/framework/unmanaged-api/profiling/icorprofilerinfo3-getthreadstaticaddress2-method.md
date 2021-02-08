---
description: '詳細について: ICorProfilerInfo3:: GetThreadStaticAddress2 メソッド'
title: ICorProfilerInfo3::GetThreadStaticAddress2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: 6734996435206f9e0c837eba39df1ad81677e54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794547"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a>ICorProfilerInfo3::GetThreadStaticAddress2 メソッド

指定したスレッドおよびアプリケーション ドメインのスコープ内にある、指定したスレッド内静的フィールドのアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>パラメーター  

 `classId`  
 から要求されたスレッド静的フィールドを含むクラスの ID。  
  
 `fieldToken`  
 から要求されたスレッドの静的フィールドのメタデータトークン。  
  
 `appDomainId`  
 [in] アプリケーション ドメインの ID。  
  
 `threadId`  
 から要求された静的フィールドのスコープであるスレッドの ID。  
  
 `ppAddress`  
 入出力指定したスレッド内の静的フィールドのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 `GetThreadStaticAddress2`メソッドは、次のいずれかを返す場合があります。  
  
- 指定されたコンテキストで、指定された静的フィールドにアドレスが割り当てられていない場合は CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- ガベージコレクションヒープ内に存在する可能性があるオブジェクトのアドレス。 これらのアドレスは、ガベージコレクションの後に無効になることがあります。そのため、ガベージコレクションの後、プロファイラーはそれらが有効であると想定してはなりません。  
  
 では、クラスのクラスコンストラクターが完了する前に、 `GetThreadStaticAddress2` すべての静的フィールドに対して CORPROF_E_DATAINCOMPLETE が返されます。ただし、静的フィールドの一部は既に初期化されており、ガベージコレクションオブジェクトがルート化される場合があります。  
  
 [ICorProfilerInfo2:: GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md)メソッドはメソッドに似てい `GetThreadStaticAddress2` ますが、アプリケーションドメインの引数を受け取りません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo3 インターフェイス](icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [プロファイル](index.md)
