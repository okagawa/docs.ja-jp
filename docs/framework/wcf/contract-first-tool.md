---
description: '詳細情報: Contract-First ツール'
title: コントラクト優先ツール
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 6455fa866afd440e70062f8433356b13fe163a8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736402"
---
# <a name="contract-first-tool"></a>コントラクト優先ツール

サービス コントラクトは、多くの場合、既存のサービスから作成する必要があります。 .NET Framework 4.5 以降では、コントラクト優先ツールを使用して、既存のサービスからデータコントラクトクラスを自動的に作成できます。 コントラクト優先ツールを使用するには、XML スキーマ定義ファイル (XSD) をローカルにダウンロードする必要があります。ツールは、HTTP 経由でリモート データ コントラクトをインポートすることはできません。

 コントラクト優先ツールは、ビルドタスクとして Visual Studio 2012 に統合されています。 ビルド タスクによって生成されるコード ファイルは、基になるサービス コントラクトの変更をプロジェクトが簡単に取り込むことができるように、プロジェクトがビルドされるたびに作成されます。

 コントラクト優先ツールがインポートできるスキーマ型には、次のようなものがあります。

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 単純型は、`Int16` または `String` のようなプリミティブである場合は生成されません。複合型は、`Collection` 型である場合は生成されません。 他の `xsd:complexType` の一部である型も、生成されません。 これらのすべての場合に、型はプロジェクト内の既存の型を参照するようになります。

## <a name="adding-a-data-contract-to-a-project"></a>プロジェクトへのデータ コントラクトの追加

 コントラクト優先ツールを使用する前に、サービス コントラクト (XSD) をプロジェクトに追加する必要があります。 この概要説明では、コントラクト優先機能を示すために、次のコントラクトを使用します。 このサービス定義は、Bing の検索 API で使用されるサービスコントラクトの小さなサブセットです。

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema id="ServiceSchema"
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"
    elementFormDefault="qualified"
    xmlns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
>
  <xs:complexType name="SearchRequest">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="WebSearchOption">
    <xs:restriction base="xs:string">
      <xs:enumeration value="DisableHostCollapsing" />
      <xs:enumeration value="DisableQueryAlterations" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

 上記のサービスコントラクトをプロジェクトに追加するには、プロジェクトを右クリックし、[ **新規追加**] をクリックします。 [テンプレート] ダイアログ ボックスの [WCF] ペインで [スキーマ定義] を選択し、新しいファイルの名前を SampleContract.xsd にします。 上のコードをコピーし、新しいファイルのコード ビューに貼り付けます。

## <a name="configuring-contract-first-options"></a>コントラクト優先のオプションの構成

 コントラクト優先のオプションは、WCF プロジェクトの [プロパティ] メニューで構成できます。 コントラクト優先の開発を有効にするには、プロジェクトのプロパティウィンドウの WCF ページで [ **XSD を型定義言語として有効に** する] チェックボックスをオンにします。

 ![コントラクト優先の開発が有効になっている WCF オプションのスクリーンショット。](./media/contract-first-tool/contract-first-options.png)

 高度なプロパティを構成するには、[詳細設定] をクリックします。

 ![[コントラクトコード生成の詳細設定] ダイアログボックス。](./media/contract-first-tool/advanced-contract-settings.png)

 次の詳細設定は、コントラクトからコードを生成するために構成できます。 設定は、プロジェクト内のすべてのファイルに対してのみ構成できます。現時点では、ファイルごとの構成はできません。

- **シリアライザーモード**: この設定は、サービスコントラクトファイルの読み取りに使用されるシリアライザーを決定します。 [ **XML シリアライザー** ] を選択すると、[ **コレクションの種類** ] オプションと [ **型の再利用** ] オプションは無効になります。 これらのオプションは、 **データコントラクトシリアライザー** にのみ適用されます。

- **型の再利用**: この設定では、型の再利用に使用するライブラリを指定します。 この設定は、 **シリアライザーモード** が **データコントラクトシリアライザー** に設定されている場合にのみ適用されます。

- **コレクションの種類**: この設定は、コレクションのデータ型に使用する完全修飾型またはアセンブリ修飾型を指定します。 この設定は、 **シリアライザーモード** が **データコントラクトシリアライザー** に設定されている場合にのみ適用されます。

- [**ディクショナリの種類**]: この設定では、ディクショナリデータ型に使用する完全修飾型またはアセンブリ修飾型を指定します。

- **Enabledatabinding**: この設定は、 <xref:System.ComponentModel.INotifyPropertyChanged> データバインディングを実装するために、すべてのデータ型にインターフェイスを実装するかどうかを指定します。

- **ExcludedTypes**: この設定は、参照されたアセンブリから除外する完全修飾型またはアセンブリ修飾型のリストを指定します。 この設定は、 **シリアライザーモード** が **データコントラクトシリアライザー** に設定されている場合にのみ適用されます。

- **Generateinternaltypes**: 内部としてマークされているクラスを生成するかどうかを指定します。 この設定は、 **シリアライザーモード** が **データコントラクトシリアライザー** に設定されている場合にのみ適用されます。

- [生成された **型**]: この設定は、属性を使用してクラスを生成するかどうかを指定し <xref:System.SerializableAttribute> ます。 この設定は、 **シリアライザーモード** が **データコントラクトシリアライザー** に設定されている場合にのみ適用されます。

- **Importxmltypes**: この設定では、属性を <xref:System.SerializableAttribute> 持たないクラスに属性を適用するようにデータコントラクトシリアライザーを構成するかどうかを指定し <xref:System.Runtime.Serialization.DataContractAttribute> ます。  この設定は、 **シリアライザーモード** が **データコントラクトシリアライザー** に設定されている場合にのみ適用されます。

- **SupportFx35TypedDataSets**: この設定は、.NET Framework 3.5 用に作成された型指定されたデータセットに対して追加の機能を提供するかどうかを指定します。 **シリアライザーモード** が **xml シリアライザー** に設定されている場合、 <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> この値が True に設定されていると、xml スキーマインポーターに拡張機能が追加されます。 **シリアライザーモード** が [**データコントラクトシリアライザー**] に設定されている場合、 <xref:System.DateTimeOffset> この値が False に設定されている場合、型は参照から除外されるので、は <xref:System.DateTimeOffset> 古いバージョンの framework に対して常に生成されます。

- **Inputxsdfiles**: この設定では、入力ファイルの一覧を指定します。 各ファイルは、有効な XML スキーマを含んでいる必要があります。

- **Language**: この設定は、生成されるコントラクトコードの言語を指定します。 設定は、<xref:System.CodeDom.Compiler.CodeDomProvider> が認識できるものである必要があります。

- **NamespaceMappings**: この設定は、XSD ターゲット名前空間から CLR 名前空間へのマッピングを指定します。 各マッピングは、次の形式を使用する必要があります。

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     XML シリアライザーは、次の形式の 1 つのマッピングだけを受け取ります。

    ```xml
    "*, CLR Namespace"
    ```

- **Outputdirectory**: この設定は、コードファイルが生成されるディレクトリを指定します。

 設定は、プロジェクトのビルド時に、サービス コントラクト ファイルからサービス コントラクト型を生成するために使用されます。

## <a name="using-contract-first-development"></a>コントラクト優先の開発の使用

 サービスコントラクトをプロジェクトに追加し、ビルド設定を確認したら、 **F6** キーを押してプロジェクトをビルドします。 これで、サービス コントラクトで定義された型が、プロジェクト内で利用できるようになります。

 サービス コントラクトで定義した型を使用するには、現在の名前空間に `ContractTypes` への参照を追加します。

```csharp
using MyProjectNamespace.ContractTypes;
```

 次に示すように、サービスコントラクトで定義されている型は、プロジェクトで解決できるようになります。

 ![最初の数文字を入力した後に IntelliSense で表示される SearchRequest クラス。](./media/contract-first-tool/service-contract-types.png)

 ツールによって生成された型は、GeneratedXSDTypes.cs ファイル内に作成されます。 ファイルは、 \<project directory> 既定では/obj//XSDGeneratedCode/ディレクトリに作成され \<build configuration> ます。 この記事の冒頭にあるサンプルスキーマは、次のように変換されます。

```csharp
//------------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by a tool.
//     Runtime Version:4.0.30319.17330
//
//     Changes to this file may cause incorrect behavior and will be lost if
//     the code is regenerated.
// </auto-generated>
//------------------------------------------------------------------------------

namespace TestXSD3.ContractTypes
{
    using System.Xml.Serialization;

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Diagnostics.DebuggerStepThroughAttribute()]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]
    public partial class SearchRequest
    {

        private string versionField;

        private string marketField;

        private string uILanguageField;

        private string queryField;

        private string appIdField;

        private double latitudeField;

        private bool latitudeFieldSpecified;

        private double longitudeField;

        private bool longitudeFieldSpecified;

        private double radiusField;

        private bool radiusFieldSpecified;

        public SearchRequest()
        {
            this.versionField = "2.2";
        }

        /// <remarks/>
        [System.ComponentModel.DefaultValueAttribute("2.2")]
        public string Version
        {
            get
            {
                return this.versionField;
            }
            set
            {
                this.versionField = value;
            }
        }

        /// <remarks/>
        public string Market
        {
            get
            {
                return this.marketField;
            }
            set
            {
                this.marketField = value;
            }
        }

        /// <remarks/>
        public string UILanguage
        {
            get
            {
                return this.uILanguageField;
            }
            set
            {
                this.uILanguageField = value;
            }
        }

        /// <remarks/>
        public string Query
        {
            get
            {
                return this.queryField;
            }
            set
            {
                this.queryField = value;
            }
        }

        /// <remarks/>
        public string AppId
        {
            get
            {
                return this.appIdField;
            }
            set
            {
                this.appIdField = value;
            }
        }

        /// <remarks/>
        public double Latitude
        {
            get
            {
                return this.latitudeField;
            }
            set
            {
                this.latitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LatitudeSpecified
        {
            get
            {
                return this.latitudeFieldSpecified;
            }
            set
            {
                this.latitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Longitude
        {
            get
            {
                return this.longitudeField;
            }
            set
            {
                this.longitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LongitudeSpecified
        {
            get
            {
                return this.longitudeFieldSpecified;
            }
            set
            {
                this.longitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Radius
        {
            get
            {
                return this.radiusField;
            }
            set
            {
                this.radiusField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool RadiusSpecified
        {
            get
            {
                return this.radiusFieldSpecified;
            }
            set
            {
                this.radiusFieldSpecified = value;
            }
        }
    }

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]
    public enum WebSearchOption
    {

        /// <remarks/>
        DisableHostCollapsing,

        /// <remarks/>
        DisableQueryAlterations,
    }
}
```

## <a name="errors-and-warnings"></a>エラーと警告

 XSD スキーマの解析中に発生したエラーと警告は、ビルドのエラーと警告として表示されます。

## <a name="interface-inheritance"></a>インターフェイスの継承

 コントラクト優先の開発でインターフェイスの継承を使用することはできません。これは、他の操作におけるインターフェイスの動作と一致しています。 基底インターフェイスを継承するインターフェイスを使用するには、2 つの別個のエンドポイントを使用します。 最初のエンドポイントは継承されるコントラクトを使用し、2 番目のエンドポイントは基底インターフェイスを実装します。
