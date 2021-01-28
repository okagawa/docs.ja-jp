---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957937"
---
## <a name="suppress-a-warning"></a>警告の非表示

規則違反を抑制するには、特定の規則 ID の重大度オプションを `none` EditorConfig ファイルでに設定します。 例:

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio には、コード分析規則からの警告を抑制するための追加の方法が用意されています。 詳細については、「 [違反の抑制](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations)」を参照してください。

規則の重大度の詳細については、「 [規則の重要度の構成](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level)」を参照してください。
