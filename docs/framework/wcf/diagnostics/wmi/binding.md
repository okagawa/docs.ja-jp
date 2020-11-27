---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: b72bd3903b7139c4adf2a8bd0ced6c34e7285640
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274297"
---
# <a name="binding"></a>バインド

wmi バインディング  
  
## <a name="syntax"></a>構文  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>メソッド  

 Binding クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 Binding クラスには、次のプロパティがあります。  
  
### <a name="bindingelements"></a>BindingElements  

 データ型 : BindingElement 配列  
  
 アクセスの種類: 読み取り専用  
  
 バインディングによって実装されるバインド要素のコレクションです。  
  
### <a name="closetimeout"></a>CloseTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 クローズ操作が完了するまで待機する時間です。  
  
### <a name="name"></a>名前  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 バインディングの名前。  
  
### <a name="namespace"></a>名前空間  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 バインディングの XML 名前空間。  
  
### <a name="opentimeout"></a>OpenTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 オープン操作が完了するまで待機する時間です。  
  
### <a name="receivetimeout"></a>ReceiveTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 受信操作が完了するまで待機する時間です。  
  
### <a name="scheme"></a>Scheme  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 このバインディングに組み込まれているチャネルおよびリスナー ファクトリによって使用される URI トランスポート スキームです。  
  
### <a name="sendtimeout"></a>SendTimeout  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 送信操作が完了するまで待機する時間です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.Binding>
