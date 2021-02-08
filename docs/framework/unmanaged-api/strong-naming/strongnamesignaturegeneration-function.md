---
description: '詳細情報: StrongNameSignatureGeneration 関数'
title: StrongNameSignatureGeneration 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: 6f5a164e73af743cdd13390c60d00d553e5e0312
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798902"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration 関数

指定したアセンブリに対して厳密な名前の署名が生成されます。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。  
  
 `wszKeyContainer`  
 から公開キーと秘密キーのペアを格納するキーコンテナーの名前。  
  
 `pbKeyBlob`が null の場合、では、 `wszKeyContainer` 暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。 この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。  
  
 `pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。  
  
 キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。 この時点では、他の種類のキーはサポートされていません。  
  
 `pbKeyBlob`  
 から公開/秘密キーのペアへのポインター。 このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。 `pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `wszKeyContainer` 見なされます。  
  
 `cbKeyBlob`  
 からのサイズ (バイト単位) `pbKeyBlob` 。  
  
 `ppbSignatureBlob`  
 入出力共通言語ランタイムが署名を返す場所へのポインター。 `ppbSignatureBlob`が null の場合、ランタイムはによって指定されたファイルに署名を格納し `wszFilePath` ます。  
  
 `ppbSignatureBlob`が null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。 呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用してこの領域を解放する必要があります。  
  
 `pcbSignatureBlob`  
 入出力返されたシグネチャのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>解説  

 `wszFilePath`署名を作成せずに署名のサイズを計算するには、に null を指定します。  
  
 署名は、ファイルに直接格納するか、呼び出し元に返すことができます。  
  
 関数が `StrongNameSignatureGeneration` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureGeneration メソッド](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx メソッド](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
