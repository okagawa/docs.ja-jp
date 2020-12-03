---
title: .NET ライブラリの破壊的変更
description: .NET Core バージョン 1.0-3.0 の Core .NET ライブラリにおける破壊的変更の一覧を示します。
ms.date: 07/27/2020
ms.openlocfilehash: 0f42429e44776fc70bb99ed3bdf346f0d5dbc9eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "96032044"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a>.NET Core 1.0-3.0 の Core .NET ライブラリの破壊的変更

Core .NET ライブラリでは、.NET Core で使用されるプリミティブとその他の一般的な型が提供されます。

このページでは、次の破壊的変更について説明します。

| 互換性に影響する変更点 | 導入されたバージョン |
| - | :-: |
| [バージョンをレポートする API が、ファイル バージョンではなく製品をレポートするようになった](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [カスタム EncoderFallbackBuffer インスタンスが再帰的にフォールバックしない](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [浮動小数点の書式設定と解析の動作の変更](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [浮動小数点の解析操作が失敗したり OverflowException がスローされたりすることがなくなった](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException を別のアセンブリに移動](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [Unicode のガイドラインに従って不適切な形式の UTF-8 バイト シーケンスを置き換える](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute を別のアセンブリに移動](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry による、エントリ サイズに一貫性のないアーカイブ処理の中止](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [FieldInfo.SetValue で、静的な初期化専用フィールドに対する例外がスローされる](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [組み込みの構造体型に追加されたプライベート フィールド](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [UseShellExecute の既定値の変更](#change-in-default-value-of-useshellexecute) | 2.1 |
| [macOS 上の OpenSSL バージョン](#openssl-versions-on-macos) | 2.1 |
| [FileSystemInfo.Attributes によってスローされる UnauthorizedAccessException](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [プロセス破損状態例外の処理がサポートされない](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |
| [UriBuilder のプロパティでは今後、先頭に文字が付加されない](#uribuilder-properties-no-longer-prepend-leading-characters) | 1.0 |
| [開始されなかったプロセスについて Process.StartInfo が InvalidOperationException をスローする](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | 1.0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

**_

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

_**
