---
title: ICorDebugEval インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
ms.openlocfilehash: f13cd6d6cae5bae0c51674e00f275a2c4853c915
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976227"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval インターフェイス

デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](icordebugeval-abort-method.md)|この`ICorDebugEval`オブジェクトが現在実行している計算を中止します。|  
|[CallFunction メソッド](icordebugeval-callfunction-method.md)|指定された関数の呼び出しを設定します。 (.NET Framework バージョン2.0 で廃止されました。代わりに[ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md)を使用してください。)|  
|[CreateValue メソッド](icordebugeval-createvalue-method.md)|初期値0または null を指定して、指定した型の "ICorDebugValue" オブジェクトへのインターフェイスポインターを取得します。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md)を使用してください。)|  
|[GetResult メソッド](icordebugeval-getresult-method.md)|評価の結果を格納し`ICorDebugValue`ているへのインターフェイスポインターを取得します。|  
|[GetThread メソッド](icordebugeval-getthread-method.md)|この評価が実行されているか実行される "表示スレッド" へのインターフェイスポインターを取得します。|  
|[IsActive メソッド](icordebugeval-isactive-method.md)|この`ICorDebugEval`オブジェクトが現在実行中かどうかを示す値を取得します。|  
|[NewArray メソッド](icordebugeval-newarray-method.md)|指定した要素の型と次元の新しい配列を割り当てます。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md)を使用してください。)|  
|[NewObject メソッド](icordebugeval-newobject-method.md)|新しいオブジェクトインスタンスを割り当て、指定したコンストラクターメソッドを呼び出します。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md)を使用してください。)|  
|[NewObjectNoConstructor メソッド](icordebugeval-newobjectnoconstructor-method.md)|コンストラクターメソッドを呼び出さずに、指定した型の新しいオブジェクトインスタンスを割り当てます。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md)を使用してください。)|  
|[NewString メソッド](icordebugeval-newstring-method.md)|指定された内容を持つ新しい文字列オブジェクトを割り当てます。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugEval`オブジェクトは、評価を実行するために使用される特定のスレッドのコンテキストで作成されます。 特定の評価で使用されるすべてのオブジェクトと型は、同じアプリケーションドメイン内に存在する必要があります。 このアプリケーションドメインは、スレッドの現在のアプリケーションドメインと同じである必要はありません。 評価は入れ子にすることができます。  
  
 評価の操作が完了しないのは、デバッガーが "を実行してい[ます:: Continue](icordebugcontroller-continue-method.md)" というメッセージを呼び出し、次に、"は、" は、"は、" のようなコール[バック](icordebugmanagedcallback-evalcomplete-method.md)を受け取ります。 他のスレッドの実行を許可せずに評価機能を使用する必要がある場合は、"が表示されない[ようにし](icordebugcontroller-stop-method.md)てください:: [SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md)またはのいずれかを使用してスレッドを中断する::[続行](icordebugcontroller-continue-method.md)します。  
  
 評価の進行中にユーザーコードが実行されているので、クラスの読み込みやブレークポイントなどのデバッグイベントが発生する可能性があります。 デバッガーは、これらのイベントに対して通常どおりコールバックを受け取ります。 評価の状態は、通常のプログラムの状態の検査の一部として表示されます。 スタックチェーンはチェーンに`CHAIN_FUNC_EVAL`なります ("CorDebugStepReason" 列挙型と、「の場合は、" [: getreason](icordebugchain-getreason-method.md) " メソッドを参照してください)。 完全なデバッガー API は通常どおりに動作します。  
  
 デッドロックまたは無限ループの状態が発生した場合、ユーザーコードが完全に完了することはありません。 このような場合は、プログラムを再開する前に、「いいね! [: Abort](icordebugeval-abort-method.md) 」を呼び出す必要があります。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
