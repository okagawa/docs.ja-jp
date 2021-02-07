---
description: 詳細については、「XmlReader」を参照してください。
title: XmlReader Qlreader メソッド (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 61d594c0438c86863ce4052387439f5483d8a34c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740435"
---
# <a name="xmlreadercreatesqlreader-method"></a>XmlReader.CreateSqlReader  メソッド

解析のために指定されたストリーム、設定、およびコンテキスト情報を使用して、新しい <xref:System.Xml.XmlReader> インスタンスを作成します。

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a>パラメーター

- `input` <xref:System.IO.Stream>  
  XML データを格納しているストリーム。

- `settings` <xref:System.Xml.XmlReaderSettings>  
  新しい <xref:System.Xml.XmlReader> インスタンスの設定。 この値は、`null` の場合もあります。

- `inputContext` <xref:System.Xml.XmlParserContext>  
  XML フラグメントの解析に必要なコンテキスト情報。 この値は、`null` の場合もあります。

## <a name="returns"></a>戻り値

<xref:System.Xml.XmlReader>  
ストリーム内の XML データの読み取りに使用するオブジェクト。

## <a name="remarks"></a>解説

> [!WARNING]
> `XmlReader.CreateSqlReader`メソッドは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Xml>

**アセンブリ:** System.Xml.dll

**.NET Framework のバージョン:** 2.0 以降で使用できます。
