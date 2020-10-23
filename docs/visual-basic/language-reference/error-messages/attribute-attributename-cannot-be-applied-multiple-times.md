---
title: 属性 '<attributename>' を複数回適用することはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162662"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a>BC30663:属性 '\<attributename>' を複数回適用することはできません。

属性は、1 回のみ適用できます。 `AttributeUsage` 属性は、属性を複数回適用できるかどうかを決定します。

 **エラー ID:** BC30663

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 属性が 1 回だけ適用されていることを確認してください。

2. 開発したカスタム属性を使用する場合は、次の例のように、複数の属性の使用を許可するように `AttributeUsage` 属性を変更することを検討してください。

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a>関連項目

- <xref:System.AttributeUsageAttribute>
- [カスタム属性の作成](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
