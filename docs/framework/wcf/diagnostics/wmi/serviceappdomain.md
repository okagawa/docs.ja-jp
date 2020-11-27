---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 243c9112dd9caf5c92ef77aa0f45b4b1e71a4e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273257"
---
# <a name="serviceappdomain"></a>ServiceAppDomain

アプリケーション ドメインにサービスを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>メソッド  

 ServiceAppDomain クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 ServiceAppDomain クラスには、次のプロパティがあります。  
  
### <a name="ref"></a>ref  

 データ型 : Service  
修飾子: キー  
  
 アクセスの種類: 読み取り専用  
  
 このアプリケーション ドメインのサービスです。  
  
### <a name="ref"></a>ref  

 データ型: AppDomainInfo  
修飾子: キー  
  
 アクセスの種類: 読み取り専用  
  
 アプリケーション ドメインのプロパティが格納されています。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|
