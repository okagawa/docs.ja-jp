---
description: '詳細情報: インスタンス'
title: インスタンス
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 9cd602164816a419b481ff600a7537593d4f500e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655267"
---
# <a name="instances"></a>インスタンス

カウンター名 : インスタンス  
  
## <a name="description"></a>説明  

 現在サービスに含まれているインスタンス コンテキストの数。  
  
 多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。 ただし、次のシナリオではこの規則は当てはまりません。  
  
- サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。  
  
- <xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.OperationBehaviorAttribute>
