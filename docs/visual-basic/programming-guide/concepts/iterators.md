---
title: Iterators
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: e638d35aeb86837d91fb14681d300772e3c2375a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410930"
---
# <a name="iterators-visual-basic"></a>反復子 (Visual Basic)

*反復子*を使用して、リストや配列などのコレクションをステップ実行することができます。

iterator メソッドまたは `get` アクセサーは、コレクションに対するカスタム イテレーションを実行します。 iterator メソッドは、[Yield](../../language-reference/statements/yield-statement.md) ステートメントを使用して、各要素を 1 回に 1 つ返します。 `Yield` ステートメントに達すると、コードの現在の場所が記憶されます。 次回、iterator 関数が呼び出されると、この位置から実行が再開されます。

[For Each…Next](../../language-reference/statements/for-each-next-statement.md) ステートメントまたは LINQ クエリを使用して、クライアント コードから反復子を呼び出します。

次の例では、`For Each` ループの最初の反復子により、最初の `Yield` ステートメントに達するまで `SomeNumbers` iterator メソッドで実行が続行されます。 このイテレーションは 3 の値を返し、iterator メソッドの現在の場所が保持されます。 ループの次のイテレーションでは、iterator メソッドの実行が中断した場所から続行し、`Yield` ステートメントに達したときに再度停止します。 このイテレーションは 5 の値を返し、ここでも iterator メソッドの現在の場所が保持されます。 iterator メソッドの最後に達すると、ループが完了します。

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

Iterator メソッドまたは `get` アクセサーの戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> となります。

`Exit Function` または `Return` ステートメントを使用すると、反復を終了できます。

Visual Basic の iterator 関数と `get` アクセサー宣言には、[Iterator](../../language-reference/modifiers/iterator.md) 修飾子が含まれています。

反復子は、Visual Studio 2012 の Visual Basic で導入されました。

**このトピックの内容**

- [単純な反復子](#BKMK_SimpleIterator)

- [コレクション クラスを作成する](#BKMK_CollectionClass)

- [Try ブロック](#BKMK_TryBlocks)

- [匿名メソッド](#BKMK_AnonymousMethods)

- [ジェネリック リストと共に反復子を使用する](#BKMK_GenericList)

- [構文情報](#BKMK_SyntaxInformation)

- [技術的な実装](#BKMK_Technical)

- [反復子の使用](#BKMK_UseOfIterators)

> [!NOTE]
> このトピックの単純な反復子の例を除くすべての例には、`System.Collections` および `System.Collections.Generic` 名前空間の [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) ステートメントが含まれています。

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a> 単純な反復子

次の例では、[For…Next](../../language-reference/statements/for-next-statement.md) ループ内に 1 つの `Yield` ステートメントが含まれます。 `Main` では、`For Each` ステートメント本文の各イテレーションで iterator 関数が呼び出され、これが次の `Yield` ステートメントに続行されます。

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a> コレクション クラスを作成する

次の例の `DaysOfTheWeek` クラスは、<xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを必要とする <xref:System.Collections.IEnumerable> インターフェイスを実装します。 コンパイラは、<xref:System.Collections.IEnumerator> を返す `GetEnumerator` メソッドを暗黙的に呼び出します。

`GetEnumerator` メソッドは、`Yield` ステートメントを使用して各文字列を 1 つずつ返すもので、関数の宣言には `Iterator` 修飾子が存在します。

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

次の例では、動物のコレクションを含む `Zoo` クラスを作成します。

クラス インスタンス (`theZoo`) を参照する `For Each` ステートメントでは、`GetEnumerator` メソッドが暗黙的に呼び出されます。 `Birds` および `Mammals` プロパティを参照する `For Each` ステートメントでは、`AnimalsForType` という名前の iterator メソッドが使用されます。

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a> Try ブロック

Visual Basic では、[Try...Catch...Finally ステートメント](../../language-reference/statements/try-catch-finally-statement.md)の `Try` ブロックで `Yield` ステートメントを使用できます。 `Yield` ステートメントがある `Try` ブロックには、`Catch` ブロックと `Finally` ブロックを記述することができます。

次の例では、iterator 関数の中に `Try`、`Catch`、`Finally` の各ブロックが存在します。 iterator 関数内の `Finally` ブロックは、`For Each` の反復が完了する前に実行されます。

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

`Yield` ステートメントを `Catch` ブロックや `Finally` ブロックに記述することはできません。

(iterator メソッドではなく) `For Each` 本体で例外がスローされた場合、iterator 関数の `Catch` ブロックは実行されず、iterator 関数の `Finally` ブロックが実行されます。 iterator 関数内の `Catch` ブロックでキャッチされるのは、iterator 関数内で発生した例外だけです。

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a> 匿名メソッド

Visual Basic では、iterator 関数として匿名関数を使用することができます。 次に例を示します。

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

次の例に示したのは、iterator メソッドではない、引数を検証するメソッドです。 このメソッドは、コレクション要素を表す匿名反復子の結果を返します。

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

このようにせず、検証を iterator 関数内で行った場合、`For Each` 本体の最初の反復の開始まで検証を実行できません。

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a> ジェネリック リストと共に反復子を使用する

次の例の `Stack(Of T)` ジェネリック クラスは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスを実装しています。 `Push` メソッドでは、`T` 型の配列に値を割り当てます。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドは、`Yield` ステートメントを使って配列値を返します。

ジェネリック メソッド <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> だけでなく、非ジェネリック メソッド <xref:System.Collections.IEnumerable.GetEnumerator%2A> も実装する必要があります。 これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.IEnumerable> から継承するためです。 非ジェネリック実装は、ジェネリック実装に従います。

例では名前付き反復子を使用して、同じデータ コレクションでのさまざまな反復処理をサポートします。 この場合の名前付き反復子は、`TopToBottom` プロパティと `BottomToTop` プロパティ、および `TopN` メソッドです。

`BottomToTop` プロパティの宣言には、`Iterator` キーワードが含まれます。

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a> 構文情報

反復子は、メソッドまたは `get` アクセサーとして指定できます。 反復子を、イベント、インスタンス コンストラクター、静的コンストラクター、静的デストラクターで指定することはできません。

`Yield` ステートメント内の式の型から反復子の戻り値の型への暗黙的な変換が存在する必要があります。

Visual Basic の場合、iterator メソッドで `ByRef` パラメーターを指定することはできません。

Visual Basic の場合、"Yield" は予約語ではなく、`Iterator` メソッドまたは `get` アクセサーで使用される場合にのみ、特別な意味を持ちます。

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a> 技術的な実装

メソッドとして反復子を記述しても、コンパイラが入れ子のクラス (つまり、事実上、ステート マシン) に変換します。 このクラスは、クライアント コードで `For Each...Next` ループが続く限り、反復子の位置を追跡します。

コンパイラの動作を確認するには、Ildasm.exe ツールを使用して、iterator メソッドに対して生成される Microsoft 中間言語コードを表示します。

[クラス](../../language-reference/statements/class-statement.md)または[構造体](../../language-reference/statements/structure-statement.md)用の反復子を作成する場合、<xref:System.Collections.IEnumerator> インターフェイス全体を実装する必要はありません。 コンパイラは、反復子を検出すると、<xref:System.Collections.IEnumerator> または <xref:System.Collections.Generic.IEnumerator%601> インターフェイスの `Current`、`MoveNext`、および `Dispose` メソッドを自動的に生成します。

`For Each…Next` ループの連続する反復ごとに (または `IEnumerator.MoveNext` を直接呼び出すと)、前の `Yield` ステートメントの後で次の反復子コード本体が再開されます。 その後、反復子本体の最後に到達するか、`Exit Function` または `Return` ステートメントが検出されるまで、次の `Yield` ステートメントに続行されます。

反復子は、<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> メソッドをサポートしません。 反復処理を最初から再度行う場合は、新しい反復子を取得する必要があります。

詳細については、「[Visual Basic 言語の仕様](../../reference/language-specification/index.md)」を参照してください。

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a> 反復子の使用

反復子を使用すると、複雑なコードを使用して一覧シーケンスを設定する必要がある場合に、`For Each` ループの単純さを維持することができます。 これは次のような場合に役立ちます。

- 最初の `For Each` ループ イテレーションの後に一覧シーケンスを変更する。

- 最初の `For Each` ループ イテレーションの前に大きい一覧が完全に読み込まれないようにする。 例として、ページ フェッチでのテーブル行のバッチの読み込みなどがあります。 また、別の例として、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A> メソッドでの .NET Framework 内の反復子の実装があります。

- 反復子に一覧の作成をカプセル化する。 iterator メソッドでは、一覧を作成してから、ループで各結果を生成することができます。

## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next ステートメント](../../language-reference/statements/for-each-next-statement.md)
- [Yield ステートメント](../../language-reference/statements/yield-statement.md)
- [Iterator](../../language-reference/modifiers/iterator.md)
