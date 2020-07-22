---
title: コントロールを追加する
description: Windows フォームにコントロールを描画する方法について説明します。 コントロールは、フォーム上のコンポーネントであり、情報の表示やユーザー入力の受け入れに使用できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: d9ab0d78fa0153cce20fb17d22f6e9e781229ece
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325881"
---
# <a name="how-to-add-controls-to-windows-forms"></a>方法 : Windows フォームにコントロールを追加する

ほとんどのフォームは、ユーザーインターフェイス (UI) を定義するためにフォームの画面にコントロールを追加することによって設計されています。 *コントロール*は、情報の表示やユーザー入力の受け入れに使用されるフォーム上のコンポーネントです。 コントロールの詳細については、「 [Windows フォームコントロール](index.md)」を参照してください。

## <a name="to-draw-a-control-on-a-form"></a>フォームにコントロールを描画するには

1. フォームを開きます。 詳細については、「[方法: デザイナーで Windows フォームを表示する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))」を参照してください。

2. **ツールボックス**で、フォームに追加するコントロールをクリックします。

3. フォームで、コントロールの左上隅を配置する場所をクリックして、コントロールの右下隅を配置する場所にドラッグして、をドラッグします。

    コントロールが、指定された位置とサイズでフォームに追加されます。

    > [!NOTE]
    > 各コントロールには、既定のサイズが定義されています。 コントロールを**ツールボックス**からフォームにドラッグすると、コントロールの既定のサイズでコントロールをフォームに追加できます。

## <a name="to-drag-a-control-to-a-form"></a>コントロールをフォームにドラッグするには

1. フォームを開きます。 詳細については、「[方法: デザイナーで Windows フォームを表示する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))」を参照してください。

2. **ツールボックス**で、目的のコントロールをクリックし、フォームにドラッグします。

    コントロールは、既定のサイズで指定された位置にフォームに追加されます。

    > [!NOTE]
    > **ツールボックス**のコントロールをダブルクリックすると、既定のサイズでフォームの左上隅に追加できます。

    また、実行時にコントロールをフォームに動的に追加することもできます。 次のコード例では、コントロール <xref:System.Windows.Forms.TextBox> がクリックされると、コントロールがフォームに追加され <xref:System.Windows.Forms.Button> ます。

    > [!NOTE]
    > 次の手順では、**ボタン**コントロールが既に配置されているフォームが存在する必要があり `Button1` ます。

## <a name="to-add-a-control-to-a-form-programmatically"></a>プログラムによってフォームにコントロールを追加するには

1. フォームのクラス内のボタンのイベントを処理するメソッドで `Click` 、次のようなコードを挿入して、コントロール変数への参照を追加し、コントロールのを設定して、 `Location` コントロールを追加します。

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    > また、コントロールの他のプロパティを初期化するコードを追加することもできます。

    > [!IMPORTANT]
    > 悪意のあるを参照することにより、ネットワーク経由でローカルコンピューターをセキュリティ上のリスクにさらすことがあり `UserControl` ます。 これは、悪意のあるユーザーが有害なカスタムコントロールを作成した後、誤ってプロジェクトに追加した場合にのみ問題になります。

## <a name="see-also"></a>関連項目

- [Windows フォームコントロール](index.md)
- [方法 : Windows フォーム上のコントロールのサイズを変更する](how-to-resize-controls-on-windows-forms.md)
- [方法 : Windows フォーム コントロールによって表示されるテキストを設定する](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
