---
title: 基本クラス ライブラリの破壊的変更
description: Core .NET ライブラリにおける破壊的変更の一覧を示します。
ms.date: 07/27/2020
ms.openlocfilehash: 3ecf0e81a3adef097aafb760dc44498d7263f0b6
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050567"
---
# <a name="core-net-libraries-breaking-changes"></a>Core .NET ライブラリの破壊的変更

Core .NET ライブラリでは、.NET Core で使用されるプリミティブとその他の一般的な型が提供されます。

このページでは、次の破壊的変更について説明します。

| 互換性に影響する変更点 | 導入されたバージョン |
| - | :-: |
| [FrameworkDescription の値が .NET Core ではなく .NET になる](#frameworkdescriptions-value-is-net-instead-of-net-core) | 5.0 |
| [単一ファイル発行形式のアセンブリ関連 API 動作の変更](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | 5.0 |
| [Activity.Tags 内のタグの順序が逆になっている](#order-of-tags-in-activitytags-is-reversed) | 5.0 |
| [RC1 でパラメーター名が変更されている](#parameter-names-changed-in-rc1) | 5.0 |
| [OSPlatform 属性の名前変更または削除](#osplatform-attributes-renamed-or-removed) | 5.0 |
| [Thread.Abort は古い形式](#threadabort-is-obsolete) | 5.0 |
| [ConsoleLoggerOptions の古いプロパティ](#obsolete-properties-on-consoleloggeroptions) | 5.0 |
| [ハードウェアに組み込みの IsSupported チェックは、入れ子にされた型によって異なる場合があります](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | 5.0 |
| [参照アセンブリのパラメーター名の変更](#parameter-names-changed-in-reference-assemblies) | 5.0 |
| [Unix 上で ASCII 以外の文字を含む URI パスが正しく解析される](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | 5.0 |
| [Unix での UNC パスの URI 認識](#uri-recognition-of-unc-paths-on-unix) | 5.0 |
| [Environment.OSVersion で正しいオペレーティング システム バージョンが返される](#environmentosversion-returns-the-correct-operating-system-version) | 5.0 |
| [LINQ OrderBy.First{OrDefault} の複雑さが増大](#complexity-of-linq-orderbyfirstordefault-increased) | 5.0 |
| [IntPtr と UIntPtr の IFormattable 実装](#intptr-and-uintptr-implement-iformattable) | 5.0 |
| [PrincipalPermissionAttribute は現在使用されていないエラーです](#principalpermissionattribute-is-obsolete-as-error) | 5.0 |
| [BinaryFormatter シリアル化メソッドが古い形式になり、ASP.NET アプリでは使用不可に](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | 5.0 |
| [UTF-7 コード パスが古い形式に](#utf-7-code-paths-are-obsolete) | 5.0 |
| [Vector\<T> で、サポートされない型に対して常に NotSupportedException がスローされる](#vectort-always-throws-notsupportedexception-for-unsupported-types) | 5.0 |
| [既定の ActivityIdFormat は W3C](#default-activityidformat-is-w3c) | 5.0 |
| [Vector2.Lerp と Vector4.Lerp の動作の変更](#behavior-change-for-vector2lerp-and-vector4lerp) | 5.0 |
| [SSE および SSE2 の CompareGreaterThan メソッドで NaN 入力が正しく処理されるようになった](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | 5.0 |
| [インスタンスが既に存在する場合、CounterSet.CreateCounterSetInstance は InvalidOperationException をスローするようになった](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | 5.0 |
| [Microsoft.DotNet.PlatformAbstractions パッケージの削除](#microsoftdotnetplatformabstractions-package-removed) | 5.0 |
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

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

***

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

***

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

***

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

***

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

***

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

***

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

***

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

***

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

***

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

***

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

***

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

***

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

***

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
