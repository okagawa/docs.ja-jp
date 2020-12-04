---
title: 定義済みの構成ファイル (コード分析)
description: 定義済みの editorconfig ファイルとルールセットファイルを使用して、特定の種類のコード分析を対象にする方法について説明します。
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2020
ms.locfileid: "96591664"
---
# <a name="predefined-configuration-files"></a>定義済みの構成ファイル

定義済みの EditorConfig ファイルと [ルールセット](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) ファイルを使用して、セキュリティや設計ルールなどのコード品質ルールのカテゴリをすばやく簡単に有効にすることができます。 特定のカテゴリのルールを有効にすることで、対象となる問題と特定の条件を特定できます。 これらの定義済みのファイルにアクセスするには、 [Microsoft CodeAnalysis. netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet アナライザーパッケージをインストールします。

[Microsoft CodeAnalysis. netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) には、次のルールカテゴリの定義済みの editorconfig ファイルとルールセットが含まれています。

- すべてのルール
- データフロー
- 設計
- ドキュメント
- グローバリゼーション
- 相互運用性
- 保守容易性
- 名前を付ける
- パフォーマンス
- FxCop からの移植
- [信頼性]
- セキュリティ
- 使用

これらの規則の各カテゴリには、次のように EditorConfig ファイルまたは規則セットファイルがあります。

- カテゴリ内のすべてのルールを有効にします (他のすべてのルールを無効にします)。
- 各ルールの既定の重要度を使用し、既定の設定で有効にします (他のすべてのルールを無効にします)。

> [!TIP]
> [すべてのルール] カテゴリには、すべてのルールを無効にするための追加の EditorConfig ファイルまたはルールセットファイルがあります。 このファイルを使用すると、プロジェクト内のアナライザーの警告またはエラーがすぐに除去されます。

## <a name="predefined-editorconfig-files"></a>定義済みの EditorConfig ファイル

Microsoft. CodeAnalysis. NetAnalyzers アナライザーパッケージの定義済み EditorConfig ファイルは、NuGet パッケージがインストールされているの *EditorConfig* サブディレクトリにあります。 たとえば、すべてのセキュリティ規則を有効にする EditorConfig ファイルは、 *editorconfig/Securityrules enabled/editorconfig* にあります。

選択した *editorconfig* ファイルをプロジェクトのルートディレクトリにコピーします。

## <a name="predefined-rule-sets"></a>定義済みの規則セット

Microsoft CodeAnalysis. NetAnalyzers アナライザーパッケージの定義済みの規則セットファイルは、NuGet パッケージがインストールされている *のルールセットサブディレクトリ* にあります。 たとえば、すべてのセキュリティ規則を有効にする規則セットファイルは、ルールセット */securityrules enabled にあります。* 1つまたは複数の規則セットをコピーし、プロジェクトが格納されているディレクトリに貼り付けます。

## <a name="see-also"></a>関連項目

- [アナライザーの構成](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [EditorConfig の .NET コードスタイル規則オプション](code-style-rule-options.md)
