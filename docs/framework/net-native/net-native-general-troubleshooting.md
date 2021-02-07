---
description: '詳細情報: .NET Native の一般的なトラブルシューティング'
title: .NET ネイティブの一般的なトラブルシューティング
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
ms.openlocfilehash: c486b1968036c42ac6d6e565abd9a9f7d795abc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738534"
---
# <a name="net-native-general-troubleshooting"></a>.NET ネイティブの一般的なトラブルシューティング

このトピックでは、.NET Native でアプリを開発するときに発生する可能性がある問題のトラブルシューティング方法について説明します。

- **問題:** ビルド出力ウィンドウが正しく更新されない。

  **解決方法:** ビルド出力ウィンドウは、ビルドが完了するまで更新されません。 ビルドには数分かかる場合があるため、更新が表示されるまでに遅延が発生することがあります。

- **問題:** ARM 用のアプリの製品ビルド時間が長くなった。

  **解決策:** ARM デバイスにアプリをデプロイすると、.NET Native インフラストラクチャが呼び出されます。 このコンパイルは、リフレクションなどの非静的セマンティクスの実行が継続された状態で、多数の最適化を実行します。 さらに、パフォーマンスの最適化のために、.NET Framework でアプリが使用する部分は静的リンクされるため、コンパイルしてネイティブ コードにも含める必要があります。 このため、コンパイルの時間が長くなります。

  ただし、標準的な開発用コンピューター上で、ほとんどのアプリの標準的なコンパイルにかかる時間は 1 分以内です。  通常、標準的な開発用コンピューターでは、.NET Framework のネイティブ イメージを生成するだけで数分かかります。  生成されるコードを改善するための最適化をすべて行い、.NET Framework を含めても、通常、アプリのビルド時間は 1 ～ 2 分です。

  現在も、マルチスレッド コンパイルやその他の最適化を調査して、コンパイルのパフォーマンスを改善する取り組みが続いています。

- **問題:** アプリが .NET Native を使用してコンパイルされたかどうかはわかりません。

  **解決策:** .NET Native コンパイラが呼び出されると、ビルド時間が長くなり、タスクマネージャーによって ILC.exe や nutc_driver.exe などのさまざまな .NET Native コンポーネントプロセスが表示されます。

  .NET Native でプロジェクトを正常にビルドすると、obj \\ *config* \  *arch* \\ *projectname*. ilc\out の下に出力が表示されます。 最終的なネイティブパッケージコンテンツは、bin \\ *arch* \\ *config*\appx にあります。 \\ \\ アプリをデプロイしている場合、最終的なネイティブパッケージコンテンツは \bin アーキテクチャ *config*/AppX の下にあります。

- **問題:** .NET Native を使用してアプリをコンパイルすると、.NET Native を使用せずにコンパイルしたときにはスローされないランタイム例外 (通常は [MissingMetadataException](missingmetadataexception-class-net-native.md) または [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外) がスローされる。

  **解決方法:** これらの例外は、リフレクションを介して使用できるはずのメタデータまたは実装コードが .NET Native では提供されなかったためにスローされます  (詳細については、「 [.NET Native とコンパイル](net-native-and-compilation.md)」を参照してください)。この例外を回避するには、ランタイム [ディレクティブ (rd.xml) ファイル](runtime-directives-rd-xml-configuration-file-reference.md) にエントリを追加して、.NET Native ツールチェーンが実行時にメタデータまたは実装コードを使用できるようにする必要があります。 次の 2 つのトラブルシューティング ツールを使用して、ランタイム ディレクティブ ファイルに追加する必要があるエントリを生成できます。

  - [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。

  - [MissingMetadataException トラブルシューティング ツール](https://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。

  詳細については、「[リフレクションおよび .NET ネイティブ](reflection-and-net-native.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [Windows ストア アプリの .NET ネイティブへの移行](migrating-your-windows-store-app-to-net-native.md)
