---
description: '詳細情報: 依存関係プロパティ'
title: 依存関係プロパティ
ms.date: 10/22/2008
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 78b141d6e8d1bb6bd5cf050a89aa67705111bae3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642306"
---
# <a name="dependency-properties"></a>依存関係プロパティ

依存関係プロパティ (DP) は、その値が、たとえば型変数 (フィールド) に格納されるのではなく、プロパティ ストアに格納される通常のプロパティです。

 添付依存関係プロパティは、オブジェクトとそのコンテナーの間の関係 (たとえば、`Panel` コンテナー上の `Button` オブジェクトの位置) を記述する "プロパティ" を表す静的な Get メソッドと Set メソッドとしてモデル化された、依存関係プロパティの一種です。

 ✔️ スタイル設定、トリガー、データ バインディング、アニメーション、動的リソース、継承などの WPF の機能をサポートするためにプロパティが必要な場合は、依存関係プロパティを提供します。

## <a name="dependency-property-design"></a>依存関係プロパティの設計

 ✔️ 依存関係プロパティを実装するときは、<xref:System.Windows.DependencyObject> またはそのいずれかのサブタイプを継承します。 この型を使用すると、プロパティ ストアの非常に効率的な実装が提供され、WPF のデータ バインディングが自動的にサポートされます。

 ✔️ 依存関係プロパティごとに、通常の CLR プロパティと、<xref:System.Windows.DependencyProperty?displayProperty=nameWithType> のインスタンスを格納するパブリックの静的読み取り専用フィールドを提供します。

 ✔️ インスタンス メソッド <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> と <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> を呼び出すことにより、依存関係プロパティを実装します。

 ✔️ 依存関係プロパティの静的フィールドの名前は、プロパティの名前に "Property" というサフィックスを付けたものにします。

 ❌ 依存関係プロパティの既定値を、コードで明示的に設定しないでください。代わりに、メタデータで設定します。

 プロパティの既定値を明示的に設定した場合、スタイル設定などの一部の暗黙的な方法によって、そのプロパティを設定できなくなることがあります。

 ❌ 静的フィールドにアクセスするための標準コード以外のコードを、プロパティ アクセサーに配置しないでください。

 スタイル設定などの暗黙的な方法によってプロパティが設定された場合、そのコードは実行されません。これは、スタイルによって静的フィールドが直接使用されるためです。

 ❌ 依存関係プロパティを使用して、セキュリティ保護されたデータを格納しないでください。 プライベートな依存関係プロパティであっても、パブリックにアクセスできます。

## <a name="attached-dependency-property-design"></a>添付依存関係プロパティの設計

 前のセクションで説明した依存関係プロパティは、宣言する型の組み込みプロパティを表します。たとえば、`Text` プロパティは、それを宣言している `TextButton` のプロパティです。 添付依存関係プロパティは、特別な種類の依存関係プロパティです。

 添付プロパティの典型的な例は、<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> プロパティです。 このプロパティは、(Grid ではなく) Button の列位置を表しますが、Button が Grid に含まれている場合にのみ関連があるので、Grid によって Button に "添付" されています。

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 添付プロパティの定義は、通常の依存関係プロパティとほとんど同じように見えますが、アクセサーが静的な Get と Set メソッドによって表される点が異なります。

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a>依存関係プロパティの検証

 通常、プロパティによって検証と呼ばれるものが実装されています。 プロパティの値を変更しようとすると、検証ロジックが実行されます。

 残念ながら、依存関係プロパティのアクセサーに任意の検証コードを含めることはできません。 代わりに、プロパティを登録するときに、依存関係プロパティの検証ロジックを指定する必要があります。

 ❌ 依存関係プロパティの検証ロジックを、プロパティのアクセサーに配置しないでください。 代わりに、検証コールバックを `DependencyProperty.Register` メソッドに渡します。

## <a name="dependency-property-change-notifications"></a>依存関係プロパティの変更通知

 ❌ 変更通知のロジックを依存関係プロパティのアクセサーに実装しないでください。 依存関係プロパティには組み込みの変更通知機能があり、変更通知コールバックを <xref:System.Windows.PropertyMetadata> に提供することによって、それを使用する必要があります。

## <a name="dependency-property-value-coercion"></a>依存関係プロパティの値の強制型変換

 プロパティの強制型変換は、プロパティのセッターに渡された値が、プロパティ ストアが実際に変更される前に、セッターによって変更されるときに行われます。

 ❌ 依存関係プロパティのアクセサーに、強制型変換のロジックを実装しないでください。

 依存関係プロパティには組み込みの強制型変換機能があり、強制型変換コールバックを `PropertyMetadata` に渡すことによって使用できます。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [共通デザイン パターン](common-design-patterns.md)
