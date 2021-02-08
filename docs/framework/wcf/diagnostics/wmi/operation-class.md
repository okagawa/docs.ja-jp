---
description: '詳細: Operation クラス'
title: Operation class
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 035c02bc05b7a64c5d15538001dbdcf2ec0b135b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803075"
---
# <a name="operation-class"></a>Operation class

Operation  
  
## <a name="syntax"></a>構文  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>メソッド  

 Operation クラスで定義されているメソッドはありせん。  
  
## <a name="properties"></a>プロパティ  

 Operation クラスには、次のプロパティがあります。  
  
### <a name="action"></a>操作  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 要求メッセージの WS-Addressing 操作。  
  
### <a name="asyncpattern"></a>AsyncPattern  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 `Begin`サービスコントラクトで [開始/終了山かっこ] と `End` [開始/終了山かっこ] の組み合わせを使用して、操作が非同期的に実装されることを示します。  
  
### <a name="behaviors"></a>動作  

 データ型 : Behavior array  
  
 アクセスの種類: 読み取り専用  
  
 この操作に関連付けられている動作。  
  
### <a name="iscallback"></a>IsCallback  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 この操作がコールバック操作の場合、True。  
  
### <a name="isinitiating"></a>IsInitiating  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 メソッドが、サーバーでセッションを開始できる操作を実装するかどうかを指定します。  
  
### <a name="isoneway"></a>IsOneWay  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 操作が応答メッセージを返すかどうかを指定します。  
  
### <a name="isterminating"></a>IsTerminating  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 操作が応答メッセージを返すかどうかを指定します。  
  
### <a name="methodsignature"></a>MethodSignature  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 操作のメソッド署名。  
  
### <a name="name"></a>名前  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 操作の名前。  
  
### <a name="parametertypes"></a>ParameterTypes  

 データ型 : string array  
  
 アクセスの種類: 読み取り専用  
  
 操作のパラメーターの型。  
  
### <a name="replyaction"></a>ReplyAction  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 操作の応答メッセージの SOAP アクションの値。  
  
### <a name="returntype"></a>ReturnType  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 操作の戻り値の型。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.OperationDescription>
