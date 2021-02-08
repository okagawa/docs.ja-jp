---
description: '詳細情報: 相互運用可能なオブジェクト参照'
title: 相互運用可能なオブジェクト参照
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 27c801fb3954c7ea3f821a6588a2229502702989
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802685"
---
# <a name="interoperable-object-references"></a>相互運用可能なオブジェクト参照

既定では、は <xref:System.Runtime.Serialization.DataContractSerializer> 値によってオブジェクトをシリアル化します。 プロパティを使用すると、オブジェクトをシリアル化する <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> ときにオブジェクト参照を保持するようにデータコントラクトシリアライザーに指示できます。  
  
## <a name="generated-xml"></a>生成される XML  

 例として、次のオブジェクトを考えます。  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass
{  
}  
```  
  
 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `false` (既定値) に設定すると、次の XML が生成されます。  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `true` に設定すると、次の XML が生成されます。  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 ただし、では、 <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` `ref` `preserveObjectReferences` プロパティがに設定されている場合でも、スキーマの属性と属性が記述されていません `true` 。  
  
## <a name="using-isreference"></a>IsReference の使用  

 記述されたスキーマに従って有効なオブジェクト参照情報を生成するには、 <xref:System.Runtime.Serialization.DataContractAttribute> 属性を型に適用し、 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> フラグをに設定し `true` ます。 次の例では、 `X` 前の例でを追加してクラスを変更し `IsReference` ます。  
  
```csharp
[DataContract(IsReference=true)]
public class X
{  
     SomeClass someInstance = new SomeClass();
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember]
     public SomeClass B = someInstance;
}
  
public class SomeClass
{
}  
````

 次のような XML が生成されます。  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 `IsReference` を使用すると、メッセージのラウンド トリップに対応できます。 このメソッドを使用しない場合、スキーマから型が生成されるときに、その型の XML 出力は、最初に想定したスキーマと必ずしも互換性がありません。 つまり、`id` 属性と `ref` 属性がシリアル化されたとしても、元のスキーマによってこれらの属性 (またはすべての属性) が拒否される可能性があります。 `IsReference`データメンバーに適用されると、ラウンドトリップ時にメンバーは引き続き *参照可能* として認識されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
