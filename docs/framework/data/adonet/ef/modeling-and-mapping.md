---
title: モデリングとマッピング
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: e70411bb9c9797ee348aeef055c9af20ea092ae3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450597"
---
# <a name="modeling-and-mapping"></a>モデリングとマッピング
Entity Framework では、概念モデル、ストレージ モデル、およびこの 2 つのモデル間のマッピングをアプリケーションに最適な方法で定義できます。 Visual Studio の Entity Data Model ツールを使用すると、データベースまたはグラフィカルなモデルから [.edmx ファイル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))を作成し、データベースまたはモデルが変更されたときにそのファイルを更新できます。  
  
 Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。 Code First の開発に対しては、2 つの異なるシナリオがあります。 どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。  
  
 詳しくは、「[モデルの作成](/ef/ef6/modeling/)」をご覧ください。  
  
 .NET Framework に含まれている EDM ジェネレーターを使用することもできます。 EdmGen.exe は、既存のデータ ソースから .csdl ファイル、.ssdl ファイル、および .msl ファイルを生成します。 モデルとマッピングの内容を手動で作成することもできます。 詳しくは、「[EDM ジェネレーター (EdmGen.exe)](edm-generator-edmgen-exe.md)」をご覧ください。
