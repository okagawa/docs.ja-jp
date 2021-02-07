---
description: 詳細については、「ICeeGen インターフェイス」を参照してください。
title: ICeeGen インターフェイス
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: 43e9e0696523346ffbcf0b8823a48ed2c9c359e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706813"
---
# <a name="iceegen-interface"></a>ICeeGen インターフェイス

動的なコード コンパイルのためのメソッドを提供します。  
  
 このインターフェイスは互換性のために残されています。使用しないでください。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AddSectionReloc メソッド](iceegen-addsectionreloc-method.md)|互換性のために残されています。 コードベースに reloc 命令を追加します。|  
|[AllocateMethodBuffer メソッド](iceegen-allocatemethodbuffer-method.md)|互換性のために残されています。 メソッドに対して指定したサイズのバッファーを作成し、メソッドの相対仮想アドレスを取得します。|  
|[ComputePointer メソッド](iceegen-computepointer-method.md)|互換性のために残されています。 指定されたコードセクションのバッファーを決定します。|  
|[EmitString メソッド](iceegen-emitstring-method.md)|互換性のために残されています。 指定した文字列をコードベースに出力します。|  
|[GenerateCeeFile メソッド](iceegen-generateceefile-method.md)|互換性のために残されています。 このに現在読み込まれているコードベースを含むコードベースファイルを生成 `ICeeGen` します。|  
|[GenerateCeeMemoryImage メソッド](iceegen-generateceememoryimage-method.md)|互換性のために残されています。 コードベースのイメージをメモリ内に生成します。|  
|[GetIlSection メソッド](iceegen-getilsection-method.md)|互換性のために残されています。 指定したハンドルによって参照される中間言語コードベースのセクションを取得します。|  
|[GetIMapTokenIface メソッド](iceegen-getimaptokeniface-method.md)|互換性のために残されています。 指定したトークンによって参照されるインターフェイスを取得します。|  
|[GetMethodBuffer メソッド](iceegen-getmethodbuffer-method.md)|互換性のために残されています。 指定した相対仮想アドレスで、メソッドの適切なサイズのバッファーを取得します。|  
|[GetSectionBlock メソッド](iceegen-getsectionblock-method.md)|互換性のために残されています。 コードベースのセクションブロックを取得します。|  
|[GetSectionCreate メソッド](iceegen-getsectioncreate-method.md)|互換性のために残されています。 指定された名前とフラグ値を使用して、コードセクションを生成して取得します。|  
|[GetSectionDataLen メソッド](iceegen-getsectiondatalen-method.md)|互換性のために残されています。 指定したセクションの長さを取得します。|  
|[GetString メソッド](iceegen-getstring-method.md)|互換性のために残されています。 指定した相対仮想アドレスに格納されている文字列を取得します。|  
|[GetStringSection メソッド](iceegen-getstringsection-method.md)|互換性のために残されています。 指定したハンドルによって参照されるコードセクションの文字列表現を取得します。|  
|[TruncateSection メソッド](iceegen-truncatesection-method.md)|互換性のために残されています。 指定したコードセクションを指定した長さだけ切り捨てます。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ インターフェイス](metadata-interfaces.md)
