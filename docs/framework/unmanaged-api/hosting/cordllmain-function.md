---
title: _CorDllMain 関数
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: 1b3ebcabc66ee7ca29245bb02d958be311bc65fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673697"
---
# <a name="_cordllmain-function"></a>\_CorDllMain 関数

共通言語ランタイム (CLR) を初期化し、DLL アセンブリの CLR ヘッダー内のマネージエントリポイントを検索して、実行を開始します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `hInst`  
 から読み込まれたモジュールのインスタンスハンドル。  
  
 `dwReason`  
 からDLL のエントリポイント関数が呼び出される理由を示します。 このパラメーターには、DLL \_ PROCESS_ATTACH、dll \_ スレッド \_ のアタッチ、dll \_ スレッドの \_ アタッチ、または dll プロセスの \_ \_ デタッチのいずれかの値を指定できます。 これらの値の詳細については、Platform SDK のドキュメントを参照してください `DllMain` 。  
  
 `lpReserved`  
 から未使用.  
  
## <a name="return-value"></a>戻り値  

 このメソッドは `true` 、成功し `false` た場合はを返し、エラーが発生した場合はを返します。  
  
## <a name="remarks"></a>注釈  

 この関数は、DLL アセンブリのオペレーティングシステムローダーによって呼び出されます。 実行可能アセンブリの場合、ローダーは代わりに[ \_ CorExeMain](corexemain-function.md)関数を呼び出します。  
  
 オペレーティングシステムローダーは、DLL ファイルで指定されたエントリポイントに関係なく、このメソッドを呼び出します。  
  
`_CorDllMain`関数は、オペレーティングシステムローダーによって直接呼び出されます。
  
 詳細については、 [ \_ corvalidateimage](corvalidateimage-function.md)トピックの「解説」を参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ グローバル静的関数](../metadata/metadata-global-static-functions.md)
