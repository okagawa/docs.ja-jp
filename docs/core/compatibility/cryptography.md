---
title: 暗号での破壊的変更
description: .NET Core で暗号化に関連する破壊的変更の一覧を示します。
ms.date: 04/22/2020
ms.openlocfilehash: b755876624a7709cfe08b5993655e78be9f8e1f2
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888614"
---
# <a name="cryptography-breaking-changes"></a>暗号での破壊的変更

このページでは、次の破壊的変更について説明します。

| 互換性に影響する変更点 | 導入されたバージョン |
| - | :-: |
| [TripleDES.Create で作成されるインスタンスの既定の FeedbackSize 値の変更](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | 5.0 |
| [暗号抽象化の既定の実装のインスタンス化はサポートされていない](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | 5.0 |
| [Linux 上の .NET 用の既定の TLS 暗号スイート](#default-tls-cipher-suites-for-net-on-linux) | 5.0 |
| [Blazor WebAssembly で System.Security.Cryptography API がサポートされない](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | 5.0 |
| [System.Security.Cryptography.Oid は機能的に初期化専用](#systemsecuritycryptographyoid-is-functionally-init-only) | 5.0 |
| [Linux で BEGIN TRUSTED CERTIFICATE 構文がサポートされなくなった](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3.0 |
| [EnvelopedCms で AES-256 暗号化を既定で使用](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [RSAOpenSsl キー生成の最小サイズの増加](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [.NET Core 3.0 では、OpenSSL 1.0.x よりも OpenSSL 1.1.x を優先する](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [CryptoStream.Dispose は書き込み時にのみ最後のブロックを変換する](#cryptostreamdispose-transforms-final-block-only-when-writing) | 3.0 |
| [SignedCms.ComputeSignature のブール型パラメーターの尊重](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

**_

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

_*_

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

_*_

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

_**
