---
title: StrongNameGetPublicKey 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: c97cc0c1d4c022583d0823abeff998e2ed5f719e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710975"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey 関数

秘密/公開キーの組から公開キーが取得されます。 キーペアは、暗号化サービスプロバイダー (CSP) 内のキーコンテナー名として、またはバイトの未加工コレクションとして指定できます。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `szKeyContainer`  
 から公開キーと秘密キーのペアを格納するキーコンテナーの名前。 `pbKeyBlob`が null の場合、は `szKeyContainer` CSP 内の有効なコンテナーを指定する必要があります。 この場合、は、 `StrongNameGetPublicKey` コンテナーに格納されているキーペアから公開キーを抽出します。  
  
 `pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。  
  
 キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。 この時点では、他の種類のキーはサポートされていません。  
  
 `pbKeyBlob`  
 から公開/秘密キーのペアへのポインター。 このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。 `pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `szKeyContainer` 見なされます。  
  
 `cbKeyBlob`  
 からのサイズ (バイト単位) `pbKeyBlob` 。  
  
 `ppbPublicKeyBlob`  
 入出力返された公開キー BLOB。 パラメーターは、 `ppbPublicKeyBlob` 共通言語ランタイムによって割り当てられ、呼び出し元に返されます。 呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用してメモリを解放する必要があります。  
  
 `pcbPublicKeyBlob`  
 入出力返される公開キー BLOB のサイズ。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>注釈  

 公開キーは [Publickeyblob](publickeyblob-structure.md) 構造に含まれています。  
  
 関数が `StrongNameGetPublicKey` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetPublicKey メソッド](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey メソッド](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob 構造体](publickeyblob-structure.md)
