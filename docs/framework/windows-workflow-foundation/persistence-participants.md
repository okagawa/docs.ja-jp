---
title: 永続参加要素
ms.date: 03/30/2017
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
ms.openlocfilehash: 0bff6cc8fafb1832dc4d0e33b754fe3adb81dcf6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246109"
---
# <a name="persistence-participants"></a>永続参加要素

永続参加要素は、アプリケーション ホストによってトリガーされる永続化操作 (保存または読み込み) に参加できます。 には、 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] **PersistenceParticipant** と **PersistenceIOParticipant** という2つの抽象クラスが付属しています。このクラスを使用して、永続参加要素を作成できます。 永続参加要素はこれらのクラスの 1 つから派生し、目的のメソッドを実装して、このクラスのインスタンスを <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> の <xref:System.ServiceModel.Activities.WorkflowServiceHost> コレクションに追加します。 アプリケーション ホストは、ワークフロー インスタンスを永続化するときにこのようなワークフロー拡張機能を必要とする場合があり、適切なときに永続参加要素の適切なメソッドを呼び出します。  
  
 次の一覧では、永続化 (保存) 操作のさまざまな段階で永続化サブシステムが実行するタスクについて説明します。 3 番目および 4 番目の段階で永続参加要素が使用されます。 参加要素が i/o 参加要素 (i/o 操作にも参加する永続参加要素) である場合、参加者は6番目のステージでも使用されます。  
  
1. ワークフロー状態、ブックマーク、マップされた変数、およびタイムスタンプなどの組み込みの値を収集します。  
  
2. ワークフロー インスタンスに関連付けられた拡張コレクションに追加された永続参加要素を収集します。  
  
3. すべての永続参加要素によって実装された <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> メソッドを呼び出します。  
  
4. すべての永続参加要素によって実装された <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドを呼び出します。  
  
5. ワークフローを永続ストアに永続化または保存します。  
  
6. すべての <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> 永続 i/o 参加要素に対してメソッドを呼び出します。 参加者が i/o 参加要素ではない場合、このタスクはスキップされます。 永続化がトランザクションである場合、Transaction.Current プロパティにトランザクションが提供されます。  
  
7. すべての永続参加要素が完了するのを待機します。 すべての参加要素がインスタンス データの永続化に成功したら、トランザクションをコミットします。  
  
 永続参加要素は **PersistenceParticipant** クラスから派生し、 **Collectvalues** および **mapvalues** メソッドを実装できます。 永続 i/o 参加要素は **PersistenceIOParticipant** クラスから派生し、 **Collectvalues** および **mapvalues** メソッドの実装に加えて **beginonsave** メソッドを実装できます。  
  
 それぞれの段階の完了後に次の段階が開始されます。 たとえば、最初の段階で **すべて** の永続参加要素から値が収集されます。 2 番目の段階では、最初の段階で収集されたすべての値がマップのためにすべての永続参加要素に提供されます。 3 番目の段階では、1 番目および 2 番目の段階で収集してマップされたすべての値が永続参加要素に提供されます。  
  
 次の一覧では、読み込み操作のさまざまな段階で永続化サブシステムが実行するタスクについて説明します。 4 番目の段階で永続参加要素が使用されます。 永続 i/o 参加要素 (i/o 操作にも参加する永続参加要素) は、3番目の段階でも使用されます。  
  
1. ワークフロー インスタンスに関連付けられた拡張コレクションに追加された永続参加要素を収集します。  
  
2. 永続ストアからワークフローを読み込みます。  
  
3. すべての <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> 永続 i/o 参加要素でを呼び出し、すべての永続参加要素が完了するまで待機します。 永続化がトランザクションである場合、Transaction.Current にトランザクションが提供されます。  
  
4. 永続ストアから取得されたデータに基づいて、メモリ内のワークフロー インスタンスを読み込みます。  
  
5. 各永続参加要素の <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> メソッドを呼び出します。  
  
 永続参加要素は **PersistenceParticipant** クラスから派生し、 **publishvalues** メソッドを実装できます。 永続 i/o 参加要素は **PersistenceIOParticipant** クラスから派生し、 **publishvalues** メソッドの実装に加えて **beginonload** メソッドを実装できます。  
  
 ワークフロー インスタンスを読み込む場合、永続化プロバイダーはそのインスタンスのロックを作成します。 これにより、各インスタンスが複数ノードのシナリオでは、複数のホストによって読み込まれることはありません。 ロックされたワークフロー インスタンスを読み込もうとすると、次のような例外が表示されます: 例外「System.ServiceModel.Persistence.InstanceLockException: 要求された操作は、インスタンス '00000000-0000-0000-0000-000000000000' のロックが取得できなかったため、完了できませんでした」。 このエラーが発生するのは、次のいずれかが発生した場合です。  
  
- 複数ノード シナリオで、インスタンスが他のホストによって読み込まれます。  これらの種類の競合を解決する方法がいくつかあります。ロックと再試行を所有するノードへ処理を転送するか、または他のホストでの作業を保存できないようにする読み込みを強制します。  
  
- 単一ノード シナリオで、ホストがクラッシュしました。  ホストが再度起動されるとき (プロセスのリサイクル、または新しい永続化プロバイダー ファクトリの作成)、新しいホストが、ロックの期限がまだ切れていないために古いホストによってまだロックされているインスタンスの読み込みを試みます。  
  
- 単一ノード シナリオで、当該インスタンスがあるポイントで中止され、別のホスト ID を持つ新しい永続化プロバイダー インスタンスが作成されます。  
  
 ロックのタイムアウト値の既定値は 5 分です。呼び出したときに、別のタイムアウト値を指定できます <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
- [方法: カスタム永続参加要素を作成する](how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>関連項目

- [ストア拡張](store-extensibility.md)
