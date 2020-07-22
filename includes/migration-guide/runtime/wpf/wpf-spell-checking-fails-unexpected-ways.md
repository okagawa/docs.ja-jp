---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621810"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF スペル チェックが予期しない方法で失敗する

#### <a name="details"></a>説明

これには、次の WPF スペル チェックのいくつかの問題が含まれます。<ul><li>WPF スペル チェックで <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName> がスローされる場合がある。</li><li>"別のユーザーとして実行" を使用してアプリケーションが起動された場合、WPF スペル チェックが <xref:System.UnauthorizedAccessException> で失敗する。</li><li>WPF スペル チェックで、ドイツ語の "Hausnummer" などの複合語のスペル ミスが正しく識別されない。</li></ul>

#### <a name="suggestion"></a>提案される解決策

問題 1 - これは .NET Framework 4.6.2 で修正されました。問題 2 - "別のユーザーとして実行" を使用してアプリケーションが起動された場合、WPF スペル チェックがサポートされなくなりました。 .NET Framework 4.6.2 以降では、このように起動されたアプリケーションが予期せずクラッシュしなくなります。代わりに、スペル チェックが自動的に無効になります。 問題 3 - これは .NET Framework 4.6.2 で修正されました。

| 名前    | [値]       |
|:--------|:------------|
| スコープ   |エッジ|
|バージョン|4.6.1|
|種類|ランタイム|
