---
title: ICorProfilerInfo2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
ms.openlocfilehash: 4480fefa51eec2f2751bd71910db87b72a1c32cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496727"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 インターフェイス
コードプロファイラーが共通言語ランタイム (CLR) と通信してイベント監視と要求情報を制御するために使用するメソッドを提供します。 インターフェイスは、 `ICorProfilerInfo2` [ICorProfilerInfo](icorprofilerinfo-interface.md)インターフェイスの拡張機能です。 つまり、.NET Framework バージョン2.0 以降のバージョンでサポートされている新しいメソッドが用意されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DoStackSnapshot メソッド](icorprofilerinfo2-dostacksnapshot-method.md)|マネージ呼び出しフレームをプロファイラーに報告するために、指定したスレッドのスタックを走査します。|  
|[EnumModuleFrozenObjects メソッド](icorprofilerinfo2-enummodulefrozenobjects-method.md)|指定したモジュール内の固定されたオブジェクトを反復処理できる列挙子を取得します。|  
|[GetAppDomainStaticAddress メソッド](icorprofilerinfo2-getappdomainstaticaddress-method.md)|指定したアプリケーションドメインのスコープ内にある、指定したアプリケーションドメインの静的フィールドのアドレスを取得します。|  
|[GetArrayObjectInfo メソッド](icorprofilerinfo2-getarrayobjectinfo-method.md)|配列オブジェクトに関する詳細情報を取得します。|  
|[GetBoxClassLayout メソッド](icorprofilerinfo2-getboxclasslayout-method.md)|ボックス化された指定された値型のクラスレイアウトに関する情報を取得します。|  
|[GetClassFromTokenAndTypeArgs メソッド](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|`ClassID`指定されたメタデータトークンと `ClassID` 任意の型引数の値を使用して、型のを取得します。|  
|[GetClassIDInfo2 メソッド](icorprofilerinfo2-getclassidinfo2-method.md)|指定されたジェネリッククラスの親モジュール、クラスのメタデータトークン、 `ClassID` その親クラスの、および `ClassID` クラスの型引数 (存在する場合) のを取得します。|  
|[GetClassLayout メソッド](icorprofilerinfo2-getclasslayout-method.md)|指定したクラスで定義されるフィールドのメモリ内レイアウトに関する情報を取得します。 つまり、このメソッドはクラスのフィールドのオフセットを取得します。|  
|[GetCodeInfo2 メソッド](icorprofilerinfo2-getcodeinfo2-method.md)|指定した `FunctionID` に関連付けられているネイティブ コードの範囲を取得します。|  
|[GetContextStaticAddress メソッド](icorprofilerinfo2-getcontextstaticaddress-method.md)|指定されたコンテキストのスコープ内にある、指定されたコンテキスト静的フィールドのアドレスを取得します。|  
|[GetFunctionFromTokenAndTypeArgs メソッド](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|`FunctionID`指定されたメタデータトークン、クラス、および `ClassID` 任意の型引数の値を使用して、関数のを取得します。|  
|[GetFunctionInfo2 メソッド](icorprofilerinfo2-getfunctioninfo2-method.md)|関数の親クラス、メタデータ トークン、および型引数が存在する場合はそれぞれの `ClassID` を取得します。|  
|[GetGenerationBounds メソッド](icorprofilerinfo2-getgenerationbounds-method.md)|ガベージコレクトされたヒープのジェネレーションを構成するメモリ領域 (ヒープのセグメント) を取得します。|  
|[GetNotifiedExceptionClauseInfo メソッド](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|`catch` / `finally` / `filter` 実行される、または実行されたばかりの例外句 () のネイティブアドレスとフレーム情報を取得します。|  
|[GetObjectGeneration メソッド](icorprofilerinfo2-getobjectgeneration-method.md)|指定されたオブジェクトを格納しているヒープのセグメントを取得します。|  
|[GetRVAStaticAddress メソッド](icorprofilerinfo2-getrvastaticaddress-method.md)|指定された相対仮想アドレス (RVA) の静的フィールドのアドレスを取得します。|  
|[GetStaticFieldInfo メソッド](icorprofilerinfo2-getstaticfieldinfo-method.md)|指定したフィールドが静的であるスコープを取得します。|  
|[GetStringLayout メソッド](icorprofilerinfo2-getstringlayout-method.md)|文字列オブジェクトのレイアウトに関する情報を取得します。|  
|[GetThreadAppDomain メソッド](icorprofilerinfo2-getthreadappdomain-method.md)|指定したスレッドが現在コードを実行しているアプリケーションドメインの ID を取得します。|  
|[GetThreadStaticAddress メソッド](icorprofilerinfo2-getthreadstaticaddress-method.md)|指定したスレッドのスコープ内にある、指定したスレッド静的フィールドのアドレスを取得します。|  
|[SetEnterLeaveFunctionHooks2 メソッド](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|マネージ関数の "enter"、"leave"、および "tailcall" フックで呼び出されるプロファイラー実装関数を指定します。|  
  
## <a name="remarks"></a>解説  
 プロファイラーは、 `ICorProfilerInfo2` CLR と通信してイベントの監視と要求情報を制御するために、インターフェイスのメソッドを呼び出します。  
  
 インターフェイスのメソッドは、 `ICorProfilerInfo2` フリースレッドモデルを使用して CLR によって実装されます。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
 CLR は、 `ICorProfilerInfo2` [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)のプロファイラーの実装を使用して、初期化中に各コードプロファイラーにインターフェイスを渡します。 次に、コードプロファイラーは、インターフェイスのメソッドを呼び出して、 `ICorProfilerInfo2` CLR の制御下で実行されているマネージコードに関する情報を取得できます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
