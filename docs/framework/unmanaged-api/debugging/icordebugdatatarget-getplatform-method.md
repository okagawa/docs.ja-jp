---
title: ICorDebugDataTarget::GetPlatform メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: e8612b23cbfa506fddb2fad712848b285b9ac28e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679794"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform メソッド

ターゲットプロセスが実行されているプラットフォーム (プロセッサアーキテクチャやオペレーティングシステムなど) に関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pTargetPlatform`  
 入出力ターゲットプラットフォームを記述する [Cordebugplatformenum](cordebugplatform-enumeration.md) 列挙体へのポインター。  
  
## <a name="remarks"></a>注釈  

 `CorDebugPlatformEnum`列挙型の戻り値は、ポインターのサイズ、アドレス空間のレイアウト、レジスタセット、命令形式、コンテキストレイアウト、呼び出し規約などのターゲットプロセスの詳細を確認するために、 [ICorDebug](icordebug-interface.md)インターフェイスによって使用されます。  
  
 値は、使用されている `pTargetPlatform` 実際のハードウェアを指定する代わりに、ターゲットに対してエミュレートされるプラットフォームを参照する場合があります。 たとえば、64-bit エディションの Windows オペレーティングシステムで Windows on Windows (WOW) 環境で実行されているプロセスでは、 `CORDB_PLATFORM_WINDOWS_X86` [Cordebugplatformenum](cordebugplatform-enumeration.md) 列挙型の値を使用する必要があります。  
  
 このメソッドは成功する必要があります。 失敗した場合、ターゲットプラットフォームは使用できません。 メソッドは、次の理由により失敗する可能性があります。  
  
- ターゲットに対してエミュレートされるプラットフォームは使用できません。  
  
- ターゲットプラットフォームの実際のハードウェアは使用できません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget インターフェイス](icordebugdatatarget-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
