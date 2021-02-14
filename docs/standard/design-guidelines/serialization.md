---
description: '詳細情報: シリアル化'
title: シリアル化
ms.date: 10/22/2008
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: a12163c01da2f9eed19de05b0434c02d05ca99b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713300"
---
# <a name="serialization"></a>シリアル化

シリアル化とは、簡単に永続化または転送できる形式にオブジェクトを変換するプロセスのことです。 たとえば、オブジェクトをシリアル化し、HTTP を使用してインターネット経由で転送して、転送先のコンピューターで逆シリアル化することができます。

 .NET Framework には、さまざまなシリアル化シナリオに合わせて最適化できる 3 つの主なシリアル化テクノロジがあります。 これらのテクノロジ、およびテクノロジに関連した主な Framework 型を次の表に示します。

|**テクノロジ名**|**主要な型**|**シナリオ**|
|-------------------------|--------------------|-------------------|
|**データ コントラクトのシリアル化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|永続化全般<br />Web サービス<br />JSON|
|**XML シリアル化**|<xref:System.Xml.Serialization.XmlSerializer>|XML の構造を完全に制御する XML 形式|
|**ランタイム シリアル化 (バイナリおよび SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET リモート処理|

 ✔️ 新しい型を設計するときは、シリアル化について考えます。

## <a name="choosing-the-right-serialization-technology-to-support"></a>サポートする適切なシリアル化テクノロジの選択

 ✔️ 型のインスタンスを Web サービスで永続化または使用する必要がある場合は、データ コントラクトのシリアル化をサポートすることを検討します。

 ✔️ 型をシリアル化するときに作成される XML 形式の制御を強化する必要がある場合は、データ コントラクトのシリアル化の代わり、またはそれに加えて、XML シリアル化をサポートすることを検討します。

 これは、たとえば XML 属性を作成するために、データ コントラクトのシリアル化ではサポートされていない XML コンストラクトを使用する必要がある一部の相互運用性シナリオで、必要になることがあります。

 ✔️ 型のインスタンスが .NET リモート処理の境界を超えて移動する必要がある場合は、ランタイムのシリアル化をサポートすることを検討します。

 ❌ 一般的な永続化のために、ランタイムのシリアル化や XML のシリアル化をサポートしないでください。 代わりに、データ コントラクトのシリアル化を使用してください。

## <a name="supporting-data-contract-serialization"></a>データ コントラクトのシリアル化のサポート

 <xref:System.Runtime.Serialization.DataContractAttribute> を型に適用し、<xref:System.Runtime.Serialization.DataMemberAttribute> をその型のメンバー (フィールドおよびプロパティ) に適用することによって、型でデータ コントラクトのシリアル化をサポートすることができます。

 ✔️ 型を部分信頼で使用できる場合は、型のデータ メンバーをパブリックにすることを検討します。

 完全な信頼では、データ コントラクト シリアライザーで非パブリックの型とメンバーをシリアル化および逆シリアル化できますが、部分信頼の場合は、パブリック メンバーのみをシリアル化および逆シリアル化できます。

 ✔️ <xref:System.Runtime.Serialization.DataMemberAttribute> を持つすべてのプロパティで、ゲッターとセッターを実装します。 データ コントラクト シリアライザーにより、この型のゲッターとセッターの両方がシリアル化可能と見なされる必要があります。 (.NET Framework 3.5 SP1 では、一部のコレクション プロパティを取得専用にすることができます)。型を部分信頼で使用しない場合は、1 つまたは両方のプロパティ アクセサーを非パブリックにできます。

 ✔️ 逆シリアル化されたインスタンスの初期化には、シリアル化コールバックを使用することを検討します。

 オブジェクトの逆シリアル化時にはコンストラクターは呼び出されません。 (このルールには例外があります。 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> でマークされたコレクションのコンストラクターは、逆シリアル化の間に呼び出されます)。このため、通常の構築時に実行されるすべてのロジックを、シリアル化コールバックの 1 つとして実装する必要があります。

 `OnDeserializedAttribute` は最もよく使用されるコールバック属性です。 その他の属性には、<xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute>、および <xref:System.Runtime.Serialization.OnSerializedAttribute> があります。 これらを使用して、逆シリアル化前、シリアル化前、およびシリアル化後に実行されるコールバックをマークすることができます。

 ✔️ 複雑なオブジェクト グラフを逆シリアル化する場合は、<xref:System.Runtime.Serialization.KnownTypeAttribute> を使用して、使用する必要がある具象型を示すことを検討します。

 ✔️ シリアル化可能な型を作成または変更するときは、下位互換性と上位互換性を考慮します。

 シリアル化した型の将来のバージョンは、現在のバージョンの型に逆シリアル化でき、その逆も可能であることを念頭に置いてください。

 明示的なパラメーターを使用してデータ コントラクト属性にコントラクトを保存する特別な措置を取らない限り、データ メンバーはプライベートで内部データであっても、型の将来のバージョンで名前、型、順序を変更することはできないことを理解しておいてください。

 シリアル化可能な型を変更するときは、シリアル化の互換性をテストします。 新しいバージョンを古いバージョンに逆シリアル化したり、その逆も試してみてください。

 ✔️ 異なるバージョンの型の間でラウンドトリッピングができるように、<xref:System.Runtime.Serialization.IExtensibleDataObject> を実装することを検討します。

 インターフェイスを使用すると、ラウンドトリッピングの間にデータが失われないようにシリアライザーで確認することができます。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> プロパティは、現在のバージョンでは未知である、将来のバージョンの型のデータを格納するために使用されるため、そのデータ メンバーにはそれを格納できません。 現在のバージョンを、後で将来のバージョンにシリアル化または逆シリアル化するときに、シリアル化されたストリームで追加データを使用できます。

## <a name="supporting-xml-serialization"></a>XML シリアル化のサポート

 データ コントラクトのシリアル化は .NET Framework の主な (既定の) シリアル化テクノロジですが、データ コントラクトのシリアル化ではサポートされないシリアル化シナリオがあります。 たとえば、シリアライザーによって作成または使用された XML の形状は完全に制御できません。 そのような微調整が必要な場合は、XML シリアル化を使用する必要があり、このシリアル化テクノロジをサポートするように型を設計する必要があります。

 ❌ 作成された XML の形状を制御しなければならない強力な理由がない限り、XML シリアル化のために特別に型を設計することは避けてください。 このシリアル化テクノロジは、前のセクションで説明したデータ コントラクトのシリアル化よりも優先されます。

 ✔️ XML シリアル化属性を適用することで提供されるものより細かく、シリアル化された XML の形状を制御する必要がある場合は、<xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装することを検討します。 2 つのインターフェイスのメソッド、<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> と <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> を使用することで、シリアル化された XML ストリームを完全制御できます。 また、`XmlSchemaProviderAttribute` を適用することで、その型用に生成される XML スキーマを制御することもできます。

## <a name="supporting-runtime-serialization"></a>ランタイム シリアル化のサポート

 ランタイム シリアル化は、.NET リモート処理で使用されるテクノロジです。 .NET リモート処理を使用して型が転送されると考えられる場合は、ランタイム シリアル化をサポートする必要があります。

 ランタイム シリアル化の基本的なサポートは、<xref:System.SerializableAttribute> を適用することで提供でき、より高度なシナリオでは、単純なランタイム シリアル化可能パターンの実装が必要になります (<xref:System.Runtime.Serialization.ISerializable> を実装してシリアル化コンストラクターを提供します)。

 ✔️ 型が .NET リモート処理で使用される場合は、ランタイム シリアル化をサポートすることを検討します。 たとえば、<xref:System.AddIn?displayProperty=nameWithType> 名前空間では .NET リモート処理が使用されるため、`System.AddIn` アドインの間で交換されるすべての型で、ランタイム シリアル化をサポートする必要があります。

 ✔️ シリアル化プロセスを完全に制御する必要がある場合は、ランタイム シリアル化可能パターンを実装することを検討します。 たとえば、シリアル化または逆シリアル化されたデータを変換したいとします。

 パターンは単純です。 必要な作業は、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装し、オブジェクトを逆シリアル化するときに使用する特別なコンストラクターを指定するだけです。

 ✔️ このサンプルで示されているように、シリアル化コンストラクターを保護し、型と名前を厳密に指定した 2 つのパラメーターを提供します。

```csharp
[Serializable]
public class Person : ISerializable
{
    protected Person(SerializationInfo info, StreamingContext context)
    {
        // ...
    }
}
```

 ✔️ <xref:System.Runtime.Serialization.ISerializable> メンバーを明示的に実装します。

 ✔️ <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> の実装にはリンク確認要求を適用します。 こうすることで、完全に信頼できるコアとランタイム シリアライザーだけが、メンバーにアクセスできるようになります。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](index.md)
- [使用方法のガイドライン](usage-guidelines.md)
