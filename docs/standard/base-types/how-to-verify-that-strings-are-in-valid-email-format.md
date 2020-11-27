---
title: 文字列が有効な電子メール形式であるかどうかを検証する方法
description: 正規表現を使用して、.NET で文字列が有効な電子メール形式であるかどうかを確認する方法の例について確認します。
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET], examples [Visual Basic]
- email [.NET], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 88ff326e16ede6a422e9403b71905845014c4c25
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982493"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>文字列が有効な電子メール形式であるかどうかを検証する方法

正規表現を使用して文字列の形式が有効な電子メール形式であるかどうかを検証する例を次に示します。

この正規表現は、電子メールとして実際に使用できるものに比べると単純です。 正規表現を使用して電子メールを検証することは、電子メールの構造が正しいことを確認するのに役立ちますが、実際に電子メールが存在することを確認する代わりにはなりません。

✔️ 小さい正規表現を使用して、電子メールの有効な構造を確認します。

✔️ アプリのユーザーが指定したアドレスにテスト メールを送信します。

❌ 電子メールを検証する唯一の方法として、正規表現を使用しないでください。

電子メールの構造が正しいことを検証するために "_完全な_" 正規表現を作成しようとすると、正規表現が非常に複雑になり、デバッグや改善が非常に困難になります。 正規表現では、電子メールが正しく構成されていても、それが存在することを検証できません。 電子メールを検証する最善の方法は、そのアドレスにテスト メールを送信することです。

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>例

次の例では、`IsValidEmail` メソッドを定義します。このメソッドは、文字列に有効なメール アドレスが含まれている場合には `true` を返し、含まれていない場合には `false` を返します。それ以外のアクションは行われません。

電子メール アドレスが有効であることを確認するため、 `IsValidEmail` メソッドは <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> メソッドを呼び出し、 `(@)(.+)$` の正規表現パターンを指定して、電子メール アドレスからドメイン名を切り離します。 3 番目のパラメーターは、一致したテキストを操作また置換するメソッドを表す <xref:System.Text.RegularExpressions.MatchEvaluator> デリゲートです。 正規表現パターンは次のように解釈されます。

| パターン | 説明                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | @ 文字と一致します。 この部分が最初のキャプチャ グループです。                           |
| `(.+)`  | 任意の文字の 1 回以上の出現に一致します。 この部分が 2 番目のキャプチャ グループです。 |
| `$`     | 入力文字列の末尾で照合を終了します。                                             |

ドメイン名は @ 文字と合わせて `DomainMapper` メソッドに渡されます。このメソッドは <xref:System.Globalization.IdnMapping> クラスを使用して、US-ASCII 文字の範囲に含まれない Unicode 文字を Punycode に変換します。 また、このメソッドは、 `invalid` メソッドがドメイン名に無効な文字を検出すると、 `True` フラグを <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> に設定します。 このメソッドは、Punycode ドメイン名の前に @ 記号を付けて、これを `IsValidEmail` メソッドに返します。

> [!TIP]
> 単純な `(@)(.+)$` 正規表現パターンを使用してドメインを正規化し、それが成功または失敗したことを示す値を返すことをお勧めします。 ただし、この記事の例では、正規表現を使用して電子メールを検証する方法について説明します。 電子メールの検証方法に関係なく、必ずそのアドレスにテスト メールを送信して、それが存在することを確認する必要があります。

次に、 `IsValidEmail` メソッドは <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> メソッドを呼び出して、電子メール アドレスが正規表現パターンに準拠するかどうかを確認します。

`IsValidEmail` メソッドは、電子メールの形式がメール アドレスに対して有効かどうかを判断するだけで、電子メールが存在するかどうかの検証は行われません。 また、`IsValidEmail` メソッドでは、トップレベル ドメイン名が [IANA ルート ゾーン データベース](https://www.iana.org/domains/root/db)に掲載されている有効なドメイン名であることの確認は行われません (これには検索操作が必要です)。

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

この例の正規表現パターン `^[^@\s]+@[^@\s]+\.[^@\s]+$` の意味を次の表に示します。 正規表現のコンパイルには、<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> フラグが使用されます。

| Pattern   | 説明                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | 文字列の先頭から照合を開始します。                                              |
| `[^@\s]+` | @ 文字または空白以外の任意の文字の 1 回以上の出現を照合します。 |
| `@`       | @ 文字と一致します。                                                                   |
| `[^@\s]+` | @ 文字または空白以外の任意の文字の 1 回以上の出現を照合します。 |
| `\.`      | 1 つのピリオド文字を照合します。                                                         |
| `[^@\s]+` | @ 文字または空白以外の任意の文字の 1 回以上の出現を照合します。 |
| `$`       | 入力文字列の末尾で照合を終了します。                                                  |

> [!IMPORTANT]
> この正規表現は、有効なメール アドレスのすべての側面をカバーすることを意図したものではありません。 必要に応じて拡張するための例として提供されています。

## <a name="see-also"></a>関連項目

- [.NET の正規表現](regular-expressions.md)
- [メール アドレスの検証はどこまで行う必要があるか](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
