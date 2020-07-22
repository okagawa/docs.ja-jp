---
title: <Namespace>要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180963"
---
# <a name="namespace-element-net-native"></a>\<Namespace>要素 (.NET ネイティブ)
指定した名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Namespace Name="namespace_name"
           Activate="policy_type"
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|Description|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 名前空間の名前を指定します。|  
|`Activate`|リフレクション|省略可能な属性です。 コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。|  
|`Browse`|リフレクション|省略可能な属性です。 プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。|  
|`Dynamic`|リフレクション|省略可能な属性です。 コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。|  
|`Serialize`|シリアル化|省略可能な属性です。 コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。|  
|`DataContractSerializer`|シリアル化|省略可能な属性です。 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。|  
|`DataContractJsonSerializer`|シリアル化|省略可能な属性です。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。|  
|`XmlSerializer`|シリアル化|省略可能な属性です。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。|  
|`MarshalObject`|Interop|省略可能な属性です。 Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。|  
|`MarshalDelegate`|Interop|省略可能な属性です。 ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。|  
|`MarshalStructure`|Interop|省略可能な属性です。 ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|値|[説明]|  
|-----------|-----------------|  
|*namespace_name*|名前空間の名前。 \<Namespace>要素が、、または要素の子である場合 [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) [\<Assembly>](assembly-element-net-native.md) 、 *namespace_name*は完全修飾名前空間名である必要があります。 \<Namespace>要素が別の要素の子である場合 \<Namespace> 、 *namespace_name*は相対名前空間名である必要があります。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|値|[説明]|  
|-----------|-----------------|  
|*policy_setting*|名前空間内のすべての型について、このポリシーの種類に適用する設定です。 指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`<Namespace>`|親名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。|  
|[\<Type>](type-element-net-native.md)|型にリフレクション ポリシーを適用します。|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|構築されたジェネリック型にリフレクション ポリシーを適用します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。 要素には、 [\<Application>](application-element-net-native.md) 0 個以上の要素を含めることができ [\<Assembly>](assembly-element-net-native.md) ます。|  
|[\<Assembly>](assembly-element-net-native.md)|指定したアセンブリ内のすべての型にランタイム リフレクション ポリシーを適用します。|  
|[\<Library>](library-element-net-native.md)|実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。 要素には、 [\<Library>](library-element-net-native.md) 0 個または1個の要素を含めることができ [\<Assembly>](assembly-element-net-native.md) ます。|  
|`<Namespace>`|親名前空間内のすべての型にリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>解説  
 `Activate` 属性、`Browse` 属性、`Dynamic`、および `Serialize` 属性はすべて省略可能です。 いずれも存在しない場合、`<Namespace>` 要素は子要素のコンテナーとしてのみ機能します。 存在する場合は、`<Namespace>` 要素は、指定された名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。  
  
 要素の子である場合 [\<Assembly>](assembly-element-net-native.md) 、要素は、 `<Namespace>` 要素によって定義されたランタイムリフレクションポリシーをオーバーライドし [\<Assembly>](assembly-element-net-native.md) ます。  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ ポリシーの設定](runtime-directive-policy-settings.md)
- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](runtime-directive-elements.md)
