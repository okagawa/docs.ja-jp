---
title: '破壊的変更:Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名'
description: 'ASP.NET Core 6.0 での破壊的変更について学習します。タイトル: Blazor:RequestImageFileAsync メソッドで変更されたパラメーター名'
author: scottaddie
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: bfaaa6bfe94c32fbc1a5b5b70db863d105d389b5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488242"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a>Blazor: RequestImageFileAsync メソッドで変更されたパラメーター名

`RequestImageFileAsync` メソッドの `maxWith` パラメーターの名前が `maxWith` から `maxWidth` に変更されました。

## <a name="version-introduced"></a>導入されたバージョン

6.0 Preview 1

## <a name="old-behavior"></a>以前の動作

パラメーター名のスペルは `maxWith` です。

## <a name="new-behavior"></a>新しい動作

パラメーター名のスペルは `maxWidth` です。

## <a name="reason-for-change"></a>変更理由

元のパラメーター名はタイプミスでした。

## <a name="recommended-action"></a>推奨される操作

`RequestImageFile` API で名前付きパラメーターを使用している場合は、`maxWith` パラメーター名を `maxWidth` に更新してください。 それ以外の場合、変更は必要ありません。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
