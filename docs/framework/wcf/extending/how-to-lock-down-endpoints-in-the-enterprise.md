---
description: '詳細については、「方法: 企業内のエンドポイントをロックダウンする」を参照してください。'
title: '方法: 企業内のエンドポイントをロックダウンする'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 8e54c3d1cadcfdb6f0102281813eb3758320a143
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644230"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>方法: 企業内のエンドポイントをロックダウンする

大規模な企業では、多くの場合、企業のセキュリティ ポリシーに準拠してアプリケーションを開発する必要があります。 次のトピックでは、コンピューターにインストールされているすべての Windows Communication Foundation (WCF) クライアントアプリケーションの検証に使用できるクライアントエンドポイント検証コントロールを開発してインストールする方法について説明します。

この場合、このエンドポイントの動作は、machine.config ファイルの client セクションに追加されるため、検証コントロールはクライアント検証コントロールです [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) 。 WCF は、クライアントアプリケーションに対してのみ共通のエンドポイント動作を読み込み、サービスアプリケーションに対してのみ共通のサービス動作を読み込みます。 サービス アプリケーション用のこの同じ検証コントロールをインストールするには、検証コントロールがサービス動作であることが必要です。 詳細については、「」を参照してください [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) 。

> [!IMPORTANT]
> 構成ファイルのセクションに追加された属性 (APTCA) でマークされていないサービスまたはエンドポイントの動作 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) は、アプリケーションが部分信頼環境で実行されている場合は実行されず、この発生時に例外はスローされません。 検証コントロールなどの共通動作を強制的に実行するには、次のいずれかを行う必要があります。
>
> - 共通動作を属性でマークして、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 部分信頼アプリケーションとして展開されたときに実行できるようにします。 APTCA でマークされたアセンブリを実行できないように、コンピューターでレジストリ エントリを設定できます。
>
> - アプリケーションが完全に信頼されたアプリケーションとして配置されている場合は、ユーザーが部分信頼環境でアプリケーションを実行するようにコードアクセスセキュリティ設定を変更できないことを確認します。 ユーザーがこのような変更を行うことができる場合、カスタム検証コントロールは実行されず、例外もスローされません。 これを確認する方法の1つとして、「 `levelfinal` [コードアクセスセキュリティポリシーツール](../../tools/caspol-exe-code-access-security-policy-tool.md)を使用したオプション」 (Caspol.exe) を参照してください。
>
> 詳細については、「 [部分信頼のベストプラクティス](../feature-details/partial-trust-best-practices.md) 」および「 [サポートされている展開シナリオ](../feature-details/supported-deployment-scenarios.md)」を参照してください。

### <a name="to-create-the-endpoint-validator"></a>エンドポイント検証コントロールを作成するには

1. <xref:System.ServiceModel.Description.IEndpointBehavior> メソッドに、必要な検証手順を備えた <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> を作成します。 コードの例は次のとおりです。 (は、 `InternetClientValidatorBehavior` [セキュリティ検証](../samples/security-validation.md) のサンプルから取得したものです)。

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. 手順 1. で作成したエンドポイント検証コントロールを登録する新しい <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を作成します。 このコード例を次に示します。 (この例の元のコードは、 [セキュリティ検証](../samples/security-validation.md) のサンプルに含まれています)。

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. コンパイル済みのアセンブリが厳密な名前で署名されていることを確認します。 詳細については、 [厳密な名前ツール (SN.EXE)](../../tools/sn-exe-strong-name-tool.md) と、使用している言語のコンパイラコマンドを参照してください。

### <a name="to-install-the-validator-into-the-target-computer"></a>検証コントロールをターゲット コンピューターにインストールするには

1. 適切な機構を使用してエンドポイント検証をインストールします。 企業では、グループ ポリシーと Systems Management Server (SMS) を使用してインストールします。

2. [Gacutil.exe (グローバルアセンブリキャッシュツール)](../../tools/gacutil-exe-gac-tool.md)を使用して、厳密な名前のアセンブリをグローバルアセンブリキャッシュにインストールします。

3. <xref:System.Configuration?displayProperty=nameWithType> 名前空間の型を使用して、次の処理を行います。

    1. [\<behaviorExtensions>](../../configure-apps/file-schema/wcf/behaviorextensions.md)完全修飾型名を使用して、セクションに拡張機能を追加し、要素をロックします。

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. セクションのプロパティに behavior 要素を追加 `EndpointBehaviors` [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) し、要素をロックします。 (検証コントロールをサービスにインストールするには、検証コントロールがであること、 <xref:System.ServiceModel.Description.IServiceBehavior> およびプロパティに追加されている必要があり `ServiceBehaviors` ます)。次のコード例は、手順の後の適切な構成を示しています。 と b. の後の適切な構成を示しています。厳密な名前が存在しない点だけが異なります。

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. machine.config ファイルを保存します。 次のコード例では、手順 3. にあるすべてのタスクを実行しますが、変更された machine.config ファイルのコピーはローカルに保存されます。

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>例

次のコード例では、machine.config ファイルに共通の動作を追加し、そのコピーをディスクに保存する方法を示します。 は、 `InternetClientValidatorBehavior` [セキュリティ検証](../samples/security-validation.md) のサンプルから取得されます。

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>.NET Framework のセキュリティ

また、構成ファイルの要素を暗号化する必要がある場合もあります。 詳細については、「参照」を参照してください。

## <a name="see-also"></a>関連項目

- [DPAPI を使用した構成ファイルの要素の暗号化](/previous-versions/msp-n-p/ff647398(v=pandp.10))
- [RSA を使用した構成ファイルの要素の暗号化](/previous-versions/msp-n-p/ff650304(v=pandp.10))
