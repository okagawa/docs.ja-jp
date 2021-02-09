---
description: '詳細情報: AddHandler ステートメント'
title: AddHandler ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c0c34abd7ff225765ab36278825a555e2b84b0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674104"
---
# <a name="addhandler-statement"></a>AddHandler ステートメント

実行時にイベントをイベント ハンドラーに関連付けます。  
  
## <a name="syntax"></a>構文  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>指定項目  

|||
|---|---|
|event|処理するイベントの名前。|  
|`eventhandler`|イベントを処理するプロシージャの名前。|
|||
  
## <a name="remarks"></a>Remarks  

 `AddHandler` および `RemoveHandler` ステートメントを使用すると、プログラムの実行中にいつでもイベント処理を開始および停止できます。  
  
 `eventhandler` プロシージャのシグネチャは、イベント `event` のシグネチャと一致する必要があります。  
  
 `Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。 `AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。 `Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。 詳細については、「[Handles](handles-clause.md)」を参照してください。  
  
> [!NOTE]
> カスタム イベントの場合は、`AddHandler` ステートメントによってイベントの `AddHandler` アクセサーが呼び出されます。 カスタム イベントの詳細については、「[Event ステートメント](event-statement.md)」を参照してください。  
  
## <a name="example"></a>例  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>関連項目

- [RemoveHandler ステートメント](removehandler-statement.md)
- [Handles](handles-clause.md)
- [Event ステートメント](event-statement.md)
- [イベント](../../programming-guide/language-features/events/index.md)
