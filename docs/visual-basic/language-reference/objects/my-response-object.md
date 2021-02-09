---
description: '詳細情報: My.Response オブジェクト'
title: My.Response オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 551528356040539994251cb66a905d0249f482da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640616"
---
# <a name="myresponse-object"></a>My.Response オブジェクト

<xref:System.Web.UI.Page> に関連付けられた <xref:System.Web.HttpResponse> オブジェクトを取得します。 このオブジェクトでは、HTTP 応答データをクライアントに送信し、その応答に関する情報を含めることができます。  
  
## <a name="remarks"></a>Remarks  

 `My.Response` オブジェクトには、ページに関連付けられている現在の <xref:System.Web.HttpResponse> オブジェクトが含まれています。  
  
 `My.Response` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。  
  
## <a name="example"></a>例  

 次の例では、`My.Request` オブジェクトからヘッダー コレクションを取得し、`My.Response` オブジェクトを使用して ASP.NET ページに書き込みます。  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Web.HttpResponse>
- [My.Request オブジェクト](my-request-object.md)
