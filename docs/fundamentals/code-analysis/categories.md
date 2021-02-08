---
title: コード分析規則のカテゴリ
description: さまざまな .NET コード分析規則のカテゴリについて説明します。
ms.date: 02/05/2021
ms.topic: reference
helpviewer_keywords:
- code analysis, categories
ms.openlocfilehash: 3eaff57a7ea175fbe0895fb7bb8d8d0d8df1365d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804190"
---
# <a name="rule-categories"></a>ルール カテゴリ

各コード分析ルールは、ルールのカテゴリに属しています。 たとえば、設計規則は .NET デザインガイドラインへの準拠をサポートし、セキュリティ規則はセキュリティの欠陥を防ぐのに役立ちます。 ルールの [カテゴリ全体を無効または有効に](configuration-options.md#scope) することができます。 カテゴリごとに [追加のオプションを構成](code-quality-rule-options.md#category-of-rules) することもできます。

次の表に、さまざまなコード分析規則のカテゴリと、各カテゴリの規則へのリンクを示します。

| カテゴリ | 説明 |
| - | - |
| [デザイン規則](quality-rules/design-warnings.md) | 設計規則は、 [.NET Framework 設計ガイドライン](../../standard/design-guidelines/index.md)への準拠をサポートします。 |
| [ドキュメント規則](quality-rules/documentation-warnings.md) | ドキュメントルールでは、外部から参照可能な Api に XML ドキュメントコメントを適切に使用することで、適切にドキュメント化されたライブラリの作成をサポートしています。 |
| [グローバリゼーション規則](quality-rules/globalization-warnings.md) | グローバル化ルールは、国際対応のライブラリとアプリケーションをサポートします。 |
| [移植性と相互運用性の規則](quality-rules/interoperability-warnings.md) | 移植性ルールは、異なるプラットフォーム間での移植性をサポートします。 相互運用性規則は、COM クライアントとの対話をサポートします。 |
| [保守容易性の規則](quality-rules/maintainability-warnings.md) | 保守容易性の規則により、ライブラリとアプリケーションのメンテナンスがサポートされます。 |
| [名前付け規則](quality-rules/naming-warnings.md) | 名前付け規則は、.NET デザインガイドラインの名前付け規則への準拠をサポートします。 |
| [パフォーマンス ルール](quality-rules/performance-warnings.md) | パフォーマンスルールは、高パフォーマンスのライブラリとアプリケーションをサポートします。 |
| [規則の発行](quality-rules/publish-warnings.md) | 発行規則は、単一ファイルアプリケーションをサポートします。 |
| [信頼性の規則](quality-rules/reliability-warnings.md) | 信頼性規則は、正しいメモリやスレッドの使用など、ライブラリとアプリケーションの信頼性をサポートします。 |
| [セキュリティ規則](quality-rules/security-warnings.md) | セキュリティ規則は、より安全なライブラリとアプリケーションをサポートします。 これらの規則は、プログラムのセキュリティの欠陥を防ぐのに役立ちます。 |
| [スタイルルール](style-rules/index.md) | スタイルルールは、コードベースで一貫性のあるコードスタイルをサポートします。 これらの規則は、"IDE" プレフィックスで始まります。 |
| [使い方の規則](quality-rules/usage-warnings.md) | 使用規則は、.NET の適切な使用をサポートします。 |
