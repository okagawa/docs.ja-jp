---
title: <oidMap> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155168"
---
# <a name="oidmap-element"></a>\<oidMap> 要素
クラスに対する asn.1 オブジェクト識別子 (OID) マッピングが含まれています。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a>構文  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|Asn.1 OID をフレンドリ名にマップします。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号設定を含みます。|  
|`mscorlib`|要素が含まれてい `cryptographySettings` ます。|  
  
## <a name="example"></a>例  
 次の例は、要素を使用して、 **\<oidMap>** RIPEMD-160 ハッシュアルゴリズムの OID とそのハッシュアルゴリズムの実装とのマッピングを格納する方法を示しています。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [構成ファイル スキーマ](../index.md)
- [暗号設定スキーマ](index.md)
- [暗号化サービス](../../../../standard/security/cryptographic-services.md)
- [暗号化クラスの設定](../../configure-cryptography-classes.md)
- [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../map-object-identifiers-to-cryptography-algorithms.md)
