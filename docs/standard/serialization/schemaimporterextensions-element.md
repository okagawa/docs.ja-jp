---
title: <schemaImporterExtensions> 要素
description: <schemaImporterExtensions> 要素には、XSD の型を .NET の型にマッピングするために XmlSchemaImporter によって使用される型が含まれます。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 35626618a8dd7c63a7008d10bc3568484836a488
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282276"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> 要素

XSD の型を .NET の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型が含まれます。 構成ファイルの詳細については、「[構成ファイル スキーマ](../../framework/configure-apps/file-schema/index.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<schemaImporterExtensions> の \<add> 要素](add-element-for-schemaimporterextensions.md)|マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。|  
  
## <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.xml.serialization> 要素](system-xml-serialization-element.md)|XML シリアル化を制御する最上位の要素です。|  
  
## <a name="example"></a>例  
 次のコード例では、XSD の型を .NET の型にマッピングするときに <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を示します。  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [構成ファイル スキーマ](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 要素](datetimeserialization-element.md)
- [\<schemaImporterExtensions> の \<add> 要素](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> 要素](system-xml-serialization-element.md)
