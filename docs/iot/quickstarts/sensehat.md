---
title: クイックスタート-.NET を使用して Raspberry Pi Sense HAT を駆動する
description: Raspberry Pi のアドオンボードである Sense HAT を使用して、5分で .NET IoT ライブラリを使い始めることができます。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 09e0c46a08e08a2021a9dffe214d3d62d6fb8ec5
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594025"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a>クイックスタート-.NET を使用して Raspberry Pi Sense HAT を駆動する

Raspberry Pi [SENSE HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> は、Raspberry pi のアドオンボードです。 Sense HAT には、8×8の RGB LED 行列 (5 ボタンのジョイスティック) が搭載されており、次のセンサーが含まれています。

- ジャイロスコープ
- 加速度計
- 磁力計
- 気温
- 気圧の圧力
- 湿度

このクイックスタートでは、.NET を使用して Sense HAT からセンサー値を取得し、ジョイスティック入力に応答して、LED マトリックスを駆動しています。

## <a name="prerequisites"></a>前提条件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Sense HAT

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a>クイックスタートを実行する

Sense HAT を Raspberry Pi に接続します。 Raspberry Pi (ローカルまたはリモート) の Bash プロンプトから、次のコマンドを実行します。

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

コマンドは、スクリプトをダウンロードして実行します。 スクリプト:

- .NET SDK をインストールします。
- Sense HAT クイックスタートプロジェクトを含む GitHub リポジトリを複製します。
- プロジェクトをビルドします。
- プロジェクトを実行します。

センサーデータが表示されていることを確認します。 LED マトリックスには、青のフィールドに黄色のピクセルが表示されます。 ジョイスティックを任意の方向に保持すると、その方向に黄色のピクセルが移動します。 [Center ジョイスティック] ボタンをクリックすると、背景が青から赤に切り替わります。

## <a name="get-the-source-code"></a>ソース コードを入手する

このクイックスタートのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart)ます。 <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [General Purpose 入力/出力を使用して LED を点滅させる方法について説明します](../tutorials/blink-led.md)
