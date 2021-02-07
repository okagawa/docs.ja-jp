---
description: '詳細情報: PrivacyNoticeBindingElement'
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: ece6687f12c4ece45254b1acddb9598e4a10cbb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743883"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement

PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>メソッド  

 PrivacyNoticeBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 PrivacyNoticeBindingElement クラスには、次のプロパティがあります。  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 プライバシーに関する声明のバージョンです。  
  
### <a name="url"></a>url  

 データ型: 文字列  
  
 アクセスの種類: 読み取り専用  
  
 プライバシーに関する声明がある URL です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
