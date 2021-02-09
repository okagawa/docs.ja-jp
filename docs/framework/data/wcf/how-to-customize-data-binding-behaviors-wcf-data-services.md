---
description: '詳細情報: 方法:データ バインディングの動作をカスタマイズする (WCF Data Services)'
title: '方法: データ バインディングの動作をカスタマイズする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 60c8808f90f8e0a824a8b2b641508c0fe33f14cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765686"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>方法: データ バインディングの動作をカスタマイズする (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services では、バインディング コレクションに対してオブジェクトが追加または削除されたときまたはプロパティの変更が検出されたときに <xref:System.Data.Services.Client.DataServiceCollection%601> によって呼び出されるカスタム ロジックを提供できます。 このカスタム ロジックは、<xref:System.Func%602> デリゲートと呼ばれるメソッドとして提供されています。これらは、カスタム メソッドの完了時にも既定の動作を実行する必要がある場合は `false` を返し、イベントの後続の処理を停止する必要がある場合は `true` を返します。  
  
 このトピックの例は、`entityChanged` の `entityCollectionChanged` パラメーターと <xref:System.Data.Services.Client.DataServiceCollection%601> パラメーターの両方のカスタム メソッドを示します。 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスは、「[WCF Data Services クイックスタート](quickstart-wcf-data-services.md)」を完了すると作成されます。  
  
## <a name="example"></a>例  

 次の XAML ファイルの分離コード ページは、バインディング コレクションにバインドされたデータへの変更が発生すると呼び出される <xref:System.Data.Services.Client.DataServiceCollection%601> とカスタム メソッドを作成します。 <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> イベントが発生すると、指定したメソッドは、バインディング コレクションから削除された項目がデータ サービスから削除されることを防止します。 <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> イベントが発生すると、出荷済みの注文に対する変更がないことを確認するために、`ShipDate` の値が検証されます。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>例  

 次の XAML は、前の例のウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)
