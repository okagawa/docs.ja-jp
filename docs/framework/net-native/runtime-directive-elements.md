---
title: ランタイム ディレクティブ要素
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128170"
---
# <a name="runtime-directive-elements"></a>ランタイム ディレクティブ要素
ランタイム ディレクティブ (rd.xml) ファイル形式は、次のランタイム ディレクティブ要素をサポートします。 階層表現については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。  
  
 [\<Application>](application-element-net-native.md)  
 アプリで使用されるすべての型にランタイム リフレクション ポリシーを適用し、実行時にリフレクションに使用できるメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。 これは要素の子です [\<Directives>](directives-element-net-native.md) 。  
  
 [\<Assembly>](assembly-element-net-native.md)  
 アセンブリ内のすべての型に実行時ポリシーを適用します。 これは、 [\<Application>](application-element-net-native.md) 要素と要素の子です [\<Library>](library-element-net-native.md) 。  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 それを含む [\<Type>](type-element-net-native.md) ディレクティブが属性の場合、は、その属性が適用されるコード要素に実行時ポリシーを適用します。  
  
 [\<Directives>](directives-element-net-native.md)  
 .NET ネイティブのすべてのランタイムディレクティブファイルのルート要素。 その子要素は [\<Application>](application-element-net-native.md) と [\<Library>](library-element-net-native.md) です。  
  
 [\<Event>](event-element-net-native.md)  
 イベントに実行時ポリシーを適用します。 これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。  
  
 [\<Field>](field-element-net-native.md)  
 フィールドに実行時ポリシーを適用します。 これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 ジェネリック型またはメソッドのパラメーター型に実行時ポリシーを適用します。  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 型に実行時ポリシーを適用します (それを含んでいる型またはメソッドにそのポリシーが適用されている場合)。  
  
 [\<Library>](library-element-net-native.md)  
 アセンブリ内のすべての型に実行時ポリシーを適用します。 これは、 [\<Application>](application-element-net-native.md) 要素と要素の子です [\<Library>](library-element-net-native.md) 。  
  
 [\<Method>](method-element-net-native.md)  
 メソッドに実行時ポリシーを適用します。 これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 構築されたジェネリック メソッドに実行時ポリシーを適用します。 これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。  
  
 [\<Namespace>](namespace-element-net-native.md)  
 名前空間内のすべての型に実行時ポリシーを適用します。  
  
 [\<Parameter>](parameter-element-net-native.md)  
 メソッドに渡された引数の型に実行時ポリシーを適用します。  
  
 [\<Property>](property-element-net-native.md)  
 プロパティに実行時ポリシーを適用します。 これは、 [\<Type>](type-element-net-native.md) 要素と要素の子です [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。  
  
 [\<Type>](type-element-net-native.md)  
 型に実行時ポリシーを適用します。  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 構築されたジェネリック型に実行時ポリシーを適用します。  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 メソッドに渡された <xref:System.Type> 引数によって表される型に実行時ポリシーを適用します。  
  
## <a name="see-also"></a>関連項目

- [rd.xml 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)
