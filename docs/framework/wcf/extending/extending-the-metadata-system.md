---
title: メタデータ システムの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: 7113120a3cde6b4e6a7eb1d329da625e25996952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272984"
---
# <a name="extending-the-metadata-system"></a>メタデータ システムの拡張

Windows Communication Foundation (WCF) メタデータシステムは、サービスベースのアプリケーションを実装するために必要なメタデータを表すクラスとインターフェイスのグループです。 クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [WCF 拡張に対するカスタム メタデータのエクスポート](exporting-custom-metadata-for-a-wcf-extension.md)  
 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、カスタム ポリシー アサーションを WSDL ドキュメントに埋め込む方法を説明します。  
  
 [WCF 拡張に対するカスタム メタデータのインポート](importing-custom-metadata-for-a-wcf-extension.md)  
 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、WSDL ドキュメント内のカスタム ポリシー アサーションの読み取りや応答を行う方法を説明します。  
  
 [カスタム バインディングを介したメタデータの公開と取得](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 カスタム バインドを介してメタデータを交換する方法について説明します。
