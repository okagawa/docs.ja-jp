---
title: ProgressBar コントロールによって表示される値を設定する
description: Windows フォーム ProgressBar コントロールによって表示される値を設定する方法について説明します。 使用できる方法は複数あります。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 75fe1b416636471d797a39134f45a05c972c9d39
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618104"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>方法: Windows フォーム ProgressBar コントロールによって表示される値を設定する
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 .NET Framework には、コントロール内に特定の値を表示するさまざまな方法が用意されて <xref:System.Windows.Forms.ProgressBar> います。 どの方法を選択するかは、当面のタスクや、解決する問題によって異なります。 次の表に、選択できる方法を示します。  
  
|アプローチ|説明|  
|--------------|-----------------|  
|コントロールの値を <xref:System.Windows.Forms.ProgressBar> 直接設定します。|この方法は、データソースからのレコードの読み取りなど、関連する項目の合計がわかっているタスクに役立ちます。 また、値を1回または2回だけ設定する必要がある場合は、これを簡単に行うことができます。 最後に、進行状況バーに表示される値を小さくする必要がある場合に、このプロセスを使用します。|  
|<xref:System.Windows.Forms.ProgressBar>固定値で表示を増やします。|この方法は、最小値と最大値の間に単純なカウント (経過時間、または既知の合計から処理されたファイルの数など) を表示する場合に便利です。|  
|<xref:System.Windows.Forms.ProgressBar>変化する値で表示を増やします。|この方法は、表示された値をさまざまな量の回数だけ変更する必要がある場合に便利です。 たとえば、一連のファイルをディスクに書き込んでいる間に消費されているハードディスク領域の量を示します。|  
  
 プログレスバーに表示される値を設定する最も直接的な方法は、プロパティを設定することです <xref:System.Windows.Forms.ProgressBar.Value%2A> 。 これは、デザイン時または実行時に行うことができます。  
  
### <a name="to-set-the-progressbar-value-directly"></a>ProgressBar 値を直接設定するには  
  
1. <xref:System.Windows.Forms.ProgressBar>コントロールの <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 値と値を設定 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> します。  
  
2. コードで、コントロールのプロパティを、設定 <xref:System.Windows.Forms.ProgressBar.Value%2A> した最小値と最大値の間の整数値に設定します。  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティとプロパティによって確立された境界の外側でプロパティを設定した場合 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 、コントロールは例外をスロー <xref:System.ArgumentException> します。  
  
     次のコード例は、値を直接設定する方法を示してい <xref:System.Windows.Forms.ProgressBar> ます。 このコードは、データソースからレコードを読み取り、データレコードが読み取られるたびに進行状況バーとラベルを更新します。 この例では、フォームに <xref:System.Windows.Forms.Label> コントロール、 <xref:System.Windows.Forms.ProgressBar> コントロール、 `CustomerRow` およびフィールドとフィールドを持つという行を持つデータテーブルが `FirstName` あることが必要です `LastName` 。  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     一定の間隔で進行状況を表示している場合は、値を設定してから、 <xref:System.Windows.Forms.ProgressBar> その間隔でコントロールの値を増やすメソッドを呼び出すことができます。 これは、タイマーや、進行状況を全体に対する割合として測定しないその他のシナリオに役立ちます。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>プログレスバーを固定値で増やすには  
  
1. <xref:System.Windows.Forms.ProgressBar>コントロールの <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 値と値を設定 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> します。  
  
2. コントロールのプロパティを、 <xref:System.Windows.Forms.ProgressBar.Step%2A> その量を表す整数に設定して、進行状況バーの表示値を増やします。  
  
3. メソッドを呼び出し <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> て、プロパティで設定された量によって表示される値を変更し <xref:System.Windows.Forms.ProgressBar.Step%2A> ます。  
  
     次のコード例は、進行状況バーがコピー操作でファイルの数を保持する方法を示しています。  
  
     次の例では、各ファイルがメモリに読み込まれると、進行状況バーとラベルが更新され、読み取られたファイルの合計が反映されます。 この例では、フォームにコントロールとコントロールが含まれている必要があり <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.ProgressBar> ます。  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     最後に、各増加が一意の値になるように、進行状況バーによって表示される値を増やすことができます。 これは、さまざまなサイズのファイルをハードディスクに書き込む場合や、進行状況を全体の割合として測定する場合など、一連の一意の操作を追跡する場合に便利です。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>動的な値で進行状況バーを拡大するには  
  
1. <xref:System.Windows.Forms.ProgressBar>コントロールの <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 値と値を設定 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> します。  
  
2. 指定し <xref:System.Windows.Forms.ProgressBar.Increment%2A> た整数によって表示される値を変更するには、メソッドを呼び出します。  
  
     次のコード例は、コピー操作中にどの程度のディスク領域が使用されたかを、進行状況バーで計算する方法を示しています。  
  
     次の例では、各ファイルがハードディスクに書き込まれると、進行状況バーとラベルが更新され、使用可能なハードディスク領域の容量が反映されます。 この例では、フォームにコントロールとコントロールが含まれている必要があり <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.ProgressBar> ます。  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar コントロールの概要](progressbar-control-overview-windows-forms.md)
- [ProgressBar コントロール](progressbar-control-windows-forms.md)
