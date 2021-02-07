---
description: '詳細情報: Mailaddressparc Ser クラス'
title: Mailaddressparc Ser クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 5ad534e731e283f5449b3b8cc8e87628716da9b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699767"
---
# <a name="mailaddressparser-class"></a>MailAddressParser クラス

RFC 2822 で説明されているように、電子メールアドレスを解析します。 このクラスは継承できません。

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> このクラスは内部的なものであり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。

## <a name="parseaddress-method"></a>ParseAddress メソッド

指定した文字列から1つの電子メールアドレスを解析します。

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a>パラメーター

`data` <xref:System.String>

解析する電子メールアドレスを含む文字列。

### <a name="return-value"></a>戻り値

<xref:System.Net.Mail.MailAddress>

有効な電子メールアドレス。

### <a name="exceptions"></a>例外

<xref:System.FormatException?displayProperty=nameWithType>

電子メールアドレスが無効です。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (System.dll)
