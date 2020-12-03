---
title: '破壊的変更: MVC:ObjectModelValidator は、ValidationVisitor.Validate の新しいオーバーロードを呼び出す'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: MVC: ObjectModelValidator は、ValidationVisitor.Validate の新しいオーバーロードを呼び出す'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b28c357f51291a4f73889d5d413a983f79e09daf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760016"
---
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a>MVC:ObjectModelValidator は、ValidationVisitor.Validate の新しいオーバーロードを呼び出す

ASP.NET Core 5.0 で、<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> のオーバーロードが追加されました。 新しいオーバーロードは、次のプロパティを含む最上位レベルのモデル インスタンスを受け入れます。

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> は検証を実行するためにこの `ValidationVisitor` の新しいオーバーロードを呼び出します。 この新しいオーバーロードは、検証ライブラリが ASP.NET Core MVC のモデル検証システムと統合されている場合に関連します。

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="old-behavior"></a>以前の動作

`ObjectModelValidator` は、モデル検証中に、次のオーバーロードを呼び出します。

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a>新しい動作

`ObjectModelValidator` は、モデル検証中に、次のオーバーロードを呼び出します。

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a>変更理由

この変更は、他のプロパティの検査に依存する、<xref:System.ComponentModel.DataAnnotations.CompareAttribute> などの検証コントロールをサポートするために導入されました。

## <a name="recommended-action"></a>推奨アクション

`ValidationVisitor` の既存のオーバーロードを呼び出すために `ObjectModelValidator` に依存する検証フレームワークは、.NET 5.0 以降を対象とする場合に、新しいメソッドをオーバーライドする必要があります。

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
