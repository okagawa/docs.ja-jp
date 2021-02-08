---
description: 詳細については、「MsmqTransportBindingElement」を参照してください。
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 4b6f363d979972c6ff0a2a378906feeece2ff6b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803153"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement

MsmqTransportBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>メソッド  

 MsmqTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 MsmqTransportBindingElement クラスには、次のプロパティがあります。  
  
### <a name="maxpoolsize"></a>MaxPoolSize  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 内部 MSMQ メッセージ オブジェクトを含むプールの最大サイズです。  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 このバインディングが使用するキューに置かれた通信チャネルのトランスポートを示す列挙値です。  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 キューのアドレスを Active Directory を使用して変換する必要があるかどうかを示すブール値を返します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
