---
description: '詳細情報: <GCHeapCount> 要素'
title: G不正 Apcount 要素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 9e1e000d647435fe7a8c4b1a8f7549f06c2a3b38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786968"
---
# <a name="gcheapcount-element"></a>\<GCHeapCount> 要素

サーバーのガベージコレクションに使用するヒープまたはスレッドの数を指定します。

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a>構文

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`enabled`|必須の属性です。<br /><br />サーバーのガベージコレクションに使用するヒープの数を指定します。 実際のヒープ数は、指定するヒープの数とプロセスで使用できるプロセッサの数の最小値です。 |

#### <a name="enabled-attribute"></a>enabled 属性

|値|説明|
|-----------|-----------------|
|`nn`|サーバー GC に使用するヒープの数。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|

## <a name="remarks"></a>解説

既定では、サーバー GC スレッドはそれぞれの CPU とハード関係があるため、1つの GC ヒープ、1つのサーバー GC スレッド、および各プロセッサにつき1つのバックグラウンドサーバー GC スレッドが存在するようになります。 .NET Framework 4.6.2 以降では、 **g Apcount** 要素を使用して、アプリケーションでサーバー GC に使用されるヒープの数を制限することができます。 サーバー GC に使用されるヒープの数を制限することは、サーバーアプリケーションの複数のインスタンスを実行するシステムに特に役立ちます。

通常は、次の2つのフラグと共に使用 **されます**。

- [GCNoAffinitize](gcnoaffinitize-element.md)。サーバー GC スレッド/ヒープが cpu と関連付けられているかどうかを制御します。

- [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)。 cpu との GC スレッド/ヒープの関係を制御します。

**GGCNoAffinitize** が設定されていて、 が無効になっている場合 (既定の設定)、 *nn* GC スレッド/ヒープと最初の *nn* プロセッサの間に関係があります。 **GCHeapAffinitizeMask** 要素を使用して、プロセスのサーバー GC ヒープによって使用されるプロセッサを指定できます。 それ以外の場合、システムで複数のサーバープロセスが実行されていると、プロセッサの使用率が重複します。

**GGCNoAffinitize** が有効になっている場合、ガベージコレクターはサーバー gc に使用されるプロセッサの数を制限しますが、gc ヒープとプロセッサを関係付けしません。

## <a name="example"></a>例

次の例は、アプリケーションが10個のヒープ/スレッドを持つサーバー GC を使用することを示しています。 これらのヒープは、システムで実行されている他のアプリケーションのヒープと重複しないようにするため、 **GCHeapAffinitizeMask** を使用して、プロセスで cpu 0 ~ 9 を使用するように指定します。

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

次の例では、サーバー GC スレッドを関係付け、GC ヒープ/スレッドの数を10に制限していません。

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [GCNoAffinitize 要素](gcnoaffinitize-element.md)
- [GCHeapAffinitizeMask 要素](gcheapaffinitizemask-element.md)
- [ガベージ コレクションの基礎](../../../../standard/garbage-collection/fundamentals.md)
- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
