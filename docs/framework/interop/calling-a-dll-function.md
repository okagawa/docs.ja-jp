---
title: DLL 関数の呼び出し
description: 紛らわしく見える可能性のある DLL 関数の呼び出しに関する問題を検討します。 この関数呼び出しのプロセスは、戻り値の型が blittable かどうかによって異なります。
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 90f8f47148e652a9942a35be1564bed94c155216
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620899"
---
# <a name="calling-a-dll-function"></a>DLL 関数の呼び出し
アンマネージド DLL 関数の呼び出しは、他のマネージド コードの呼び出しとほとんど同じですが、最初のうちは DLL 関数がわかりづらいと感じる違いがあります。 ここでは、通常とは異なる呼び出しに関連するいくつかの問題について説明しているトピックを紹介します。  
  
 プラットフォーム呼び出しから返される構造体は、マネージド コードとアンマネージド コードで同じ表現のデータ型である必要があります。 このような型のことは *blittable 型*と呼ばれます。これは、会話が必要ではないためです (「[Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)」(blittable 型と非 blittable 型) を参照してください)。 戻り値の型が非 blittable 構造体の関数を呼び出すには、非 blittable 型と同じサイズの blittable ヘルパー型を定義し、関数からデータが返された後にそのデータを変換します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [構造体の受け渡し](passing-structures.md)  
 事前に定義されたレイアウトを使用して、データ構造体の受け渡しに関する問題を特定します。  
  
 [コールバック関数](callback-functions.md)  
 コールバック関数に関する基本情報を提供します。  
  
 [方法: コールバック関数を実装する](how-to-implement-callback-functions.md)  
 マネージド コードにコールバック関数を実装する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [アンマネージ DLL 関数の処理](consuming-unmanaged-dll-functions.md)  
 プラットフォーム呼び出しを使用して、アンマネージ DLL 関数を呼び出す方法について説明します。  
  
 [プラットフォーム呼び出しによるデータのマーシャリング](marshaling-data-with-platform-invoke.md)  
 メソッドのパラメーターを宣言してアンマネージ ライブラリによってエクスポートされた関数に引数を渡す方法について説明します。
