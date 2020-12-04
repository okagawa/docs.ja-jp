---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594019"
---
[SFTP クライアントを使用して](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md)、開発用コンピューターの発行場所から Raspberry Pi 上の新しいフォルダーにファイルをコピーします。

たとえば、コマンドを使用し `scp` て開発用コンピューターから Raspberry Pi にファイルをコピーするには、コマンドプロンプトを開き、次のコマンドを実行します。

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

この場合、

- `-r`オプションは、 `scp` ファイルを再帰的にコピーするように指示します。
- *また* は、前の手順で発行したフォルダーです。
- `pi@raspberypi` は、という形式のユーザー名とホスト名です `<username>@<hostname>` 。
- */home/pi/deployment-location/* は、Raspberry pi 上の新しいフォルダーです。

> [!TIP]
> 最新バージョンの Windows には、インストール済みのが含まれている OpenSSH があり `scp` ます。
