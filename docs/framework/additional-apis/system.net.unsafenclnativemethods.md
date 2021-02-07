---
description: '詳細情報: UnsafeNclNativeMethods クラス'
title: UnsafeNclNativeMethods クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa1084efddae0ba5cbfc9a949dcd94d2c64f3272
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699494"
---
# <a name="unsafenclnativemethods-class"></a>UnsafeNclNativeMethods クラス

Unsafe ネイティブネットワークメソッドをインポートするクラスが含まれています。 このクラスは継承できません。

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> このクラスは内部的なものであり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。

## <a name="nativepki-class"></a>Pipki クラス

crypt32.dll からインポートされたメソッドを格納します。 これらのメソッドは、ハイパーテキスト転送プロトコルセキュア (HTTPS) を使用する場合に証明書を処理します。 このクラスは継承できません。

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a>Pipki. FindClientCertificates メソッド

サーバーに送信できる使用可能なクライアント証明書を検出します。

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a>戻り値

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

使用可能なクライアント証明書のコレクション。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)
