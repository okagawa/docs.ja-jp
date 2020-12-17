---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009055"
---
### <a name="xml-parsing-changes"></a>XML 解析の変更

| 名前    | 値   |
|:--------|:--------|
| スコープ   | マイナー   |
| バージョン | 4.5.2   |
| 種類    | ランタイム |

#### <a name="details"></a>詳細

セキュリティ上の理由から、次の変更が XML 解析 API に導入されました。

- <xref:System.Xml.XmlReaderSettings> が初期化されるときに、<xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> は 1,000 万に設定されます。
- 既定では、<xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> は `null` に設定されています。

> [!NOTE]
> <xref:System.Xml.XmlReaderSettings> はすべての XML パーサーによって使用されるため、この変更は <xref:System.Xml.XmlReader> のケースでは役に立ちますが、他のシナリオにも影響します。

#### <a name="suggestion"></a>提案される解決策

以前の動作に戻すには、レジストリで値を設定します。 `EnableLegacyXmlSettings` という名前のダブルワード値を `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` レジストリ キーに追加し、その値を `1` に設定します。 代わりに、HKEY_CURRENT_USER ハイブでレジストリ値を追加することもできます。

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

また、直接的または間接的に <xref:System.Xml.XmlResolver> に依存するすべての XML API が影響を受けます。

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
