---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721633"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo.SetValue で、静的な初期化専用フィールドに対する例外がスローされる

.NET Core 3.0 以降、<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> を呼び出して静的な <xref:System.Reflection.FieldAttributes.InitOnly> フィールドに値を設定しようとすると、例外がスローされます。

#### <a name="change-description"></a>変更の説明

.NET Framework と、3.0 より前のバージョンの .NET Core では、定数である静的フィールドの初期化 ([C# では読み取り専用に](~/docs/csharp/language-reference/keywords/readonly.md)) した後、<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> を呼び出すことで値を設定できました。 ただし、この方法でこのようなフィールドを設定すると、ターゲット フレームワークと最適化の設定に基づく動作を予測できなくなります。

.NET Core 3.0 以降のバージョンでは、静的な <xref:System.Reflection.FieldAttributes.InitOnly> フィールドに対して <xref:System.Reflection.FieldInfo.SetValue%2A> を呼び出すと、<xref:System.FieldAccessException?displayProperty=nameWithType> 例外がスローされます。

> [!TIP]
> <xref:System.Reflection.FieldAttributes.InitOnly> フィールドは、その宣言時またはそれを含んでいるクラスのコンストラクター内にのみ設定可能なフィールドです。 つまり、それは初期化された後は定数になります。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="recommended-action"></a>推奨アクション

静的コンストラクター内の静的な <xref:System.Reflection.FieldAttributes.InitOnly> フィールドを初期化します。 これは、動的な型と非動的な型の両方に適用されます。

または、フィールドから <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> 属性を削除した後、<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> を呼び出すこともできます。

#### <a name="category"></a>カテゴリ

Core .NET ライブラリ

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
