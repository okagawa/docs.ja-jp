---
description: '詳細情報: <publisherPolicy> 要素'
title: <publisherPolicy> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 35d729d5b195e010a80e7272312f14ac5802001b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802438"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy> 要素

ランタイムが発行元ポリシーを適用するかどうかを指定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`apply`|発行者ポリシーを適用するかどうかを指定します。|  
  
## <a name="apply-attribute"></a>属性の適用  
  
|値|説明|  
|-----------|-----------------|  
|`yes`|発行者ポリシーを適用します。 これは、既定の設定です。|  
|`no`|発行者ポリシーは適用されません。|  
  
### <a name="child-elements"></a>子要素  

なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`dependentAssembly`|各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。 `<dependentAssembly>`アセンブリごとに1つの要素を使用します。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  

 コンポーネントベンダーがアセンブリの新しいバージョンをリリースする場合、ベンダーには発行者ポリシーを含めることができるため、以前のバージョンを使用するアプリケーションでは新しいバージョンが使用されるようになりました。 特定のアセンブリに対して発行者ポリシーを適用するかどうかを指定するには、要素に要素を配置し **\<publisherPolicy>** **\<dependentAssembly>** ます。  
  
 **適用** 属性の既定の設定は **[はい]** です。 **適用** 属性を [**いいえ** **]** に設定すると、アセンブリの以前のすべての設定がオーバーライドされます。  
  
 アプリケーションが [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) アプリケーション構成ファイルの要素を使用して発行者ポリシーを明示的に無視するためのアクセス許可が必要です。 権限は、にフラグを設定することによって付与され <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> ます。 詳細については、「 [アセンブリバインディングリダイレクトのセキュリティアクセス許可](../../assembly-binding-redirection-security-permission.md)」を参照してください。  
  
## <a name="example"></a>例  

 次の例では、アセンブリの発行者ポリシーをオフにし `myAssembly` ます。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [ランタイムがアセンブリを検索する方法](../../../deployment/how-the-runtime-locates-assemblies.md)
- [アセンブリ バージョンのリダイレクト](../../redirect-assembly-versions.md)
