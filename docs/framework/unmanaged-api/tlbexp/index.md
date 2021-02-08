---
description: '詳細情報: Tlbexp ヘルパー関数 (アンマネージ API リファレンス)'
title: Tlbexp ヘルパー関数 (アンマネージ API リファレンス)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 8d5aacbe63d111b0b53f6bc76357a37ee4660d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646258"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Tlbexp ヘルパー関数 (アンマネージ API リファレンス)

[タイプ ライブラリ エクスポーター ツール](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) により、TlbRef.dll という名前のダイナミック リンク ライブラリが読み込まれます。 この DLL には、エクスポーター ツールによってアセンブリからタイプ ライブラリへの変換処理中に使用される、2 つのヘルパー関数とインターフェイスが含まれています。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [GetTypeLibInfo 関数](gettypelibinfo-function.md)  
 タイプ ライブラリのローカライズとオペレーティング システムに関する情報を提供します。  
  
 [LoadTypeLibWithResolver 関数](loadtypelibwithresolver-function.md)  
 [ITypeLibResolver インターフェイス](itypelibresolver-interface.md)の実装を使ってタイプ ライブラリを読み込み、参照されたあらゆるタイプ ライブラリを解決します。  
  
 [ITypeLibResolver インターフェイス](itypelibresolver-interface.md)  
 タイプ ライブラリの完全修飾パスを返す、[ResolveTypeLib メソッド](resolvetypelib-method.md)を提供します。
