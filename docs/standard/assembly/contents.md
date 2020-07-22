---
title: アセンブリの内容
description: この記事では、アセンブリ メタデータ、型メタデータ、MSIL コード、リソースなどが含まれる可能性がある、.NET アセンブリの内容について説明します。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework]
- assemblies [.NET Core]
- single-file assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 94df452162ed7290fab7fa267d2624e6d844a587
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378567"
---
# <a name="assembly-contents"></a>アセンブリの内容

一般に、静的アセンブリは次の 4 つの要素から構成されます。

- アセンブリ メタデータを保持する[アセンブリ マニフェスト](manifest.md)。

- 型メタデータ。  

- 型を実装する MSIL (Microsoft Intermediate Language) コード。 コンパイラによって 1 つ以上のソース コード ファイルから生成されます。

- 一連の[リソース](../../framework/resources/index.md)。  

このうち必須なのはアセンブリ マニフェストだけですが、アセンブリになんらかの機能を与えるには、型またはリソースのいずれかが必要になります。

次の図は、これらの要素を 1 つの物理ファイルにグループ化したものを示しています。

![MyAssembly.dll という名前のシングルファイル アセンブリ](./media/contents/single-file-assembly.gif)

ソース コードをデザインするときは、作成するアプリケーションの機能を 1 つのファイルにまとめるのか複数のファイルに分割するのか、分割する場合は機能をどのように分けるのかを明確に決める必要があります。 .NET コードをデザインする場合も同様に、機能を 1 つのアセンブリにまとめるのか複数のアセンブリに分割するのか、分割する場合は機能をどのように分割するのかを決めておく必要があります。

## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](index.md)
- [アセンブリ マニフェスト](manifest.md)
- [アセンブリのセキュリティに関する考慮事項](security-considerations.md)
