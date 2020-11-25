---
title: CeeSectionRelocType 列挙型
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: f7aa9699e9929608c90020c6b2d66c301fc11955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732711"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列挙型

`reloc` [ICeeGen:: AddSectionReloc](iceegen-addsectionreloc-method.md)の呼び出しで生成された命令の種類に影響する値を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`srRelocAbsolute`|は、セクションに対して相対的なを生成し `reloc` 、reloc セクションには何も送信しません。|  
|`srRelocHighLow`|`reloc`ポインターサイズの位置のを生成します。 これは、プラットフォームに応じて BASED_HIGHLOW または BASED_DIR64 に変換されます。|  
|`srRelocHighAdj`|は、 `reloc` 32 ビットの数値の上位16ビットに対してを生成します。下位16ビットは、reloc テーブルの次の単語に含まれます。|  
|`srRelocMapToken`|トークンマップの再配置を生成し、reloc セクションに何も送信しません。|  
|`srRelocRelative`|値が相対アドレスの修正であることを示します。|  
|`srRelocFilePos`|は、セクションに対して相対的なを生成し `reloc` 、reloc セクションには何も送信しません。 これは、セクションの `reloc` 仮想アドレスではなく、セクションのファイル位置に対する相対パスです。|  
|`srRelocCodeRelative`|コード相対アドレスのフィックスアップを指定します。|  
|`srRelocIA64Imm64`|`reloc`Ia64 命令で64ビットアドレスのを生成 `movl` します。|  
|`srRelocDir64`|`reloc`64 ビットアドレスのを生成します。|  
|`srRelocIA64PcRel25`|`reloc`Ia64 命令で25ビット PC 相対アドレスのを生成 `br.call` します。|  
|`srRelocIA64PcRel64`|`reloc`Ia64 命令で64ビット PC 相対アドレスのを生成 `brl.call` します。|  
|`srRelocAbsoluteTagged`|`reloc`タグ付きポインター値に使用される、30ビットのセクション相対を生成します。|  
|`srRelocSentinel`|この列挙型への追加が内部名配列に反映されるようにするための sentinel 値 `reloc` 。|  
|`srNoBaseReloc`|ベースを生成しないことを指定し `reloc` ます。|  
|`srRelocPtr`|メモリの事前修正の内容が、セクションオフセットではなくポインターであることを示す値。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
- [ICeeGen インターフェイス](iceegen-interface.md)
- [AddSectionReloc メソッド](iceegen-addsectionreloc-method.md)
