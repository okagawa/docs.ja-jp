---
description: '詳細情報: の説明'
title: ICorDebugAppDomain インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 5f1ac20a7376a741da2e34de74c810c0f45e8293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754200"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain インターフェイス

アプリケーション ドメインをデバッグするためのメソッドを提供します。 このインターフェイスは、というコントロールのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Attach メソッド](icordebugappdomain-attach-method.md)|デバッガーをアプリケーションドメインにアタッチします。|  
|[EnumerateAssemblies メソッド](icordebugappdomain-enumerateassemblies-method.md)|アプリケーションドメイン内のアセンブリの列挙子を取得します。|  
|[EnumerateBreakpoints メソッド](icordebugappdomain-enumeratebreakpoints-method.md)|アプリケーションドメイン内のすべてのアクティブなブレークポイントの列挙子を取得します。|  
|[EnumerateSteppers メソッド](icordebugappdomain-enumeratesteppers-method.md)|アプリケーションドメイン内のすべてのアクティブな steppers の列挙子を取得します。|  
|[GetId メソッド](icordebugappdomain-getid-method.md)|アプリケーションドメインの一意の ID を取得します。|  
|[GetModuleFromMetaDataInterface メソッド](icordebugappdomain-getmodulefrommetadatainterface-method.md)|指定されたメタデータインターフェイスを持つ、のモジュールオブジェクトを取得します。|  
|[GetName メソッド](icordebugappdomain-getname-method.md)|アプリケーションドメインの名前を取得します。|  
|[GetObject メソッド](icordebugappdomain-getobject-method.md)|共通言語ランタイム (CLR) アプリケーションドメインへのインターフェイスポインターを取得します。|  
|[GetProcess メソッド](icordebugappdomain-getprocess-method.md)|アプリケーションドメインを格納しているプロセスを取得します。|  
|[IsAttached メソッド](icordebugappdomain-isattached-method.md)|デバッガーがアプリケーションドメインにアタッチされているかどうかを判断します。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
