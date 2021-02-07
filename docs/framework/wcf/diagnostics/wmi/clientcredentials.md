---
description: '詳細情報: ClientCredentials'
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 7b0b5a05e5b61de717567de664079f2ed1e20f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757664"
---
# <a name="clientcredentials"></a>ClientCredentials

ClientCredentials  
  
## <a name="syntax"></a>構文  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>メソッド  

 ClientCredentials クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 ClientCredentials クラスには、次のプロパティがあります。  
  
### <a name="clientcertificate"></a>ClientCertificate  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用する X.509 証明書です。  
  
### <a name="httpdigest"></a>HttpDigest  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 現在の Http ダイジェスト資格情報です。  
  
### <a name="issuedtoken"></a>IssuedToken  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 ローカル セキュリティ トークン サービスにアクセスするために使用されるエンドポイント アドレスおよびバインディングです。  
  
### <a name="peer"></a>ピア  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報です。  
  
### <a name="servicecertificate"></a>ServiceCertificate  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 サービスの X.509 証明書です。  
  
### <a name="supportinteractive"></a>SupportInteractive  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 資格情報が対話的なネゴシエーションをサポートしているかどうかを指定するブール値です。  
  
### <a name="username"></a>UserName  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用するユーザー名とパスワードです。  
  
### <a name="windows"></a>Windows  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用する Windows 資格情報です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ClientCredentials>
