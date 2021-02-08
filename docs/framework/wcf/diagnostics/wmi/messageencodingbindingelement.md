---
description: '詳細情報: MessageEncodingBindingElement'
title: MessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 7f750742-b96b-498f-bf5e-05933a1a5961
ms.openlocfilehash: 7c6660245165acb67db8af9043d956e8a82d9a03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803192"
---
# <a name="messageencodingbindingelement"></a>MessageEncodingBindingElement

MessageEncodingBindingElement

## <a name="syntax"></a>構文

```csharp
class MessageEncodingBindingElement : BindingElement
{
    string MessageVersion;
};
```

## <a name="methods"></a>メソッド

MessageEncodingBindingElement クラスは、メソッドを一切定義しません。

## <a name="properties"></a>プロパティ

MessageEncodingBindingElement クラスには、次のプロパティがあります。

### <a name="messageversion"></a>MessageVersion

データ型: 文字列

アクセスの種類: 読み取り専用

バインディングを使用して送信されたメッセージの SOAP バージョン。

## <a name="requirements"></a>要件

|MOF|Servicemodel.mof にて宣言済み。|
|---------|-----------------------------------|
|名前空間|root\ServiceModel で定義|

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
