---
description: '詳細情報: Role-Based セキュリティ'
title: ロール ベース セキュリティ
ms.date: 07/15/2020
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET]
- security [.NET], role-based
- permissions [.NET], principals
- authentication [.NET], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: 66457248ccfaa8535ce150e7654cd5be20fb6a68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629527"
---
# <a name="role-based-security"></a>ロール ベース セキュリティ

財務アプリケーションや業務アプリケーションでは、ポリシーを適用するためにロールが使用されることがよくあります。 たとえば、要求を出しているユーザーが指定のロールのメンバーかどうかに基づいて、処理するトランザクションのサイズにアプリケーションが制限を課すことがあります。 たとえば、事務員には指定のしきい値よりも小さいトランザクションを処理する権限が与えられ、スーパーバイザにはより高いしきい値が与えられ、その上司にはさらに高いしきい値が与えられる (または制限がまったくない)、という場合です。 アプリケーションで 1 つのアクションを完了するために複数の承認を必要とするときにも、ロール ベース セキュリティを使用できます。 たとえば、どの社員も購買の要求を生成できるものの、その要求を仕入先に送信できる購買発注に変換できるのは購買部門だけにする場合などが考えられます。  
  
 .NET のロールベースセキュリティでは、関連付けられている id から構築されたプリンシパルに関する情報を現在のスレッドで使用できるようにすることで、承認をサポートします。 この場合の ID (および ID を利用して定義されるプリンシパル) は、Windows アカウントに基づく ID か、または Windows アカウントとは無関係のカスタム ID です。 .NET アプリケーションは、プリンシパルの id またはロールのメンバーシップ、またはその両方に基づいて承認決定を行うことができます。 ロールとは、セキュリティに関して同じ特権を持つプリンシパルの名前付きセット (窓口係や責任者など) です。 プリンシパルは、1 つ以上のロールのメンバーであることができます。 このため、アプリケーションはロール メンバーシップを使用して、要求されたアクションを実行する権限がプリンシパルにあるかどうかを決定できます。  
  
 コードアクセスセキュリティとの使いやすさと一貫性を提供するために、.NET のロールベースセキュリティでは、 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> 共通言語ランタイムがコードアクセスセキュリティチェックに似た方法で承認を実行できるようにするオブジェクトを提供します。 <xref:System.Security.Permissions.PrincipalPermission> クラスは、プリンシパルが一致している必要のある ID またはロールを表し、宣言セキュリティ チェックと強制セキュリティ チェックの両方と互換性があります。 プリンシパルの ID 情報に直接アクセスし、必要なときに、コード内でロール チェックと ID チェックを実行することもできます。  
  
 .NET は、さまざまなアプリケーションのニーズを満たすのに十分な柔軟性と拡張性を備えた、ロールベースのセキュリティサポートを提供します。 COM+ 1.0 Services などの既存の認証インフラストラクチャと相互運用する方法と、カスタムの認証システムを作成する方法のどちらかを選択できます。 ロール ベース セキュリティは、主にサーバー上で処理される ASP.NET Web アプリケーションでの使用に適しています。 ただし、.NET のロールベースセキュリティは、クライアントとサーバーのどちらでも使用できます。  
  
 このセクションを読む前に、「 [セキュリティの基本概念](key-security-concepts.md)」に記載されている内容を理解しておく必要があります。  
  
## <a name="see-also"></a>関連項目
  
- [プリンシパル オブジェクトと ID オブジェクト](principal-and-identity-objects.md)
- [セキュリティの基本概念](key-security-concepts.md)
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
- [ASP.NET Core のセキュリティ](/aspnet/core/security/)
