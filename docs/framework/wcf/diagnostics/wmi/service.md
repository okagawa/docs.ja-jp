---
title: サービス
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: aa4eecbcc8a2ef818cd99d777b0e3c2f1f222e46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273283"
---
# <a name="service"></a>サービス

サービス  
  
## <a name="syntax"></a>構文  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>メソッド  

 Service クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  

 Service クラスには次のプロパティがあります。  
  
### <a name="baseaddresses"></a>BaseAddresses  

 データ型 : string array  
  
 アクセスの種類: 読み取り専用  
  
 サービスによって使用されるベース アドレスです。  
  
### <a name="behaviors"></a>動作  

 データ型 : Behavior array  
  
 アクセスの種類: 読み取り専用  
  
 このサービスに関連付けられている動作です。  
  
### <a name="configurationname"></a>ConfigurationName  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。  
  
### <a name="distinguishedname"></a>DistinguishedName  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 アドレスでのサービス名です。  
  
### <a name="extensions"></a>の拡張  

 データ型 : string array  
  
 アクセスの種類: 読み取り専用  
  
 サービス インスタンスの拡張に対するインスタンス コンテキストです。  
  
### <a name="metadata"></a>Metadata  

 データ型 : string array  
  
 アクセスの種類: 読み取り専用  
  
 サービス メタデータの設定です。  
  
### <a name="name"></a>名前  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 このサービスの一意の名前。  
  
### <a name="namespace"></a>名前空間  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 サービスの名前空間です。  
  
### <a name="opened"></a>開始済み  

 データ型 : datetime  
  
 アクセスの種類: 読み取り専用  
  
 サービスが開かれた時刻です。  
  
### <a name="outgoingchannels"></a>OutgoingChannels  

 データ型 : Channel 配列  
  
 アクセスの種類: 読み取り専用  
  
 サービス インスタンスから送信しているチャネルです。  
  
### <a name="processid"></a>ProcessId  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 サービスをホストするプロセスのプロセス ID です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|
