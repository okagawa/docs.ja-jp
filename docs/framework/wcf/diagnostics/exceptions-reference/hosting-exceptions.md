---
title: ホスティング例外
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: 342420f10ed53e4f4786ed9506cfde5fbfcfc957
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263335"
---
# <a name="hosting-exceptions"></a>ホスティング例外

ここでは、ホスティングによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|完全 URI は許可されていません。 完全 URI は、ServiceHostingEnvironment.EnsureServiceAvailable API に対しては許可されていません。 対応するサービスの仮想パスを使用してください。|  
|Hosting_BuildProviderCouldNotCreateType|指定した CLR 型をサービスのコンパイル中に読み込むことができません。 この型が、アプリケーションの \ App_Code ディレクトリにあるソースファイルで定義されているか \\ 、アプリケーションの \bin ディレクトリにあるコンパイル済みアセンブリに含まれているか、 \\ またはグローバルアセンブリキャッシュにインストールされているアセンブリに存在することを確認してください。 型名では、大文字と小文字が区別されます。 \ App_Code や \bin などのディレクトリは、 \\ \\ アプリケーションのルートディレクトリに配置する必要があります。 \\\ App_Code および \\ \bin ディレクトリをサブディレクトリに入れ子にすることはできません。|
