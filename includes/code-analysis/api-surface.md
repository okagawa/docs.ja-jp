---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700862"
---
### <a name="include-specific-api-surfaces"></a>特定の API サーフェスを含める

ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの *editorconfig* ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
