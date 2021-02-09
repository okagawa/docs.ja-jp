---
description: '詳細情報: 方法:メンバーの競合情報を取得する'
title: '方法: メンバーの競合情報を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 2a33aba1a113bdfd66bdc341bfc9ae59406f2c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723401"
---
# <a name="how-to-retrieve-member-conflict-information"></a>方法: メンバーの競合情報を取得する

<xref:System.Data.Linq.MemberChangeConflict> クラスを使用すると、競合する個々のメンバーに関する情報を取得できます。 この同じコンテキストで、メンバーの競合の処理をカスタマイズできます。 詳しくは、「[オプティミスティック コンカレンシー: 概要)](optimistic-concurrency-overview.md) の下のステートメントを右クリックします。  
  
## <a name="example"></a>例  

 次のコードでは、<xref:System.Data.Linq.ObjectChangeConflict> オブジェクトを反復処理します。 オブジェクトごとに、次に <xref:System.Data.Linq.MemberChangeConflict> オブジェクトを反復処理します。  
  
> [!NOTE]
> <xref:System.Reflection> 情報を提供するには、<xref:System.Data.Linq.MemberChangeConflict.Member%2A> を含めます。  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [方法: 変更の競合を管理する](how-to-manage-change-conflicts.md)
