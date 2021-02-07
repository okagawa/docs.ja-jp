---
description: 詳細については、「非ジェネリック ForEach」を参照してください。
title: 非ジェネリックの ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 16635da4ef57ff7b59e178f5954465d8b86bf488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741953"
---
# <a name="non-generic-foreach"></a>非ジェネリックの ForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] のツールボックスには、制御フロー アクティビティのセットが用意されています。これには、<xref:System.Activities.Statements.ForEach%601> コレクションを反復処理できる <xref:System.Collections.Generic.IEnumerable%601> が含まれています。  
  
 <xref:System.Activities.Statements.ForEach%601> では、その <xref:System.Activities.Statements.ForEach%601.Values%2A> プロパティを <xref:System.Collections.Generic.IEnumerable%601> 型にする必要があります。 このため、ユーザーは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイス (<xref:System.Collections.ArrayList> など) を実装するデータ構造を反復処理できません。 <xref:System.Activities.Statements.ForEach%601> の非ジェネリック バージョンにはこの要件はありませんが、コレクション内の値の型の互換性を確保するために実行時の複雑さが増します。  
  
 このサンプルでは、非ジェネリックの <xref:System.Activities.Statements.ForEach%601> アクティビティとそのデザイナーを実装する方法を示します。 このアクティビティは、<xref:System.Collections.ArrayList> の反復処理に使用できます。  
  
## <a name="foreach-activity"></a>ForEach アクティビティ  

 C#/Visual Basic のステートメントは、コレクションの要素を `foreach` 列挙し、コレクションの各要素に対して埋め込みステートメントを実行します。 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] に相当する `foreach` のアクティビティは、<xref:System.Activities.Statements.ForEach%601> および <xref:System.Activities.Statements.ParallelForEach%601> です。 <xref:System.Activities.Statements.ForEach%601> アクティビティには、値のリストと本体が含まれます。 実行時に、リストが反復処理されて、リスト内の値ごとに本体が実行されます。  
  
 ほとんどの場合、ジェネリック バージョンのアクティビティを使用することをお勧めします。ジェネリック バージョンのアクティビティは、そのアクティビティを使用するシナリオの大半に対応し、コンパイル時の型チェックが実現するためです。 非ジェネリック バージョンは、非ジェネリックの <xref:System.Collections.IEnumerable> インターフェイスを実装する型を反復処理するために使用できます。  
  
## <a name="class-definition"></a>クラス定義  

 次のコード例は、非ジェネリックの `ForEach` アクティビティの定義を示しています。  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 Body (省略可能)  
 コレクション内の要素ごとに実行される <xref:System.Activities.ActivityAction> 型の <xref:System.Object>。 各要素は、`Argument` プロパティを使用して Body に渡されます。  
  
 Values (省略可能)  
 反復処理される要素のコレクション。 コレクションのすべての要素の型が互換性のある型であることが実行時に確認されます。  
  
## <a name="example-of-using-foreach"></a>ForEach の使用例  

 アプリケーションでの ForEach アクティビティの使用方法を次のコードに示します。  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|条件|Message|重大度|例外の種類|  
|---------------|-------------|--------------|--------------------|  
|値が `null` である|必須のアクティビティ引数 'Values' の値が指定されませんでした。|エラー|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach デザイナー  

 サンプルのアクティビティ デザイナーは、組み込みの <xref:System.Activities.Statements.ForEach%601> アクティビティ用に提供されているデザイナーに外観が似ています。 デザイナーは、[ **サンプル** の **非ジェネリックアクティビティ** ] カテゴリの [ツールボックス] に表示されます。 デザイナーのツールボックスには **ForEachWithBodyFactory** という名前が付けられます。これは、アクティビティがツールボックスでを公開するためです。これにより、 <xref:System.Activities.Presentation.IActivityTemplateFactory> 適切に構成されたを持つアクティビティが作成され <xref:System.Activities.ActivityAction> ます。  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a>このサンプルを実行するには  
  
1. 選択したプロジェクトをソリューションのスタートアップ プロジェクトに設定します。  
  
    1. **Codetestclient** は、コードを使用してアクティビティを使用する方法を示しています。  
  
    2. **デザイナ Testclient** デザイナー内でアクティビティを使用する方法を示します。  
  
2. プロジェクトをビルドして実行します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
