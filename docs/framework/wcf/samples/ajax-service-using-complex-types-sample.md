---
title: 複合型を使用した AJAX サービスのサンプル
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4227446e8844accd06490d8e7cf933da43d875a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575915"
---
# <a name="ajax-service-using-complex-types-sample"></a>複合型を使用した AJAX サービスのサンプル

このサンプルでは、Windows Communication Foundation (WCF) を使用して、複合型のインスタンスを作成し、それらをサービスとクライアントの間で JavaScript Object Notation (JSON) として送信する、ASP.NET の非同期 JavaScript and XML (AJAX) サービスを作成する方法を示します。 AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。 このサンプルは、[基本的な AJAX サービス](basic-ajax-service.md)のサンプルに基づいています。

WCF での AJAX サポートは、コントロールを介して ASP.NET AJAX で使用できるように最適化されてい <xref:System.Web.UI.ScriptManager> ます。 ASP.NET AJAX で WCF を使用する例については、 [ajax のサンプル](ajax.md)を参照してください。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

次のサンプルのサービスは、AJAX 固有のコードを持たない WCF サービスです。 <xref:System.ServiceModel.Web.WebGetAttribute> 属性は適用されないため、既定の HTTP 動詞 ("POST") が使用されます。 サービスには 1 つの `DoMath` 操作があります。この操作は、`MathResult` という名前の複合型を返します。 複合型は標準のデータ コントラクト型で、AJAX 固有のコードも含まれていません。

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。

クライアント Web ページ Complextypeclientpage.aspx には、ユーザーがページの [**計算の実行**] ボタンをクリックしたときにサービスを呼び出すための ASP.NET と JavaScript のコードが含まれています。 サービスを呼び出すコードは、 [HTTP post サンプルを使用する AJAX サービス](ajax-service-using-http-post.md)と同様に、JSON 本文を構築し、http post を使用して送信します。

サービス呼び出しに成功したら、生成された JavaScript オブジェクトのそれぞれのデータ メンバー (`sum`、`difference`、`product`、および `quotient`) にアクセスできます。

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。

2. 「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の説明に従って、ソリューション ComplexTypeAjaxService をビルドします。

3. に移動 `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` します (プロジェクトディレクトリからブラウザーで complextypeclientpage.aspx を開かないでください)。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a>関連項目

- [基本的な AJAX サービス](basic-ajax-service.md)
