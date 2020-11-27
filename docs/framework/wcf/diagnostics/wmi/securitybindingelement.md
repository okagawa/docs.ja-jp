---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 61eae75de04f75b6ad6e78d16569595732b3d28f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273309"
---
# <a name="securitybindingelement"></a>SecurityBindingElement

SecurityBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>メソッド  

 SecurityBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 SecurityBindingElement クラスには、次のプロパティがあります。  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 バインディングで使用するアルゴリズムを指定します。  
  
### <a name="includetimestamp"></a>IncludeTimestamp  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 各メッセージにタイムスタンプが含まれるかどうかを指定するブール値です。  
  
### <a name="keyentropymode"></a>KeyEntropyMode  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 キーの作成に使用されるエントロピのソースです。  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  

 データ型 : LocalServiceSecuritySettings  
  
 アクセスの種類: 読み取り専用  
  
 ローカル サービスに対するバインディング固有のセキュリティ プロパティです。  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 メッセージ セキュリティで使用されるバージョンです。  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 このバインディングのセキュリティ ヘッダー内の要素の順序です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
