---
title: IMetaDataEmit::DefineMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: fbf6ce8c8c9628b08872058a794fb0e005764ab1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501301"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod メソッド
指定したシグネチャを使用してメソッドまたはグローバル関数の定義を作成し、そのメソッド定義に対するトークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 から`mdTypedef`メソッドの親クラスまたは親インターフェイスのトークン。 `td` `mdTokenNil` グローバル関数を定義する場合は、に設定します。  
  
 `szName`  
 からUnicode のメンバー名。  
  
 `dwMethodFlags`  
 からメソッドまたはグローバル関数の属性を指定する[CorMethodAttr](cormethodattr-enumeration.md)列挙体の値。  
  
 `pvSigBlob`  
 からメソッドシグネチャ。 署名は、指定されたとおりに永続化されます。 任意のパラメーターの追加情報を指定する必要がある場合は、 [IMetaDataEmit:: SetParamProps](imetadataemit-setparamprops-method.md)メソッドを使用します。  
  
 `cbSigBlob`  
 からのバイト数 `pvSigBlob` 。  
  
 `ulCodeRVA`  
 からコードのアドレス。  
  
 `dwImplFlags`  
 からメソッドの実装機能を指定する[Cormethodimpl](cormethodimpl-enumeration.md)列挙体の値。  
  
 `pmd`  
 入出力メンバートークン。  
  
## <a name="remarks"></a>解説  
 メタデータ API は、呼び出し元が指定された外側のクラスまたはインターフェイスに対してメソッドを出力するのと同じ順序でメソッドを永続化することを保証します。これは、パラメーターで指定し `td` ます。  
  
 および特定のパラメーター設定の使用に関する追加情報 `DefineMethod` を以下に示します。  
  
## <a name="slots-in-the-v-table"></a>V テーブルのスロット  
 ランタイムは、メソッド定義を使用して、v テーブルスロットを設定します。 COM インターフェイスのレイアウトでパリティを保持するなど、1つ以上のスロットをスキップする必要がある場合は、v テーブルのスロットまたはスロットを取得するためにダミーメソッドが定義されています。を `dwMethodFlags` `mdRTSpecialName` [CorMethodAttr](cormethodattr-enumeration.md)列挙の値に設定し、名前をとして指定します。  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 ここで、 *SequenceNumber*はメソッドのシーケンス番号、 *CountOfSlots*は v テーブルでスキップするスロットの数です。 *CountOfSlots*を省略すると、1が想定されます。 これらのダミーメソッドは、マネージコードまたはアンマネージコードから呼び出すことはできません。また、マネージコードまたはアンマネージコードから呼び出しを試みると、例外が生成されます。 その唯一の目的は、ランタイムが COM 統合用に生成する v テーブルの領域を占有することです。  
  
## <a name="duplicate-methods"></a>重複するメソッド  
 重複するメソッドは定義しないでください。 つまり、、、およびの各 `DefineMethod` パラメーターで、重複する値のセットを指定してを呼び出すことはできません `td` `wzName` `pvSig` 。 (これら3つのパラメーターを組み合わせて、メソッドを一意に定義します)。 ただし、メソッドの定義の1つに対して、パラメーターにビットを設定するという3つの方法を使用できます `mdPrivateScope` `dwMethodFlags` 。 (ビットは、 `mdPrivateScope` コンパイラがこのメソッド定義への参照を生成しないことを意味します)。  
  
## <a name="method-implementation-information"></a>メソッドの実装情報  
 メソッドの実装に関する情報は、多くの場合、メソッドが宣言されているときには認識されません。 したがって、 `ulCodeRVA` を呼び出すときに、パラメーターとパラメーターに値を渡す必要はありません `dwImplFlags` `DefineMethod` 。 値は、必要に応じて、後で[IMetaDataEmit:: SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md)または[IMetaDataEmit:: SetRVA](imetadataemit-setrva-method.md)を使用して指定できます。  
  
 プラットフォーム呼び出し (PInvoke) や COM 相互運用のシナリオなど、状況によっては、メソッド本体が提供されず、 `ulCodeRVA` 0 に設定する必要があります。 このような状況では、ランタイムによって実装が特定されるため、メソッドを abstract としてタグ付けすることはできません。  
  
## <a name="defining-a-method-for-pinvoke"></a>PInvoke のメソッドの定義  
 PInvoke を通じて呼び出される各アンマネージ関数に対して、対象のアンマネージ関数を表すマネージメソッドを定義する必要があります。 マネージメソッドを定義するには、 `DefineMethod` PInvoke の使用方法に応じて、特定の値に設定されているいくつかのパラメーターと共にを使用します。  
  
- True PInvoke-アンマネージ DLL に存在する外部アンマネージメソッドの呼び出しが含まれます。  
  
- ローカル PInvoke-現在のマネージモジュールに埋め込まれているネイティブアンマネージメソッドの呼び出しが含まれます。  
  
 パラメーターの設定を次の表に示します。  
  
|パラメーター|True PInvoke の値|ローカル PInvoke の値|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||`mdStatic` `mdSynchronized` を設定します。とをクリアし `mdAbstract` ます。|  
|`pvSigBlob`|有効なマネージ型であるパラメーターを持つ有効な共通言語ランタイム (CLR) メソッドシグネチャ。|有効なマネージ型であるパラメーターを含む有効な CLR メソッドシグネチャ。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|`miCil` と `miManaged` を設定します。|`miNative` と `miUnmanaged` を設定します。|  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** Mscoree.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](imetadataemit2-interface.md)
