---
title: ClrCreateManagedInstance 関数
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: ecd618ecf08836ea5e38ce738f97fc91ee6426f4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616815"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 関数
指定したマネージド型のインスタンスを作成します。  
  
 この関数は .NET Framework 4 で非推奨とされました。 COM アクティブ化を使用してマネージ型のインスタンスを作成するか、ホストを使用します (「 [.NET Framework 4 および4.5 で追加された CLR ホストインターフェイス](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)」を参照してください)。  
  
## <a name="syntax"></a>構文  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pTypeName`  
 から要求されているインスタンス型の名前へのポインター。  
  
 `riid`  
 から`IID`要求されているインスタンス型の。  
  
 `ppObject`  
 入出力呼び出し元によって要求されたマネージ型のインスタンスへのポインターへのポインター。  
  
## <a name="remarks"></a>解説  
 共通言語ランタイムは、既にプロセスに読み込まれている必要があります。 たとえば、関数が呼び出される前に[Corbindtoruntimeex](corbindtoruntimeex-function.md)関数の呼び出しを使用して読み込むことができ `ClrCreateManagedInstance` ます。 ランタイムが読み込まれていない場合、は `ClrCreateManagedInstance` まず、ランタイムの v v1.0.3705 の読み込みを試みます。 失敗した場合は、ランタイムの最新バージョンの読み込みが試行されます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
- [ホスティング](index.md)
