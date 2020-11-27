---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: eb174d12731d7f1bc78f4d709cf043daf2346bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269796"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement

BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>メソッド  

 BinaryMessageEncodingBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  

 BinaryMessageEncodingBindingElement クラスには、次のプロパティがあります。  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。  
  
## <a name="maxsessionsize"></a>MaxSessionSize  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 エンコーディングに使用するバッファーのサイズ (バイト単位) を指定する値です。  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  

 データ型 : sint32  
  
 アクセスの種類: 読み取り専用  
  
 新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。  
  
## <a name="readerquotas"></a>ReaderQuotas  

 データ型 : XmlDictionaryReaderQuotas  
  
 アクセスの種類: 読み取り専用  
  
 リーダのクォータ。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
