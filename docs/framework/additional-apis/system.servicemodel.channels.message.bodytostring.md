---
description: '詳細: Message. BodyToString メソッド'
title: Message. BodyToString メソッド (System.servicemodel)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: babcd881d191ff46b98e9999c4ff04166479a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699377"
---
# <a name="messagebodytostring-method"></a>Message. BodyToString メソッド

メソッドを呼び出すことによって、メッセージ本文を文字列に変換し <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> ます。

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>パラメーター

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  メッセージ本文を文字列に変換するために使用されるライター。

## <a name="remarks"></a>解説

> [!WARNING]
> `Message.BodyToString`メソッドは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.ServiceModel.Channels>

**アセンブリ:** System.ServiceModel.dll

**.NET Framework のバージョン:** 3.0 以降で使用できます。
