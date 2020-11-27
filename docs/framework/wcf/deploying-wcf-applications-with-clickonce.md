---
title: ClickOnce を使用して WCF アプリケーションを展開する
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: ad4c603d07885aa16640b71d43038746d3702b05
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260858"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>ClickOnce を使用して WCF アプリケーションを展開する

Windows Communication Foundation (WCF) を使用するクライアントアプリケーションは、ClickOnce テクノロジを使用して配置できます。 このテクノロジを使用すると、クライアント アプリケーションが、信頼できる証明書でデジタル署名されている場合、コード アクセス セキュリティによって提供されるランタイム セキュリティ保護を受けられます。 ClickOnce アプリケーションの署名に使用される証明書は、信頼された発行者のストアに存在する必要があり、またそのクライアント コンピューターのローカル セキュリティ ポリシーでは、発行者の証明書で署名されたアプリケーションに対して、完全信頼のアクセス許可が構成される必要があります。  
  
 ClickOnce アプリケーションと信頼された発行元の構成については、「 [Clickonce 信頼された発行元の構成](/previous-versions/dotnet/articles/ms996418(v=msdn.10))」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [信頼されたアプリケーションの配置の概要](/visualstudio/deployment/trusted-application-deployment-overview)
- [Windows フォームアプリケーションの ClickOnce 配置](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
