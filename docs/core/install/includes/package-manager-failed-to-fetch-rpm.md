---
ms.openlocfilehash: 8c05af045d2d9666b20f36e36c68cc853f906eae
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506855"
---

.NET パッケージのインストール中に、`signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'` のようなエラーが表示されることがあります。 一般に、このエラーは、.NET のパッケージ フィードが新しいバージョンのパッケージでアップグレード中であり、後でもう一度試す必要があることを意味しています。 アップグレード中は、2 時間以上パッケージ フィードを利用できません。 2 時間以上このエラーが継続的に発生する場合は、<https://github.com/dotnet/core/issues> でイシューを報告してください。
