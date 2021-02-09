---
description: '詳細情報: 方法:データベース値を上書きすることで競合を解決する'
title: '方法: データベース値を上書きすることで競合を解決する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 4eaa66b4bb49706bb1ca6449d24c688a89f2750b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723505"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>方法: データベース値を上書きすることで競合を解決する

変更を再送信する前に、データベース内の予期した値と実際の値の違いを調整するために、<xref:System.Data.Linq.RefreshMode.KeepCurrentValues> を使用してデータベース内の値を上書きできます。 詳細については、「[オプティミスティック コンカレンシー:概要)](optimistic-concurrency-overview.md) の下のステートメントを右クリックします。  
  
> [!NOTE]
> どの場合も、データベースから最新のデータを取得することで、まずクライアントのレコードが更新されます。 この処理によって、次の更新処理が同じコンカレンシー チェックで失敗することを防止できます。  
  
## <a name="example"></a>例  

 このシナリオでは、ユーザー 1 が変更を送信しようとしたときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。これは、途中でユーザー 2 が Assistant 列と Department 列を変更していたためです。 次の表は、この状況を示しています。  
  
||管理者|Assistant|Department|  
|------|-------------|---------------|----------------|  
|ユーザー 1 およびユーザー 2 が照会した最初のデータベース状態|Alfreds|Maria|Sales|  
|ユーザー 1 が送信しようとした変更内容|Alfred||Marketing|  
|ユーザー 2 が既に送信した変更内容||Mary|サービス|  
  
 ユーザー 1 は、この競合を解決するために、データベース値を現在のクライアント メンバー値で上書きすることに決めます。  
  
 ユーザー 1 が <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> を使用して競合を解決すると、データベース内の結果は次の表のようになります。  
  
||管理者|Assistant|Department|  
|------|-------------|---------------|----------------|  
|競合解決後の新しい状態|Alfred<br /><br /> (ユーザー 1 の値)|Maria<br /><br /> (元の値)|Marketing<br /><br /> (ユーザー 1 の値)|  
  
 次のコード例は、データベース値を現在のクライアント メンバー値で上書きする方法を示しています  (個々のメンバーの競合に対する検査やカスタム ハンドリングは行われません)。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [方法: 変更の競合を管理する](how-to-manage-change-conflicts.md)
