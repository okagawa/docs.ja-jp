---
description: '詳細情報: シールされていないクラス'
title: シールされていないクラス
ms.date: 10/22/2008
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6fe30c3a2ef8df6b983d857b9502805e90ab83dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641825"
---
# <a name="unsealed-classes"></a>シールされていないクラス

シールされたクラスから継承することはできません。これらは拡張できないようになっています。 対照的に、継承が可能なクラスは、シールされていないクラスと呼ばれます。

 ✔️ コストをかけずにフレームワークに高い拡張性を提供する優れた方法として、シールされていないクラスを、仮想または保護されたメンバーを追加せずに使用することを検討してください。

 開発者は、シールされていないクラスから継承を行って、カスタム コンストラクターや新しいメソッド、メソッド オーバーロードなどの便利なメンバーを追加したいと思うことがよくあります。 たとえば、`System.Messaging.MessageQueue` はシールされていないため、ユーザーは特定のキューのパスを既定とするカスタム キューを作成したり、特定のシナリオで API を簡略化するカスタム メソッドを追加したりできます。

 ほとんどのプログラミング言語では、クラスは既定でシールされていません。これは、フレームワークのほとんどのクラスに対する既定の設定としても推奨されます。 シールされていない型によって実現される拡張性は、フレームワーク ユーザーに高く評価されており、シールされていない型に関連するテスト コストが相対的に低いため、コストをかけずに提供されます。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [機能拡張のデザイン](designing-for-extensibility.md)
- [シール](sealing.md)
