---
title: 基本クラス '<assemblyname>' を含むアセンブリ '<classname>' への参照が必要です。参照をプロジェクトに追加してください。
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: d2fb3498219dfe3318ec418ede250de818874ba9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162337"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a>BC30007:基本クラス '\<assemblyname>' を含むアセンブリ '\<classname>' への参照が必要です。参照をプロジェクトに追加してください。

基底クラス '\<classname>' を含むアセンブリ '\<assemblyname>' への参照が必要です。 プロジェクトに参照を追加してください。

 プロジェクト内で直接参照されないダイナミック リンク ライブラリ (DLL) またはアセンブリでクラスが定義されています。 Visual Basic コンパイラでは、クラスが複数の DLL またはアセンブリで定義されている場合に備えて、あいまいさを避けるための参照が必要になります。

 **エラー ID:** BC30007

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 参照されない DLL またはアセンブリの名前をプロジェクト参照に含めます。

## <a name="see-also"></a>関連項目

- [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)
- [壊れた参照のトラブルシューティング](/visualstudio/ide/troubleshooting-broken-references)
