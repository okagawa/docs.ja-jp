---
title: SYSLIB0002 エラー
description: コンパイル時のエラー SYSLIB0002 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 53eb51d5e525c463e5698710bdb6fa0c0907e43c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440778"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a>SYSLIB0002: PrincipalPermissionAttribute は旧型式

<xref:System.Security.Permissions.PrincipalPermissionAttribute> コンストラクターは旧型式であり、.NET 5.0 以降、コンパイル時のエラー `SYSLIB0002` を発生させます。 この属性をインスタンス化したり、メソッドに適用したりすることはできません。

他の非推奨警告とは異なり、エラーを非表示にすることはできません。

## <a name="workarounds"></a>回避策

- ASP.NET MVC アクション メソッドにこの属性を適用する場合:

  ASP.NET に組み込まれている承認インフラストラクチャを使用することを検討してください。 次のコードからは、<xref:System.Web.Mvc.AuthorizeAttribute> 属性を使用してコントローラーに注釈を付ける方法がわかります。 ASP.NET ランタイムによって、アクションの実行前に、ユーザーが承認されます。

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  詳細については、「[ASP.NET Core でのロールベースの承認](/aspnet/core/security/authorization/roles)」と「[ASP.NET Core での承認の概要](/aspnet/core/security/authorization/introduction)」を参照してください。

- Web アプリのコンテキスト外でライブラリ コードにこの属性を適用する場合:

  <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> メソッドを呼び出して、メソッドの先頭で手動によるチェックを実行します。

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>関連項目

- [PrincipalPermissionAttribute は現在使用されていないエラーです](3.1-5.0.md#principalpermissionattribute-is-obsolete-as-error)
