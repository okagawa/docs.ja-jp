---
title: 不要なコード規則
description: コード分析の不要なコード規則について
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "96593857"
---
# <a name="unnecessary-code-rules"></a>不要なコード規則

不要なコード規則は、コードベースのさまざまな部分を特定する必要がなく、リファクタリングまたは削除することができます。 不要なコードが存在する場合は、次の問題の1つを示します。

- 読みやすさ: 読みやすさを不必要に低下させるコード。 たとえば、 [IDE0001](ide0001.md) は不要な型名の修飾にフラグを指定します。
- 保守容易性: リファクタリング後に使用されなくなり、不必要に管理されます。 たとえば、 [IDE0051](ide0051.md) は、使用されていないプライベートフィールド、プロパティ、イベント、およびメソッドにフラグを使用します。
- パフォーマンス: 副作用のない不要な計算によって、不要なパフォーマンスのオーバーヘッドが発生します。 たとえば、 [IDE0059](ide0059.md) は未使用の値の割り当てにフラグを指定し、値を計算する式には副作用がありません。
- 機能: コードの機能の問題。必要なコードを冗長にレンダリングします。 たとえば、 [IDE0060](ide0060.md) は、メソッドが誤って入力パラメーターを無視した場合に、未使用のパラメーターにフラグを指定します。

このセクションの規則では、次の不要なコード規則について考慮します。

- [簡易名 (IDE0001)](ide0001.md)
- [メンバーアクセスの簡略化 (IDE0002)](ide0002.md)
- [不要なキャストの削除 (IDE0004)](ide0004.md)
- [不要なインポートの削除 (IDE0005)](ide0005.md)
- [到達できないコードの削除 (IDE0035)](ide0035.md)
- [未使用のプライベートメンバーの削除 (IDE0051)](ide0051.md)
- [未読のプライベートメンバーの削除 (IDE0052)](ide0052.md)
- [未使用の式の値 (IDE0058) の削除](ide0058.md)
- [不要な値の割り当てを削除する (IDE0059)](ide0059.md)
- [使用されていないパラメーター (IDE0060) を削除します。](ide0060.md)
- [不要な抑制の削除 (IDE0079)](ide0079.md)
- [不要な抑制演算子 (IDE0080)](ide0080.md) -C# のみを削除します。
- [' ByVal ' (IDE0081)](ide0081.md) のみを削除します。 Visual Basic のみです。
- [不要な等値演算子 (IDE0100) の削除](ide0100.md)
- [不要な破棄 (IDE0110)](ide0110.md) -C# のみを削除します。

これらのルールには、ルールの動作を構成するためのオプションがあります。

- [csharp_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [visual_basic_style_unused_value_expression_statement_preference (IDE0058)](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [csharp_style_unused_value_assignment_preference (IDE0059)](ide0059.md#csharp_style_unused_value_assignment_preference)
- [visual_basic_style_unused_value_assignment_preference (IDE0059)](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [dotnet_code_quality_unused_parameters (IDE0060)](ide0060.md#dotnet_code_quality_unused_parameters)
- [dotnet_remove_unnecessary_suppression_exclusions (IDE0079)](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a>関連項目

- [コードスタイルの言語規則](language-rules.md)
- [コードスタイル規則のリファレンス](index.md)
