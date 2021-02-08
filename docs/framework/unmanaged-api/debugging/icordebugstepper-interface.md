---
description: 詳細については、「ICorDebugStepper インターフェイス」を参照してください。
title: ICorDebugStepper インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: a16df9d25b4d87b0638448c1fdf8fec4759261d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803586"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper インターフェイス

デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Deactivate メソッド](icordebugstepper-deactivate-method.md)|これにより、 `ICorDebugStepper` 受信した最後のステップコマンドがキャンセルされます。|  
|[IsActive メソッド](icordebugstepper-isactive-method.md)|この `ICorDebugStepper` が現在ステップを実行しているかどうかを示す値を取得します。|  
|[SetInterceptMask メソッド](icordebugstepper-setinterceptmask-method.md)|ステップインするコードの種類を指定する CorDebugIntercept 値を設定します。|  
|[SetRangeIL メソッド](icordebugstepper-setrangeil-method.md)|[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md)を呼び出すかどうかを示す値を設定します。これは、ネイティブコードまたはステップスルー中のメソッドの Microsoft 中間言語 (MSIL) コードを基準として、引数の値を渡します。|  
|[SetUnmappedStopMask メソッド](icordebugstepper-setunmappedstopmask-method.md)|実行が停止するマップされていないコードの種類を指定する CorDebugUnmappedStop 値を設定します。|  
|[Step メソッド](icordebugstepper-step-method.md)|これにより、このが格納している `ICorDebugStepper` スレッドを1ステップずつ実行します。また、必要に応じて、スレッド内で呼び出される関数を使用したシングルステップ実行を継続します。|  
|[StepOut メソッド](icordebugstepper-stepout-method.md)|これにより、この `ICorDebugStepper` が格納しているスレッドを1ステップずつ実行し、現在のフレームが呼び出し元のフレームに制御を返すときに完了します。|  
|[StepRange メソッド](icordebugstepper-steprange-method.md)|これにより、このが `ICorDebugStepper` 格納しているスレッドを1ステップずつ実行し、指定した範囲の最後のコードに到達したときにを返します。|  
  
## <a name="remarks"></a>解説  

 この `ICorDebugStepper` インターフェイスは、次の目的で機能します。  
  
- 発行されたステップコマンドとそのコマンドの完了の間の識別子として機能します。  
  
- これは、実行可能なすべてのステップをカプセル化するための中心的なインターフェイスを提供します。  
  
- これにより、ステップ実行操作を途中で取り消すことができます。  
  
 スレッドごとに複数のステッパが存在する場合があります。 たとえば、関数をステップオーバーしている間にブレークポイントがヒットし、ユーザーがその関数内で新しいステップ実行操作を開始する場合があります。 この状況をどのように処理するかは、デバッガーによって決定されます。 デバッガーでは、元のステップ実行操作をキャンセルするか、2つの操作を入れ子にすることができます。 インターフェイスでは、 `ICorDebugStepper` 両方の選択肢がサポートされています。  
  
 共通言語ランタイム (CLR) がクロススレッドでマーシャリングされた呼び出しを行う場合、ステッパはスレッド間で移行される可能性があります。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
