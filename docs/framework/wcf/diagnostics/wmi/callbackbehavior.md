---
description: 詳細情報:/の動作
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: fa9e403324afe818e247d1f751cce0ce7d5a6fb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757762"
---
# <a name="callbackbehavior"></a>CallbackBehavior

CallbackBehavior  
  
## <a name="syntax"></a>構文  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>メソッド  

 CallbackBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 CallbackBehavior クラスには、次のプロパティがあります。  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 true の場合、サービスが双方向セッションを閉じると、セッションが自動的に閉じられます。  
  
### <a name="concurrencymode"></a>ConcurrencyMode  

 データ型: 文字列  
アクセスの種類: 読み取り専用  
  
 サービスが単一のスレッド、複数のスレッド、再入可能呼び出しのいずれをサポートするかを指定します。  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 不明なシリアル化データをネットワークで送信するかどうかを指定する値です。  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 有効にした場合は、コールバックの例外に関する詳細情報が、サービスに戻されるエラーに添付されます。  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 1 つのシリアル化されたオブジェクトで許可される項目の最大数。  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 現在の同期コンテキストを使用して実行のスレッドを選択するかどうかを指定します。  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  

 データ型 : boolean  
  
 アクセスの種類: 読み取り専用  
  
 システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
