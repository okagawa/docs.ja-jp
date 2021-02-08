---
description: 詳細については、「PeerCustomResolverBindingElement」を参照してください。
title: PeerCustomResolverBindingElement
ms.date: 03/30/2017
ms.assetid: 9ccc2770-a20e-4dff-9970-f56ad8aec2b5
ms.openlocfilehash: f4277c04818eec69c1041eee30282d3111421eaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803049"
---
# <a name="peercustomresolverbindingelement"></a>PeerCustomResolverBindingElement

PeerCustomResolverBindingElement

## <a name="syntax"></a>構文

```csharp
class PeerCustomResolverBindingElement : PeerResolverBindingElement
{
    string Address;
    string Binding;
};
```

## <a name="methods"></a>メソッド

PeerCustomResolverBindingElement クラスで定義されているメソッドはありません。

## <a name="properties"></a>プロパティ

 PeerCustomResolverBindingElement クラスには、次のプロパティがあります。

### <a name="address"></a>Address

データ型: 文字列

アクセスの種類: 読み取り専用

ピア カスタム リゾルバーのアドレスです。

### <a name="binding"></a>バインド

データ型: 文字列

アクセスの種類: 読み取り専用

バインドの構成名。

## <a name="requirements"></a>要件

|MOF|Servicemodel.mof にて宣言済み。|
|---------|-----------------------------------|
|名前空間|root\ServiceModel で定義|

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement>
