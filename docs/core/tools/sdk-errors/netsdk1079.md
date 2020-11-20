---
title: NETSDK1079:.NET Core 3.0 以降を対象とする場合、Microsoft.AspNetCore.All パッケージはサポートされません。
description: Microsoft.AspNetCore.App からの移行を解決する方法
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445685"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a>NETSDK1079:.NET Core 3.0 以降を対象とする場合、Microsoft.AspNetCore.All パッケージはサポートされません。

**この記事の対象: ✔️** .NET Core SDK 3.1.100 以降のバージョン

このエラー メッセージは次の状況で表示されることがあります。

- ASP.NET Core プロジェクトの対象を .NET Core 2.2 以前から .NET Core 3.0 以降に変更します。
- プロジェクトで Microsoft.AspNetCore.All パッケージを使用します。

Microsoft.AspNetCore.All の `PackageReference` を削除します。  場合によっては、Microsoft.AspNetCore.All から参照されていたが、ASP.NET Core 共有フレームワークには含まれていないパッケージのパッケージ参照を追加する必要もあります。  そのようなパッケージを以下に示します。[Microsoft.AspNetCore.All から Microsoft.AspNetCore.App への移行](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp)

「[ASP.NET Core 2.2 から 3.0 への移行](/aspnet/core/migration/22-to-30)」も参照してください。
