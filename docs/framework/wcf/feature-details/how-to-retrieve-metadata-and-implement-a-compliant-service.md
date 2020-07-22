---
title: '方法: メタデータの取得および準拠サービスの実装をする'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 6bd67ec8dcc0e73d097796b44974dce00b9a4eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601219"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>方法: メタデータの取得および準拠サービスの実装をする
サービスのデザイン担当者と実装担当者が同じであるとは限りません。 アプリケーションの相互運用が重要な環境では、コントラクトを Web サービス記述言語 (WSDL) でデザインまたは記述した場合、開発者はそのコントラクトに準拠するサービスを実装する必要があります。 また、既存のサービスを Windows Communication Foundation (WCF) に移行し、ワイヤ形式を維持することもできます。 さらに、双方向コントラクトでは、呼び出し元でコールバック コントラクトを実装する必要もあります。  
  
 このような場合は、 [ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) (または同等のツール) を使用して、コントラクトの要件を満たすために実装できるマネージ言語のサービスコントラクトインターフェイスを生成する必要があります。 通常、 [ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)は、チャネルファクトリまたは WCF クライアントの種類で使用されるサービスコントラクトを取得するために使用されます。また、正しいバインディングとアドレスを設定するクライアント構成ファイルでも使用されます。 生成された構成ファイルを使用するには、それをサービスの構成ファイルに変更する必要があります。 また、サービス コントラクトを変更する必要もあります。  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>データを取得して準拠サービスを実装するには  
  
1. メタデータファイルまたはメタデータエンドポイントに対して[ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、コードファイルを生成します。  
  
2. 出力コード ファイルを検索し、<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 属性でマークされた対象のインターフェイス (複数ある場合) 部分を見つけます。 次のコード例は、 [ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)によって生成される2つのインターフェイスを示しています。 最初の例 (`ISampleService`) は、準拠サービスを作成するために実装するサービス コントラクト インターフェイスです。 2 番目の例 (`ISampleServiceChannel`) は、サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> の両方を拡張するクライアント用のヘルパー インターフェイスです。これはクライアント アプリケーションでも使用されます。  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. すべての操作に対する応答アクションを WSDL で指定していない場合、生成後の操作コントラクトでは、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> プロパティがワイルドカード文字 (*) に設定される場合があります。 このプロパティの設定を削除します。 削除しない場合は、サービス コントラクト メタデータを実装するときに、それらの操作のメタデータをエクスポートできません。  
  
4. クラスにインターフェイスを実装してサービスをホストします。 例については、「[方法: サービスコントラクトを実装](../how-to-implement-a-wcf-contract.md)する」を参照するか、「例」の簡単な実装を参照してください。  
  
5. [ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)によって生成されるクライアント構成ファイルで、構成セクション [\<client>](../../configure-apps/file-schema/wcf/client.md) を構成セクションに変更し [\<services>](../../configure-apps/file-schema/wcf/services.md) ます。 (生成されたクライアント アプリケーション構成ファイルの例については、次の例を参照してください)。  
  
6. 構成セクション内で、 [\<services>](../../configure-apps/file-schema/wcf/services.md) `name` [\<services>](../../configure-apps/file-schema/wcf/services.md) サービス実装の [構成] セクションに属性を作成します。  
  
7. サービスの `name` 属性をユーザーのサービス実装の構成名に設定します。  
  
8. 実装するサービス コントラクトを使用するエンドポイント構成要素をサービス構成セクションに追加します。  
  
## <a name="example"></a>例  
 次のコード例は、 [ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)をメタデータファイルに対して実行することによって生成されるコードファイルの大部分を示しています。  
  
 このコードには、次の項目が示されています。  
  
- コントラクトの要件に準拠するサービス コントラクト インターフェイス (実装する場合) (`ISampleService`)。  
  
- サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> の両方を拡張するクライアント用のヘルパー インターフェイス。これはクライアント アプリケーションでも使用されます(`ISampleServiceChannel`)。  
  
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> を拡張するヘルパー クラス。クライアント アプリケーションで使用されます。(`SampleServiceClient`)  
  
- サービスから生成された構成ファイル。  
  
- `ISampleService` サービスの簡単な実装。  
  
- クライアント側の構成ファイルからサービス側バージョンへの変換。  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>関連項目

- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
