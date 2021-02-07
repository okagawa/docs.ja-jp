---
description: '詳細情報: ControlBuilderInterceptor クラス'
title: ControlBuilderInterceptor クラス
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: ac32709bf814d17ac2a02222d4d92edc6cc93337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664822"
---
# <a name="controlbuilderinterceptor-class"></a>ControlBuilderInterceptor クラス

`ControlBuilderInterceptor`クラスを使用すると、コンパイルプロセスをカスタマイズまたは制御できます。

## <a name="syntax"></a>構文

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> `ControlBuilderInterceptor`クラスは内部であり、コードで直接使用するためのものではありません。
>
> 「解説」で説明されているように、この型の存在は、インターセプター型のサポートが存在するかどうかを確認するために確認できます。 Microsoft では、どのような状況でも、実稼働アプリケーションでこのクラスを使用することはサポートしていません。

## <a name="remarks"></a>解説

.NET Framework 2.0 および .NET Framework 3.5 では、 [年 8 2020 月](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) の更新プログラムにより、インターセプターの種類を使用してコンパイルプロセスをカスタマイズまたは制御するためのサポートが追加されました。 このサポートが存在するかどうかを判断するには、 <xref:System.Type.GetType?displayProperty=nameWithType> 次の `ControlBuilderInterceptor` コードに示すように、を使用して型の存在を確認します。

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

戻り値が null 以外の場合は、インターセプターのサポートが存在します。 戻り値がの場合、 `null` または例外がスローされた場合は、2020年8月の更新プログラムがインストールされておらず、インターセプターのサポートは存在しません。

インターセプターのサポートが存在する場合は、 <xref:System.Web.Compilation.ControlBuilderInterceptor> 以降のバージョンの .NET Framework とまったく同じ方法で、コンパイルプロセスと対話するインターセプター型を記述して登録できます。 .NET Framework 2.0 および .NET Framework 3.5 では、次の要件を満たす任意のクラスをインターセプター型にすることができます。

* には、パブリックなパラメーターなしのコンストラクターがあります。
* には、とという名前のパブリックな非静的メソッドがあります。このメソッドは、 `PreControlBuilderInit` `OnProcessGeneratedCode` およびメソッドと同じシグネチャとセマンティクスを持ち <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> ます。これは、.NET Framework の新しいバージョンに存在します。

`aspnet:20ControlBuilderInterceptor`ASP.NET アプリケーション設定 () のキーを使用して、インターセプターの種類を登録し `<appSettings>` ます。 このアプリケーション設定は、コンピューターまたはアプリケーションの *web.config* ファイルに一覧表示されている必要があります。 アセンブリ修飾型名を使用して、インターセプターの種類を指定します。 次の例は、という名前のインターセプター型を登録する方法を示して `Fabrikam.Interceptor` います。

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>
```

型のアセンブリ修飾名を取得するには、次の <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> コードに示すように、プロパティを使用します。

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

インターセプターのサポートが存在する場合、コンパイルプロセスは、前述の方法で表示されている型と対話します。 インターセプターのサポートが存在しない場合、アプリケーションの設定は無視され、効果はありません。

## <a name="requirements"></a>要件

**名前空間:** System.web. コンパイル

**アセンブリ:** System.web (System.Web.dll)

**.NET Framework のバージョン:** 3.5、2.0
