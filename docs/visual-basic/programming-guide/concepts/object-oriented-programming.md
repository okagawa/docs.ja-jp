---
title: オブジェクト指向プログラミング
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: f7e222cde8ce80d4c52cc8b4b111c576eb4041b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413194"
---
# <a name="object-oriented-programming-visual-basic"></a>オブジェクト指向プログラミング (Visual Basic)

Visual Basic は、カプセル化、継承、ポリモーフィズムなど、オブジェクト指向プログラミングを完全にサポートします。

 "*カプセル化*" とは、関連するプロパティ、メソッド、およびその他のメンバーのグループが 1 つの単位またはオブジェクトとして扱われることを意味します。

 "*継承*" は、既存のクラスに基づいて新しいクラスを作成する機能です。

 "*ポリモーフィズム*" とは、同じプロパティまたはメソッドを異なる方法で実装している複数のクラスを、交換して使用できることです。

 このセクションでは、次の概念について説明します。

- [クラスとオブジェクト](#classes-and-objects)
  - [クラス メンバー](#class-members)
    - [プロパティとフィールド](#properties-and-fields)
    - [メソッド](#methods)
    - [コンストラクター](#constructors)
    - [デストラクター](#destructors)
    - [イベント](#events)
    - [入れ子になったクラス](#nested-classes)
  - [アクセス修飾子とアクセス レベル](#access-modifiers-and-access-levels)
    - [クラスのインスタンス化](#instantiating-classes)
    - [共有クラスおよびメンバー](#shared-classes-and-members)
    - [匿名型](#anonymous-types)
- [継承](#inheritance)
  - [メンバーのオーバーライド](#overriding-members)
- [インターフェイス](#interfaces)
- [ジェネリック](#generics)
- [デリゲート](#delegates)

## <a name="classes-and-objects"></a>クラスとオブジェクト

"*クラス*" という用語と "*オブジェクト*" という用語は同じ意味で使われる場合がありますが、実際には、クラスはオブジェクトの "*型*" を表すのに対し、オブジェクトはクラスの使用可能な "*インスタンス*" です。 そのため、オブジェクトを作成する操作は "*インスタンス化*" と呼ばれます。 設計図との対比を使って説明すると、クラスは設計図であり、オブジェクトはその設計図を基にした建築物です。

クラスを定義するコード例を次に示します。

```vb
Class SampleClass
End Class
```

Visual Basic には、"*構造体*" と呼ばれる軽量バージョンのクラスも用意されています。構造体は、大きいオブジェクト配列を作成する必要があり、その配列に使用されるメモリの量を抑えたい場合に役立ちます。

構造体を定義するコード例を次に示します。

```vb
Structure SampleStructure
End Structure
```

詳細については次を参照してください:

- [Class ステートメント](../../language-reference/statements/class-statement.md)
- [Structure ステートメント](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a>クラス メンバー

各クラスには、さまざまな "*クラス メンバー*" を含めることができます。クラス メンバーには、クラスのデータを記述するプロパティ、クラスの動作を定義するメソッド、異なるクラスやオブジェクト間で通信するためのイベントが含まれます。

#### <a name="properties-and-fields"></a>プロパティとフィールド

フィールドとプロパティは、オブジェクトに格納されている情報を表します。 フィールドは、直接読み取ったり設定したりできるので変数と似ています。

フィールドを定義するコード例を次に示します。

```vb
Class SampleClass
    Public SampleField As String
End Class
```

プロパティには get プロシージャと set プロシージャがあり、これらを使用することで値の設定方法や戻り値をより細かく制御できます。

Visual Basic では、プロパティ値を格納するプライベート フィールドを作成するか、または自動実装プロパティと呼ばれる手法を使用できます。自動実装プロパティでは、値を格納するフィールドが背後で自動的に作成され、プロパティ プロシージャの基本的なロジックが提供されます。

自動実装プロパティを定義するコード例を次に示します。

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

プロパティ値の読み取りと書き込みのために追加の操作を実行する必要がある場合は、プロパティ値を格納するフィールドを定義し、値を格納および取得する基本的なロジックを実装します。

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

ほとんどのプロパティには、プロパティ値の設定と取得を行うための両方のメソッドまたはプロシージャがあります。 ただし、読み取り専用または書き込み専用のプロパティを作成して、プロパティの変更や読み取りを制限することもできます。 そのためには、Visual Basic では `ReadOnly` キーワードと `WriteOnly` キーワードを使用します。 ただし、自動実装プロパティを読み取り専用または書き込み専用にすることはできません。

詳細については次を参照してください:

- [Property ステートメント](../../language-reference/statements/property-statement.md)
- [Get ステートメント](../../language-reference/statements/get-statement.md)
- [Set ステートメント](../../language-reference/statements/set-statement.md)
- [ReadOnly](../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>メソッド

 "*メソッド*" は、オブジェクトが実行できる処理です。

> [!NOTE]
> Visual Basic には、メソッドを作成する方法が 2 つあります。メソッドが値を返さない場合は `Sub` ステートメントを使用し、メソッドが値を返す場合は `Function` ステートメントを使用します。

クラスのメソッドを定義するコード例を次に示します。

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

クラスには、同じメソッドに対して、パラメーターの数やパラメーターの型が異なる複数の実装 ("*オーバーロード*") を含めることができます。

メソッドをオーバーロードするコード例を次に示します。

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

ほとんどの場合、メソッドはクラス定義内で宣言します。 ただし、Visual Basic では、既存のクラスの実際の定義の外部にメソッドを追加できる "*拡張メソッド*" がサポートされています。

詳細については次を参照してください:

- [Function ステートメント](../../language-reference/statements/function-statement.md)
- [Sub ステートメント](../../language-reference/statements/sub-statement.md)
- [Overloads](../../language-reference/modifiers/overloads.md)
- [拡張メソッド](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>コンストラクター

コンストラクターは、特定の型のオブジェクトを作成するときに自動的に実行されるクラス メソッドです。 コンストラクターは、通常、新しいオブジェクトのデータ メンバーを初期化します。 コンストラクターは、クラスの作成時に 1 回だけ実行できます。 また、コンストラクター内のコードは常に、クラス内の他のすべてのコードより先に実行されます。 他のメソッドと同じように、コンストラクターにも複数のオーバーロードを作成できます。

クラスのコンストラクターを定義するコード例を次に示します。

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

詳細については次を参照してください:[オブジェクトの有効期間: オブジェクトの作成と破棄](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

#### <a name="destructors"></a>デストラクター

デストラクターは、クラスのインスタンスを消滅させるために使用します。 .NET Framework では、アプリケーション内のマネージド オブジェクトのメモリの割り当てと解放は、ガベージ コレクターによって自動的に管理されます。 ただし、アプリケーションで作成されるアンマネージ リソースを適切にクリーンアップするために、デストラクターも必要になることがあります。 1 つのクラスに定義できるデストラクターは 1 つだけです。

.NET Framework のデストラクターおよびガベージ コレクションの詳細については、「[ガベージ コレクション](../../../standard/garbage-collection/index.md)」をご覧ください。

#### <a name="events"></a>イベント

クラスやオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。 イベントを送信する (発生させる) クラスは "*パブリッシャー*" と呼ばれ、イベントを受信する (処理する) クラスは "*サブスクライバー*" と呼ばれます。 イベント、およびイベントの発生と処理の詳細については、「[イベント](../../../standard/events/index.md)」をご覧ください。

- イベントを宣言するには、[Event ステートメント](../../language-reference/statements/event-statement.md)を使用します。

- イベントを発生させるには、[RaiseEvent ステートメント](../../language-reference/statements/raiseevent-statement.md)を使用します。

- 宣言によってイベント ハンドラーを指定するには、[WithEvents](../../language-reference/modifiers/withevents.md) ステートメントと [Handles](../../language-reference/statements/handles-clause.md) 句を使用します。

- イベントに関連付けるイベント ハンドラーを動的に追加、削除、変更できるようにするには、[AddHandler ステートメント](../../language-reference/statements/addhandler-statement.md)と [RemoveHandler ステートメント](../../language-reference/statements/removehandler-statement.md)に [AddressOf 演算子](../../language-reference/operators/addressof-operator.md)を組み合わせて使用します。

#### <a name="nested-classes"></a>入れ子になったクラス

別のクラス内で定義されているクラスを "*入れ子になったクラス*" と呼びます。 既定では、入れ子になったクラスはプライベートです。

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

入れ子になったクラスのインスタンスを作成するには、コンテナー クラスの名前に続けて、ドットと入れ子になったクラスの名前を指定します。

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>アクセス修飾子とアクセス レベル

すべてのクラスおよびクラス メンバーでは、"*アクセス修飾子*" を使って、他のクラスに提供するアクセス レベルを指定できます。

次のアクセス修飾子を使用できます。

|Visual Basic の修飾子|定義|
|---------------------------|----------------|
|[Public](../../language-reference/modifiers/public.md)|この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。|
|[Private](../../language-reference/modifiers/private.md)|この型またはメンバーには、同じクラスのコードのみがアクセスできます。|
|[Protected](../../language-reference/modifiers/protected.md)|この型またはメンバーには、同じクラスまたは派生クラスのコードのみがアクセスできます。|
|[Friend](../../language-reference/modifiers/friend.md)|この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。|
|`Protected Friend`|この型またはメンバーには、同じアセンブリ内の任意のコード、または別のアセンブリ内の任意の派生クラスからアクセスできます。|

詳しくは、「[Visual Basic でのアクセス レベル](../language-features/declared-elements/access-levels.md)」を参照してください。

### <a name="instantiating-classes"></a>クラスのインスタンス化

オブジェクトを作成するには、クラスをインスタンス化する (クラスのインスタンスを作成する) 必要があります。

```vb
Dim sampleObject as New SampleClass()
```

クラスをインスタンス化した後は、インスタンスのプロパティやフィールドに値を割り当てたり、クラスのメソッドを呼び出したりできます。

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

クラスのインスタンス化のプロセスでプロパティに値を割り当てるには、オブジェクト初期化子を使用します。

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

詳細については次を参照してください:

- [New 演算子](../../language-reference/operators/new-operator.md)
- [オブジェクト初期化子: 名前付きの型と匿名型](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>共有クラスおよびメンバー

 クラスの共有メンバーは、クラスのすべてのインスタンスで共有されるプロパティ、プロシージャ、またはフィールドです。

 共有メンバーを定義するコード例を次に示します。

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 共有メンバーにアクセスするには、クラスのオブジェクトを作成せずにクラスの名前を使います。

```vb
MsgBox(SampleClass.SampleString)
```

 Visual Basic の共有モジュールには共有メンバーだけが含まれ、これらをインスタンス化することはできません。 また、共有メンバーから、非共有のプロパティ、フィールド、またはメソッドにアクセスすることもできません。

 詳細については次を参照してください:

- [Shared](../../language-reference/modifiers/shared.md)
- [Module ステートメント](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>匿名型

匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。 クラスは、コンパイラによって生成されます。 このクラスには使用可能な名前がなく、オブジェクトの宣言時に指定したプロパティが格納されます。

匿名型のインスタンスを作成するコード例を次に示します。

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

詳細については次を参照してください:[匿名型](../language-features/objects-and-classes/anonymous-types.md)。

## <a name="inheritance"></a>継承

継承を使用すると、他のクラスで定義されている動作を再利用、拡張、および変更する新しいクラスを作成できます。 メンバーが継承される側のクラスを "*基底クラス*" と呼び、メンバーを継承する側のクラスを "*派生クラス*" と呼びます。 ただし、Visual Basic のすべてのクラスは、.NET のクラス階層構造をサポートしてすべてのクラスに下位レベルのサービスを提供する <xref:System.Object> クラスを暗黙的に継承します。

> [!NOTE]
> Visual Basic は多重継承をサポートしていません。 つまり、派生クラスに対して指定できる基底クラスは 1 つだけです。

基底クラスを継承するコード例を次に示します。

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

既定では、すべてのクラスが継承可能になります。 ただし、クラスを基底クラスとして使用できないように指定したり、基底クラスとしてのみ使用できるクラスを作成したりできます。

クラスを基底クラスとして使用できないように指定する方法を次に示します。

```vb
NotInheritable Class SampleClass
End Class
```

クラスが基底クラスとしてのみ使用され、インスタンス化できないように指定する方法を次に示します。

```vb
MustInherit Class BaseClass
End Class
```

詳細については次を参照してください:

- [Inherits ステートメント](../../language-reference/statements/inherits-statement.md)
- [NotInheritable](../../language-reference/modifiers/notinheritable.md)
- [MustInherit](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>メンバーのオーバーライド

既定では、派生クラスは基底クラスのすべてのメンバーを継承します。 継承したメンバーの動作を変更する場合は、そのメンバーをオーバーライドする必要があります。 つまり、派生クラスに、メソッド、プロパティ、またはイベントの新しい実装を定義できます。

プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。

|Visual Basic の修飾子|定義|
|---------------------------|----------------|
|[Overridable](../../language-reference/modifiers/overridable.md)|派生クラスでのクラス メンバーのオーバーライドを許可します。|
|[Overrides](../../language-reference/modifiers/overrides.md)|基底クラスで定義されている仮想メンバー (オーバーライドできるメンバー) をオーバーライドします。|
|[NotOverridable](../../language-reference/modifiers/notoverridable.md)|継承するクラスでのメンバーのオーバーライドを禁止します。|
|[MustOverride](../../language-reference/modifiers/mustoverride.md)|派生クラスでのクラス メンバーのオーバーライドを必須にします。|
|[Shadows](../../language-reference/modifiers/shadows.md)|基底クラスから継承されたメンバーを隠ぺいします。|

## <a name="interfaces"></a>インターフェイス

インターフェイスは、クラスと同様にプロパティ、メソッド、およびイベントのセットを定義します。 ただし、クラスとは異なり、インターフェイスは実装を提供しません。 インターフェイスはクラスによって実装され、クラスとは別のエンティティとして定義されます。 インターフェイスを実装するクラスは、そのインターフェイスのあらゆる機能を定義に従って厳密に実装する必要があります。この点で、インターフェイスはコントラクトを表しています。

インターフェイスを定義するコード例を次に示します。

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

クラスにインターフェイスを実装するコード例を次に示します。

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

詳細については次を参照してください:

- [インターフェイス](../language-features/interfaces/index.md)
- [Interface ステートメント](../../language-reference/statements/interface-statement.md)
- [Implements ステートメント](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a>ジェネリック

.NET のクラス、構造体、インターフェイス、およびメソッドは、格納または使用できるオブジェクトの型を定義する "*型パラメーター*" を含むことができます。 ジェネリックの最も一般的な例として、コレクションがあります。コレクションには、その中に格納されるオブジェクトの型を指定できます。

ジェネリック クラスを定義するコード例を次に示します。

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

ジェネリック クラスのインスタンスを作成するコード例を次に示します。

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

詳細については次を参照してください:

- [ジェネリック](../../../standard/generics/index.md)
- [Generic Types in Visual Basic](../language-features/data-types/generic-types.md)

## <a name="delegates"></a>デリゲート

 "*デリゲート*" は、メソッド シグネチャを定義する型であり、互換性のあるシグネチャを持つ任意のメソッドへの参照を提供できます。 メソッドは、デリゲートを使用して起動する (呼び出す) ことができます。 デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。

> [!NOTE]
> イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。 デリゲートを使用したイベント処理について詳しくは、「[イベント](../../../standard/events/index.md)」をご覧ください。

デリゲートを作成するコード例を次に示します。

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

デリゲートで指定されたシグネチャに一致するメソッドへの参照を作成するコード例を次に示します。

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

詳細については次を参照してください:

- [デリゲート](../language-features/delegates/index.md)
- [Delegate ステートメント](../../language-reference/statements/delegate-statement.md)
- [AddressOf 演算子](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>関連項目

- [Visual Basic プログラミング ガイド](../index.md)
