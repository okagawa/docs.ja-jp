---
title: <Library>要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128364"
---
# <a name="library-element-net-native"></a>\<Library>要素 (.NET ネイティブ)
実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。  
  
 \<Directives> 要素  
\<Library> 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須の属性です。 アセンブリの名前を指定します。 この `<Library>` 要素の子要素によって、このアセンブリ内にある型と型のメンバーのランタイム リフレクション ポリシーが定義されます。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|値|Description|  
|-----------|-----------------|  
|*assembly_name*|ファイル拡張子のないアセンブリの簡易名です。 この属性は、<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> プロパティに対応します。 たとえば、Extensions.dll というアセンブリの名前は "Extensions" です。 アセンブリのメタデータの条件付きインクルードをサポートする特殊な形式の *assembly_name* については、「解説」セクションを参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|Description|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|特定のアセンブリ内のすべての型にポリシーを適用します。|  
|[\<Namespace>](namespace-element-net-native.md)|特定の名前空間内のすべての型にポリシーを適用します。|  
|[\<Type>](type-element-net-native.md)|クラスや構造体などの特定の型にポリシーを適用します。|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|構築されたジェネリック型にポリシーを適用します。 たとえば、要素を [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 使用して、型のポリシーを定義することができ `List<String>` ます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|Description|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|ランタイム ディレクティブ ファイルのルート要素です。|  
  
## <a name="remarks"></a>解説  
 要素には、 [\<Directives>](directives-element-net-native.md) 0 個以上の要素を含めることができ `<Library>` ます。  
  
 `<Library>` 要素は、実行時に必要なメタデータを持つプログラム要素を定義するためのコンテナーとして機能します。この要素はポリシーを表しません。 コンパイル時に、コンパイラ ツールは `<Library>` 要素により指定されたライブラリでのみ、その子要素により示されるプログラム要素を検索します。 これに対して、コンパイラツールは、要素の子要素によって識別されるプログラム要素のすべてのライブラリ (including.NET Framework core ライブラリ) を検索し [\<Application>](application-element-net-native.md) ます。  
  
 `<Library>` ディレクティブは、条件付きで使用される場合があります。 要素の名前の `<Library>` 先頭と末尾がアスタリスク () の場合 \* 、このディレクティブは、 `<Library>` アスタリスクによって指定されたアセンブリがアプリによって参照されている場合にのみ効果があります。 たとえば、次のランタイムディレクティブは、ユーティリティ .dll アセンブリがアプリによって参照されている場合にのみ適用されます。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>関連項目

- [\<Application>Element](application-element-net-native.md)
- [\<Directives>Element](directives-element-net-native.md)
- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](runtime-directive-elements.md)
