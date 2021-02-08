---
description: 詳細については、「アクティビティ検証の構成」を参照してください。
title: アクティビティ検証の構成
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 9e40842a18dd2afd9a5ec0104d66e8971d691b5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792753"
---
# <a name="configuring-activity-validation"></a>アクティビティ検証の構成

アクティビティの検証を使用すると、アクティビティの作成者とユーザーは、アクティビティを実行する前に、アクティビティの構成エラーを特定および報告できます。 Windows Workflow Foundation (WF) には、次の3種類のアクティビティの検証が用意されています。  
  
- `RequiredArgument` 属性および `OverloadGroup` 属性。  
  
- 命令型コードに基づく検証。  
  
- 宣言の制約。  
  
 `RequiredArgument` 属性と `OverloadGroup` 属性は、アクティビティにおける特定の引数が必須であることを示します。 命令型コードに基づく検証には、アクティビティが自身に関する検証を提供できる単純な方法が用意されています。また、宣言の制約を使用すると、アクティビティとそれを含むワークフローとの関係に関して検証できます。 検証の要件に従ってアクティビティが正しく構成されていない場合、検証のエラーと警告が返されます。 包含するワークフローをワークフロー デザイナーを使用して作成する場合、デザイナーには任意の検証のエラーと警告が表示されます。 ワークフローをワークフロー デザイナーを使用せずに作成する場合、ワークフローを呼び出すときに任意の検証エラーが返されます。 ワークフローの作成方法にかかわらず、検証エラーを含むワークフローは実行できません。 ここでは、このようなアクティビティの検証に関する概要と、アクティビティの検証を呼び出す方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [必須の引数とオーバーロード グループ](required-arguments-and-overload-groups.md)  
 検証を実現するために、`RequiredArgument` 属性および `OverloadGroup` 属性を使用する方法について説明します。  
  
 [命令型コードに基づく検証](imperative-code-based-validation.md)  
 <xref:System.Activities.CodeActivity> および <xref:System.Activities.NativeActivity> に基づくアクティビティにコードに基づく検証を使用する方法について説明します。  
  
 [宣言の制約](declarative-constraints.md)  
 複雑なアクティビティの検証を実現するために宣言の制約を使用する方法について説明します。  
  
 [アクティビティ検証の呼び出し](invoking-activity-validation.md)  
 アクティビティの検証が自動的に呼び出される場合と、明示的に検証を呼び出す方法について説明します。  
  
## <a name="reference"></a>関連項目  
  
## <a name="related-sections"></a>関連項目
