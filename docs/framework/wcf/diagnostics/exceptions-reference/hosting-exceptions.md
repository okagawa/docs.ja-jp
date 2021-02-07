---
description: 詳細については、「例外のホスト」をご覧ください。
title: ホスティング例外
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: ba2ff3d4bd069483ddc620a09bb97eeaddf84a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686454"
---
# <a name="hosting-exceptions"></a>ホスティング例外

ここでは、ホスティングによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|完全 URI は許可されていません。 完全 URI は、ServiceHostingEnvironment.EnsureServiceAvailable API に対しては許可されていません。 対応するサービスの仮想パスを使用してください。|  
|Hosting_BuildProviderCouldNotCreateType|指定した CLR 型をサービスのコンパイル中に読み込むことができません。 この型が、アプリケーションの \ App_Code ディレクトリにあるソースファイルで定義されているか \\ 、アプリケーションの \bin ディレクトリにあるコンパイル済みアセンブリに含まれているか、 \\ またはグローバルアセンブリキャッシュにインストールされているアセンブリに存在することを確認してください。 型名では、大文字と小文字が区別されます。 \ App_Code や \bin などのディレクトリは、 \\ \\ アプリケーションのルートディレクトリに配置する必要があります。 \\\ App_Code および \\ \bin ディレクトリをサブディレクトリに入れ子にすることはできません。|
