---
description: '詳細情報: BC31535:フレンド アセンブリ参照 <reference> は無効です'
title: フレンド アセンブリ参照 <reference> は無効です
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: e3e08edede9bee4710c415a61592857229ea4f35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796198"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a>BC31535:フレンド アセンブリ参照 \<reference> は無効です

フレンド アセンブリ参照 \<reference> は無効です。 厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。

 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡されたアセンブリ名は、厳密な名前のアセンブリを識別しますが、`PublicKey` 属性を含みません。

 **エラー ID:** BC31535

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 厳密な名前のフレンド アセンブリの公開キーを調べます。 `PublicKey` 属性を使用して <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡されるアセンブリ名の一部として、公開キーを含めます。

## <a name="see-also"></a>関連項目

- <xref:System.Reflection.AssemblyName>
- [フレンド アセンブリ](../../../standard/assembly/friend.md)
