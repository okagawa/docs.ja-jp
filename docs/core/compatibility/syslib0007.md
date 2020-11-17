---
title: SYSLIB0007 警告
description: コンパイル時の警告 SYSLIB0007 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 4c0feac1d673e3462a4f2db470825b15cf1b1706
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439943"
---
# <a name="syslib0007-default-implementations-of-cryptography-algorithms-not-supported"></a>SYSLIB0007: 暗号化アルゴリズムの既定の実装はサポートされていません

.NET Framework 内の暗号構成システムは、適切な暗号アジリティに対応しません。また、.NET Core および .NET 5 以降に存在しません。 また、.NET の下位互換性の要件のため、暗号の進歩に対応してフレームワークで特定の暗号化 API を更新することもできません。 その結果、.NET 5.0 以降、次の API は旧型式としてマークさていれます。 これらの API を使用すると、コンパイル時に警告 `SYSLIB0007` が生成されます。

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

## <a name="workarounds"></a>回避策

- 推奨される対応は、現在は古くなった API の呼び出しを、特定のアルゴリズム用のファクトリ メソッド (<xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> など) の呼び出しに置き換えることです。 これにより、インスタンス化されるアルゴリズムを完全に制御できます。

- 古くなった API を使用している .NET Framework アプリによって生成された既存のペイロードとの互換性を維持する必要がある場合は、次の表で推奨されている代わりのものを使用します。 次の表は、.NET Framework の既定のアルゴリズムから .NET 5 以降の同等のアルゴリズムへのマッピングを示したものです。

  | .NET Framework | .NET Core および .NET 5.0 以降で互換性のある代替機能 | 注釈 |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | SHA-1 アルゴリズムは、破られたものと見なされています。 可能であれば、より強力なアルゴリズムを使用することを検討してください。 詳細については、セキュリティ アドバイザーに相談してください。 |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | ほとんどの最新のアプリケーションに対しては、HMACSHA1 アルゴリズムは推奨されません。 可能であれば、より強力なアルゴリズムを使用することを検討してください。 詳細については、セキュリティ アドバイザーに相談してください。 |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | ほとんどの最新のアプリケーションに対しては、HMACSHA1 アルゴリズムは推奨されません。 可能であれば、より強力なアルゴリズムを使用することを検討してください。 詳細については、セキュリティ アドバイザーに相談してください。 |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>関連項目

- [暗号での破壊的変更](cryptography.md#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported)
