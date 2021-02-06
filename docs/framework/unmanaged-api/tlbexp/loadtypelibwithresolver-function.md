---
description: '詳細情報: LoadTypeLibWithResolver 関数'
title: LoadTypeLibWithResolver 関数
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
ms.openlocfilehash: 6747199364a549d922ad73bfac3e93b329d1172a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646219"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 関数

タイプライブラリを読み込み、指定された [ITypeLibResolver インターフェイス](itypelibresolver-interface.md) を使用して、内部で参照されているタイプライブラリを解決します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szFile`  
 からタイプライブラリのファイルパス。  
  
 `regkind`  
 からタイプライブラリの登録方法を制御する [Regkind 列挙](/windows/win32/api/oleauto/ne-oleauto-regkind) フラグ。 指定できる値は次のとおりです。  
  
- `REGKIND_DEFAULT`: 既定の登録動作を使用します。  
  
- `REGKIND_REGISTER`: このタイプライブラリを登録します。  
  
- `REGKIND_NONE`: このタイプライブラリを登録しません。  
  
 `pTlbResolver`  
 から [ITypeLibResolver インターフェイス](itypelibresolver-interface.md)の実装へのポインター。  
  
 `pptlib`  
 入出力読み込まれているタイプライブラリへの参照。  
  
## <a name="return-value"></a>戻り値  

 次の表に示す HRESULT 値の1つ。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|正常終了しました。|  
|`E_OUTOFMEMORY`|メモリが不足しています。|  
|`E_POINTER`|1つ以上のポインターが無効です。|  
|`E_INVALIDARG`|1 つ以上の引数が無効です。|  
|`TYPE_E_IOERROR`|関数はファイルに書き込めませんでした。|  
|`TYPE_E_REGISTRYACCESS`|システム登録データベースを開けませんでした。|  
|`TYPE_E_INVALIDSTATE`|タイプライブラリを開けませんでした。|  
|`TYPE_E_CANTLOADLIBRARY`|タイプライブラリまたは DLL を読み込めませんでした。|  
  
## <a name="remarks"></a>解説  

 [Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)は、 `LoadTypeLibWithResolver` アセンブリからタイプライブラリへの変換プロセス中に関数を呼び出します。  
  
 この関数は、レジストリへの最小限のアクセスで、指定されたタイプライブラリを読み込みます。 次に、関数は、内部的に参照されるタイプライブラリのタイプライブラリを調べます。このタイプライブラリはそれぞれ、親タイプライブラリに読み込まれ、追加される必要があります。  
  
 参照されるタイプライブラリを読み込む前に、その参照ファイルのパスを完全なファイルパスに解決する必要があります。 これは、パラメーターで渡される[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)によって提供される[resolvetypelib メソッド](resolvetypelib-method.md)を使用して実現され `pTlbResolver` ます。  
  
 参照されているタイプライブラリの完全なファイルパスがわかっている場合、この関数は参照されている `LoadTypeLibWithResolver` タイプライブラリを読み込んで親タイプライブラリに追加し、結合されたマスタータイプライブラリを作成します。  
  
 関数は、内部的に参照されるすべてのタイプライブラリを解決して読み込み、パラメーター内のマスター解決済みタイプライブラリへの参照を返し `pptlib` ます。  
  
 関数は、 `LoadTypeLibWithResolver` 通常、 [Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)によって呼び出されます。この関数は、パラメーターに独自の内部 [ITypeLibResolver インターフェイス](itypelibresolver-interface.md) 実装を提供し `pTlbResolver` ます。  
  
 を直接呼び出す場合は `LoadTypeLibWithResolver` 、独自の [ITypeLibResolver インターフェイス](itypelibresolver-interface.md) 実装を指定する必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Tlf .h  
  
 **ライブラリ:** Tlf .lib  
  
 **.NET Framework バージョン:** 3.5、3.0、2.0  
  
## <a name="see-also"></a>関連項目

- [Tlbexp ヘルパー関数](index.md)
- [LoadTypeLibEx 関数](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
