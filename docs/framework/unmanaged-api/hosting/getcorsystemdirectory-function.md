---
title: GetCORSystemDirectory 関数
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 21b01156afceb24ab5c132894fae6922d7b97e59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733296"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory 関数

プロセスに読み込まれる共通言語ランタイム (CLR) のインストールディレクトリを返します。 インストールディレクトリは完全に修飾されています。たとえば、"c:\windows\microsoft.net\framework\v1.0.3705" のようになります。  
  
 この関数の使用は非推奨とされます。 .NET Framework 4 で提供される [ICLRRuntimeInfo:: GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) メソッドに置き換えられています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>パラメーター  

 `pbuffer`  
 入出力プロセスに読み込まれたランタイムのインストールディレクトリの完全修飾名が含まれた文字列をランタイムが返すバッファー。 ランタイムがまだプロセスに読み込まれていない場合、関数はコンピューターにインストールされている最新バージョンのランタイムの適切なディレクトリ情報を返します。  
  
 `cchBuffer`  
 からのサイズ (バイト単位) `pbuffer` 。  
  
 `dwLength`  
 入出力で返された文字数 `pbuffer` 。  
  
## <a name="remarks"></a>注釈  
  
> [!CAUTION]
> CLR のバージョン4を実行しているプロセスでは、この関数を使用しないでください。 コンピューターに以前のバージョンの CLR がインストールされている場合、この関数はそのバージョンのインストールディレクトリを返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
