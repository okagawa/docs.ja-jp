---
title: ボタンを承認ボタンとして指定する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142148"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>方法 : Windows フォームの Button コントロールを承認ボタンとして指定する
どの Windows フォームでも、コントロールを<xref:System.Windows.Forms.Button>既定のボタンとして指定できます。 ユーザーが Enter キーを押すと、フォーム上の他のコントロールにフォーカスが置かねな場合でも、既定のボタンがクリックされます。  
  
> [!NOTE]
> ただし、フォーカスのあるコントロールが別のボタンである場合は例外です 。  
  
### <a name="to-designate-the-accept-button"></a>[同意] ボタンを指定するには  
  
1. フォームの<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを適切な<xref:System.Windows.Forms.Button>コントロールに設定します。  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button コントロールの概要](button-control-overview-windows-forms.md)
- [Windows フォームの Button コントロールを選択する方法](ways-to-select-a-windows-forms-button-control.md)
- [方法 : Windows フォームのボタンのクリックに応答する](how-to-respond-to-windows-forms-button-clicks.md)
- [方法 : Windows フォームの Button コントロールをキャンセル ボタンとして指定する](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button コントロール](button-control-windows-forms.md)
