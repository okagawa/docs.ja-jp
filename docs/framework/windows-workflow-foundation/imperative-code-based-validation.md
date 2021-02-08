---
description: 詳細については、「命令型 Code-Based 検証」を参照してください。
title: 命令型コードに基づく検証
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 36759572393be613a569c4846e3610fcbbde2a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792701"
---
# <a name="imperative-code-based-validation"></a>命令型コードに基づく検証

命令型コードに基づく検証は、アクティビティでアクティビティ自身に関する検証を可能にする簡単な方法を提供し、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、および <xref:System.Activities.NativeActivity> から派生するアクティビティで使用できます。 検証のエラーまたは警告を判断する検証コードがアクティビティに追加されます。  
  
## <a name="using-code-based-validation"></a>コードに基づく検証の使用

コードに基づく検証は、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、および <xref:System.Activities.NativeActivity> から派生するアクティビティでサポートされています。 検証コードは <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドに配置できます。また、検証エラーまたは警告はメタデータ引数に追加できます。 次の例では、`Cost` が `Price` よりも高い場合、検証エラーがメタデータに追加されます。  
  
> [!NOTE]
> `Cost` と `Price` はこのアクティビティの引数ではありませんが、デザイン時に設定されるプロパティです。 その理由は、これらの値は <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドで検証できるためです。 引数に流入するデータの値は、データが実行時まで流れないのでデザイン時には検証できません。しかし、`RequiredArgument` 属性とオーバーロード グループを使用してアクティビティの引数を検証すると、それらの引数にバインドされていることが確認できます。 このコード例では、`RequiredArgument` 引数の `Description` 属性を確認します。これがバインドされていなければ、検証エラーが生成されます。 必須の引数につい [ては、「必須の引数とオーバーロードグループ](required-arguments-and-overload-groups.md)」を対象としています。  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 既定では、検証エラーがメタデータに追加されるのは、<xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> が呼び出されたときです。 検証の警告を追加するには、<xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> を受け取る <xref:System.Activities.Validation.ValidationError> オーバーロードを使用し、<xref:System.Activities.Validation.ValidationError> プロパティを設定することで <xref:System.Activities.Validation.ValidationError.IsWarning%2A> が警告を表すことを示します。  
  
 検証が発生するのは、ワークフローがワークフロー デザイナーで修正され、検証エラーまたは警告がワークフロー デザイナーに表示されたときです。 ワーク フローの呼び出し時に検証も行われます。検証エラーが発生すると、既定の検証ロジックによって <xref:System.Activities.InvalidWorkflowException> がスローされます。 検証の呼び出しと検証の警告またはエラーへのアクセスの詳細については、「 [アクティビティ検証の呼び出し](invoking-activity-validation.md)」を参照してください。  
  
 <xref:System.Activities.CodeActivity.CacheMetadata%2A> からスローされる例外は、検証エラーとして処理されません。 これらの例外は、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> への呼び出しからエスケープされ、呼び出し元によって処理される必要があります。  
  
 コードに基づく検証は、コードを含み、ワークフロー内の他のアクティビティから表示できないアクティビティを検証するときに役立ちます。 宣言型制約の検証では、ワークフロー内のアクティビティと他のアクティビティとの間の関係を検証する機能が提供されます。これについては、「 [宣言型制約](declarative-constraints.md) 」を参照してください。
