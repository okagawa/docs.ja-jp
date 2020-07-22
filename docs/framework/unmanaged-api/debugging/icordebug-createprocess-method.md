---
title: ICorDebug::CreateProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
ms.openlocfilehash: b9ae2b36bff9b4a6c048a8de99fa7d09350b1401
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859708"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess メソッド
デバッガーの制御下でプロセスとそのプライマリスレッドを起動します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateProcess (  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `lpApplicationName`  
 から起動されたプロセスによって実行されるモジュールを指定する、null で終わる文字列へのポインター。 モジュールは、呼び出し元プロセスのセキュリティコンテキストで実行されます。  
  
 `lpCommandLine`  
 から起動されたプロセスによって実行されるコマンドラインを指定する、null で終わる文字列へのポインター。 アプリケーション名 (たとえば、"al.exe") は最初の引数である必要があります。  
  
 `lpProcessAttributes`  
 からプロセスのセキュリティ記述子`SECURITY_ATTRIBUTES`を指定する Win32 構造体へのポインター。 が`lpProcessAttributes` null の場合、プロセスは既定のセキュリティ記述子を取得します。  
  
 `lpThreadAttributes`  
 からプロセスのプライマリスレッド`SECURITY_ATTRIBUTES`のセキュリティ記述子を指定する Win32 構造体へのポインター。 が`lpThreadAttributes` null の場合、スレッドは既定のセキュリティ記述子を取得します。  
  
 `bInheritHandles`  
 から`true`呼び出しプロセスの各継承可能なハンドルが、起動されるプロセスによって継承される`false`ことを示す場合はに設定し、ハンドルが継承されないことを示す場合はに設定します。 継承されたハンドルは、元のハンドルと同じ値とアクセス権を持ちます。  
  
 `dwCreationFlags`  
 から優先順位クラスと起動されたプロセスの動作を制御する[Win32 プロセス作成フラグ](/windows/win32/procthread/process-creation-flags)のビットごとの組み合わせ。  
  
 `lpEnvironment`  
 から新しいプロセスの環境ブロックへのポインター。  
  
 `lpCurrentDirectory`  
 からプロセスの現在のディレクトリへの完全パスを指定する、null で終わる文字列へのポインター。 このパラメーターが null の場合、新しいプロセスは呼び出しプロセスと同じ現在のドライブとディレクトリを持ちます。  
  
 `lpStartupInfo`  
 から起動された`STARTUPINFOW`プロセスのメインウィンドウのウィンドウステーション、デスクトップ、標準ハンドル、および外観を指定する Win32 構造体へのポインター。  
  
 `lpProcessInformation`  
 から起動するプロセスに`PROCESS_INFORMATION`関する識別情報を指定する Win32 構造体へのポインター。  
  
 `debuggingFlags`  
 からデバッグオプションを指定する CorDebugCreateProcessFlags 列挙体の値。  
  
 `ppProcess`  
 入出力プロセスを表す、オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  
 このメソッドのパラメーターは、Win32 `CreateProcess`メソッドのパラメーターと同じです。  
  
 アンマネージ混合モードのデバッグを有効に`dwCreationFlags`するには、を DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS に設定します。 マネージデバッグのみを使用する場合は、これらのフラグを設定しないでください。  
  
 デバッガーとデバッグするプロセス (アタッチされたプロセス) が1つのコンソールを共有し、相互運用デバッグが使用されている場合、アタッチされたプロセスがコンソールロックを保持し、デバッグイベントで停止する可能性があります。 デバッガーは、コンソールの使用をブロックします。 この問題を回避するには、 `dwCreationFlags`パラメーターに CREATE_NEW_CONSOLE フラグを設定します。  
  
 相互運用デバッグは、IA-64 ベースおよび AMD64 ベースのプラットフォームなど、Win9x および x86 以外のプラットフォームではサポートされていません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](icordebug-interface.md)
