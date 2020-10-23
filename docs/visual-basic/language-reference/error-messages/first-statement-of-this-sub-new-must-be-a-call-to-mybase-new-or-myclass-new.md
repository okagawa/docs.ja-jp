---
title: この 'Sub New' の最初のステートメントは、'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません (パラメーターのないアクセス可能なコンストラクターがありません)。
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: bce8ad10bc201386f34d6623741c7d41a5dec27e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163026"
---
# <a name="bc30148-first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>BC30148:この 'Sub New' の最初のステートメントは、'MyBase.New' または 'MyClass.New' への呼び出しでなければなりません (パラメーターのないアクセス可能なコンストラクターがありません)。

'\<derivedname>' の基底クラス '\<basename>' には、引数なしで呼び出すことができる、アクセス可能な 'Sub New' がないため、この 'Sub New' の最初のステートメントは、'MyBase.New' または 'MyClass.New' に対して呼び出さなければなりません。

 派生クラスでは、すべてのコンストラクターが基底クラスのコンストラクター (`MyBase.New`) を呼び出す必要があります。 基底クラスに、派生クラスにアクセスできるパラメーターがないコンストラクターがある場合は、`MyBase.New` を自動的に呼び出すことができます。 それ以外の場合、基底クラスのコンストラクターはパラメーターを指定して呼び出す必要があり、これを自動的に実行することはできません。 この場合、すべての派生クラスのコンストラクターの最初のステートメントは、基底クラスのパラメーター化されたコンストラクターを呼び出すか、または基底クラスのコンストラクター呼び出しを行う派生クラス内の別のコンストラクターを呼び出す必要があります。

 **エラー ID:** BC30148

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 必要なパラメーターを指定して `MyBase.New` を呼び出すか、このような呼び出しを行うピア コンストラクターを呼び出します。

     たとえば、基底クラスに `Public Sub New(ByVal index as Integer)` として宣言されたコンストラクターがある場合、派生クラスのコンストラクターの最初のステートメントは `MyBase.New(100)` である可能性があります。

## <a name="see-also"></a>関連項目

- [継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
