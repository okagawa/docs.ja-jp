---
title: .NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する
description: .NET を使用して IoT デバイスとシナリオ用のアプリケーションを作成する方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: c3d05ec5b05780f91404c3c27e91bcd602b0faeb
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594030"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a>.NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する

.NET は、さまざまなプラットフォームとアーキテクチャで動作します。 Raspberry Pi や Hummingboard など、一般的なモノのインターネット (IoT) ボードがサポートされています。 IoT アプリは通常、センサー、アナログ-デジタルコンバーター、および LCD デバイスといった特殊なハードウェアと対話します。 .NET IoT ライブラリを使用すると、これらのシナリオを実現できます。

## <a name="video-overview"></a>ビデオの概要

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a>ライブラリ

.NET IoT ライブラリは、次の2つの NuGet パッケージで構成されています。

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span>
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span>

### <a name="systemdevicegpio"></a>System.Device.Gpio

`System.Device.Gpio` では、デバイスを制御するために低レベルのハードウェア pin と対話するためのさまざまなプロトコルがサポートされています。 次に例を示します。

- 汎用入出力 (GPIO)
- Inter-Integrated 回線 (I2C)
- シリアル周辺機器インターフェイス (SPI)
- パルス幅の変調 (PWM)
- シリアル ポート

### <a name="iotdevicebindings"></a>Iot.Device.Bindings

`Iot.Device.Bindings`パッケージ:

* System.string [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md)を <span class="docon docon-navigate-external x-hidden-focus"></span> ラップすることによってアプリ開発を効率化するためのデバイスのバインドが含まれています。
* コミュニティでサポートされており、追加のバインドが継続的に追加されます。

一般的に使用されるデバイスのバインドは次のとおりです。

- [文字 lcd-lcd 文字ディスプレイ](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [SN74HC595-8 ビットシフトレジスタ](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [Max7219-LED マトリックスドライバー](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [RGBLedMatrix-RGB LED マトリックス](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)<span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

`System.Device.Gpio` は、ARM/ARM64 と Windows 10 IoT Core をサポートするほとんどのバージョンの Linux でサポートされています。

> [!TIP]
> Raspberry Pi では、 [Raspberry PI OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> (旧称 Raspbian) を使用することをお勧めします。  

## <a name="supported-hardware-platforms"></a>サポートされているハードウェアプラットフォーム

`System.Device.Gpio` は、ほとんどのシングルボードプラットフォームと互換性があります。 推奨されるプラットフォームは Raspberry Pi (2 以上) と Hummingboard です。 互換性があるとわかっているその他のプラットフォームは、BeagleBoard と OID ID です。

PC プラットフォームは、USB から SPI/I2C ブリッジを使用することによってサポートされます。

> [!IMPORTANT]
> .NET は、Raspberry Pi 2 より前の Raspberry Pi 0 および Raspberry Pi デバイスを含む、ARMv6 アーキテクチャデバイスではサポートされていません。

## <a name="resources"></a>リソース

- [Github の .Net IoT ライブラリ](https://github.com/dotnet/iot)<span class="docon docon-navigate-external x-hidden-focus"></span>
