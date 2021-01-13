---
title: Azure SDK for .NET を使用する場合のプロキシ サーバーの構成
description: Azure SDK for .NET のプロキシを定義するには、HTTP[S]_PROXY 環境変数を使用します
ms.date: 12/10/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.openlocfilehash: 64d525f8a6c277a5ac383dfded828f2fd3cfd744
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700919"
---
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a>Azure SDK for .NET を使用する場合のプロキシ サーバーの構成

組織でインターネット リソースにアクセスするためにプロキシ サーバーを使用する必要がある場合は、プロキシ サーバー情報を使用して Azure SDK for .NET を使用するように環境変数を設定する必要があります。  

## <a name="configuration-using-environment-variables"></a>環境変数を使用した構成

プロキシ サーバーで HTTP と HTTPS のどちらを使用するかに応じて、環境変数 `HTTP_PROXY` または `HTTPS_PROXY` をそれぞれ設定します。 プロキシ サーバーの URL の形式は `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` で、`username:password` の組み合わせは省略可能です。 プロキシ サーバーの IP アドレスまたはホスト名、ポート、および資格情報を取得するには、ネットワーク管理者に問い合わせてください。

次の例は、コマンド シェル (Windows) と bash (Linux/Mac) のそれぞれの環境で適切な環境変数を設定する方法を示しています。  適切な環境変数を設定すると、Azure SDK for .NET で実行時にプロキシ サーバーが使用されるようになります。

### <a name="cmd"></a>[cmd](#tab/cmd)

```cmd
rem Non-authenticated HTTP server:
set HTTP_PROXY=http://10.10.1.10:1180

rem Authenticated HTTP server:
set HTTP_PROXY=http://username:password@10.10.1.10:1180

rem Non-authenticated HTTPS server:
set HTTPS_PROXY=http://10.10.1.10:1180

rem Authenticated HTTPS server:
set HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

### <a name="bash"></a>[bash](#tab/bash)

```bash
# Non-authenticated HTTP server:
HTTP_PROXY=http://10.10.1.10:1180

# Authenticated HTTP server:
HTTP_PROXY=http://username:password@10.10.1.10:1180

# Non-authenticated HTTPS server:
HTTPS_PROXY=http://10.10.1.10:1180

# Authenticated HTTPS server:
HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

---
