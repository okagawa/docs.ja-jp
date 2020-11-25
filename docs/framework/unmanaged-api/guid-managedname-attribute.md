---
title: GUID_ManagedName 属性
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: 0127b6894f1095521f1b24fc8c0424dc7db824b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721050"
---
# <a name="guid_managedname-attribute"></a>GUID_ManagedName 属性

コンポーネントオブジェクトモデル (COM) ライブラリのマネージ名前空間名を指定するカスタムインターフェイス属性を定義します。  
  
## <a name="syntax"></a>構文  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>パラメーター  

 `value`  
 ライブラリのマネージ名前空間の名前。  
  
## <a name="definition"></a>定義  

 `GUID_ManagedName` は、Cor で次のように定義されています。  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>注釈  

 カスタムインターフェイス属性は、タイプライブラリ内のオブジェクトのメタデータを定義します。  
  
 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> 属性からマネージ名を取得するには、またはを使用します。  
  
 詳細については、Visual C++ リファレンスドキュメントの「 [インターフェイス属性](/cpp/windows/attributes/interface-attributes) 」を参照してください。  
  
## <a name="example"></a>例  

 次の例は、属性を使用したライブラリ定義を示して `GUID_ManagedName` います。  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** Cor
