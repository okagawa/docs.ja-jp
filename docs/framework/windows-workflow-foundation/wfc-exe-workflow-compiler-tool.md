---
title: Wfc.exe (ワークフローコマンドラインコンパイラツール)
description: ワークフローコマンドラインコンパイラツールである wfc.exe について説明します。
ms.date: 10/10/2020
helpviewer_keywords:
- wfc [Workflow]
- compiler tool
- wfc.exe
- Workflow, compilation
- Workflow, XOML files
- Workflow, wcf
ms.openlocfilehash: 01cbfeb72e19f727a3a470059047a2192228c394
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293859"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a>wfc.exe (ワークフローコマンドラインコンパイラツール)

> [!NOTE]
> ここでは、廃止された型と名前空間について説明します。

wfc.exe workflow コマンドラインコンパイラツールは、ファイル拡張子が *xoml* (古い) のワークフローマークアップファイルと連携します。

## <a name="compilation-process"></a>コンパイルプロセス

ワークフローのコンパイル時には、コンパイル手順として次のような処理が実行されます。

- アクティビティ自身が設定したルールに基づいて、ワークフロー アクティビティの検証が実行されます。 検証エラーが存在する場合、コンパイラはエラー リストを返します。  
- コンパイラに入力されるマークアップ定義から部分クラスが生成されます。  

- アクティビティのランタイム実行を支援するためにコードが生成されます。 子アクティビティの実行完了を親アクティビティが認識するために役立つイベント サブスクリプションが作成されます。  
- マークアップ ファイルから生成された部分クラス、およびコード ファイルからの部分クラスは、.NET Framework C# または Visual Basic コンパイラに入力されます。 この処理の出力は .NET アセンブリ WorkflowSample.dll です。 これを展開してワークフローを実行することができます。

### <a name="compiler-options"></a>コンパイラ オプション

このセクションでは、wfc.exe ワークフローコマンドラインコンパイラのオプションについて説明します。

```output
    Microsoft (R) Windows Workflow Compiler version 3.0.0.0
    Copyright (C) Microsoft Corporation 2005. All rights reserved.

                      Windows Workflow Compiler Options

    wfc.exe <Xoml file list> /target:assembly [<vb/cs file list>] [/language:...]
            [/out:...] [/reference:...] [/library:...] [/debug...] [/nocode...]
             [/checktypes...] [/resource:<resource info>]

                            - OUTPUT FILE -
    /out:<file>             Output file name
    /target:assembly        Build a Windows Workflow assembly (default).
                            Short form: /t:assembly
    /target:exe             Build a Windows Workflow application.
                            Short form: /t:exe
    /delaysign[+|-]         Delay-sign the assembly using only the public portion
                            of the strong name key.
    /keyfile:<file>         Specifies a strong name key file.
    /keycontainer:<string>  Specifies a strong name key container.

                            - INPUT FILES -
    <Xoml file list>        Xoml source file name(s).
    <vb/cs file list>       Code-beside file name(s).
    /reference:<file list>  Reference metadata from the specified assembly file(s).
                            Short form is '/r:'.
    /library:<path list>    Set of directories where to lookup for the references.
                            Short form is '/lib:'.
    /resource:<resinfo>     Embed the specified resource. Short form is '/res:'.
                            resinfo format is <file>[,<name>[,public|private]].

    Rules and freeform layout files must be embedded as assembly resources.
    The resource name is constructed by using the namespace and type name
    of the activity. For example, an activity named "MyActivity" in namespace
    "WFProject" would require resource names "WFProject.MyActivity.rules"
    and/or "WFProject.MyActivity.layout".

                            - CODE GENERATION -
    /debug[+|-]             Emit full debugging information. The default is '+'.
    /nocode[+|-]            Disallow code-beside model.
                            The default is '-'. Short form is '/nc:'.
    /checktypes[+|-]        Check for permitted types in wfc.exe.config file.
                            The default is '-'. Short form is '/ct:'.

                            - LANGUAGE -
    /language:[cs|vb]       The language to use for the generated class.
                            The default is 'CS' (C#). Short form is '/l:'.
    /rootnamespace:<string> Specifies the root Namespace for all type declarations.
                            Valid only for 'VB' (Visual Basic) language.
                            Short form is '/rns:'.

                            - MISCELLANEOUS -
    /help                   Display this usage message. Short form is '/?'.
    /nologo                 Suppress compiler copyright message. Short form is '/n'.

    /nowarn                 Ignore compiler warnings. Short form is '/w'.
```

## <a name="remarks"></a>解説

> [!NOTE]
> ここでは、廃止された型と名前空間について説明します。

承認された型の一覧は、通常、 *wfc.exe.config* ファイルで定義されます。 ワークフローコンパイルの検証フェーズでは、ワークフローソースドキュメントが承認された型の一覧に存在しない .NET Framework 型を直接参照している場合、ワークフローソースドキュメントは拒否されます。 承認された型の一覧は、、、、 `Assembly` `Namespace` `TypeName` および承認された { `True`&#124;`False` } インジケーターを各エントリが示す XML ドキュメントです。 `AuthorizedType` リスト内のエントリに対応します。 完全な名前空間を含めたり除外したりするために使用できるワイルドカード文字指定は許可されています。 たとえば、には、 `Type="System.*"` <xref:System> 子名前空間に含まれる型を含む、のすべての型が含まれます。
  
承認された型の一覧の使用は、オプションによって制御され <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> `'/checktypes'` ます。

```xml  
<configuration>  
  <System.Workflow.ComponentModel.WorkflowCompiler>
    <authorizedTypes>
      <targetFx version="v4.0">
        ...
        <authorizedType Assembly="System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True"/>
        ...
      </targetFx>
    </authorizedTypes>
  </System.Workflow.ComponentModel.WorkflowCompiler>  
</configuration>  
```

> [!WARNING]
> `Type="System.*"`型が存在する場合、コンパイルのためになどの他の意図しない型を含めることができ `Type="System.Configuration"` ます。 注意し、それぞれを確認する必要があります。 制限する必要がある型については、をに設定してください `Authorized` `False` 。

## <a name="see-also"></a>関連項目

- [AuthorizedType クラス](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
