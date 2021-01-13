---
ms.openlocfilehash: 53840ddd59ae3463bae2930fd0151ab2cd2d65cb
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593327"
---
### <a name="design-time-builds-only-return-top-level-package-references"></a>デザイン時のビルドから最上位のパッケージ参照のみが返される

.NET Core SDK 3.1.400 以降では、`RunResolvePackageDependencies` ターゲットから最上位のパッケージ参照のみが返されます。

#### <a name="version-introduced"></a>導入されたバージョン

.NET Core SDK 3.1.400

#### <a name="change-description"></a>変更の説明

以前のバージョンの .NET Core SDK では、`RunResolvePackageDependencies` ターゲットにより、NuGet アセット ファイルの情報を含む次の MSBuild 項目が作成されていました。

- `PackageDefinitions`
- `PackageDependencies`
- `TargetDefinitions`
- `FileDefinitions`
- `FileDependencies`

このデータは、ソリューション エクスプローラーで [依存関係] ノードに設定するために、Visual Studio によって使用されます。 ただし、大量のデータになる場合があります。[依存関係] ノードが展開されていない限り、このデータは必要ありません。

.NET Core SDK バージョン 3.1.400 以降、これらの項目のほとんどは既定で生成されません。 型 `Package` の項目のみが返されます。 [依存関係] ノード設定するために、Visual Studio に項目が必要な場合、アセット ファイルから情報が直接読み取られます。

#### <a name="reason-for-change"></a>変更理由

この変更は、Visual Studio 内のソリューション読み込みのパフォーマンスを向上させるために導入されました。 以前はすべてのパッケージ参照が読み込まれ、ほとんどのユーザーが表示することのない多数の参照が読み込まれていました。

#### <a name="recommended-action"></a>推奨アクション

これらの項目が作成されることに依存する MSBuild ロジックがある場合は、プロジェクト ファイルで `EmitLegacyAssetsFileItems` プロパティを `true` に設定します。 この設定にすることで、すべての項目が作成される以前の動作が有効になります。

#### <a name="category"></a>カテゴリ

MSBuild

#### <a name="affected-apis"></a>影響を受ける API

N/A
