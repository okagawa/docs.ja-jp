---
description: 詳細については、「Windows Communication Foundation トランザクションの概要」を参照してください。
title: Windows Communication Foundation のトランザクションの概要
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: c9d251e4f49ee8e2edaa0ce2ff48738383a1b76c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752653"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Windows Communication Foundation のトランザクションの概要

トランザクションを使用すると、一連の処理や操作を 1 つの不可分の実行単位にグループ化できます。 トランザクションとは、次の性質を持つ操作のコレクションです。  
  
- 原子性。 特定のトランザクションの下で完了したすべての更新は、コミットされて永続的に格納されるか、すべて中止されて前の状態にロールバックされるかのどちらかになります。  
  
- 一貫性。 トランザクション下で行う変更は、一貫性のある状態から別の一貫性のある状態への変換を表します。 たとえば、当座預金から普通預金への振り替えトランザクションでは、全体の預金残高は変更されません。  
  
- 分離。 トランザクションが他の同時実行されているトランザクションに属する確定されていない変更を監視することがなくなります。 分離により、コンカレンシーの抽象概念が提供され、1 つのトランザクションが別のトランザクションの実行に予期しない影響を与える可能性がなくなります。  
  
- 持続性。 マネージド リソース (データベース レコードなど) に対して 1 度コミットされた更新は、障害に直面しても永続的に残ります。  
  
 Windows Communication Foundation (WCF) には、Web サービスアプリケーションで分散トランザクションを作成するための豊富な機能セットが用意されています。  
  
 WCF は、WS-AtomicTransaction (WS-AT) プロトコルのサポートを実装します。これにより、WCF アプリケーションは、サードパーティのテクノロジを使用して構築された相互運用可能な Web サービスなど、相互運用可能なアプリケーションにトランザクションをフローさせることができます。 また、WCF では、OLE トランザクションプロトコルのサポートも実装しています。これは、トランザクションフローを有効にする相互運用機能が不要なシナリオで使用できます。  
  
 アプリケーション構成ファイルを使用してバインディングを構成し、トランザクション フローを有効にしたり無効にしたりできます。また、バインディングに目的のトランザクション プロトコルを設定できます。 さらに、構成ファイルを使用してサービス レベルでのトランザクションのタイムアウトを設定できます。 詳細については、「 [トランザクションフローの有効化](enabling-transaction-flow.md)」を参照してください。  
  
 <xref:System.ServiceModel> 名前空間のトランザクション属性で次の設定が行えます。  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を使用して、トランザクションのタイムアウトと分離レベルのフィルター処理を構成する。  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、トランザクション機能を有効にし、トランザクションの完了動作を構成する。  
  
- コントラクト メソッドで <xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を使用して、トランザクション フローの要求、許可、または拒否を行う。  
  
 詳細については、「 [ServiceModel トランザクション属性](servicemodel-transaction-attributes.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ServiceModel トランザクションの属性](servicemodel-transaction-attributes.md)
- [トランザクション フローの有効化](enabling-transaction-flow.md)
