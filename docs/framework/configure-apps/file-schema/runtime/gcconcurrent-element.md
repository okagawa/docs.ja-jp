---
title: gcConcurrent 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102919"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent> 要素

共通言語ランタイムがガベージ コレクションを別のスレッドで実行するかどうかを指定します。

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a>構文

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`enabled`|必須の属性です。<br /><br />ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。|

#### <a name="enabled-attribute"></a>enabled 属性

|値|Description|
|-----------|-----------------|
|`false`|ガベージコレクションを同時に実行しません。|
|`true`|ガベージ コレクションを並列に実行します。 既定値です。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|Description|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|

## <a name="remarks"></a>解説

.NET Framework 4 より前では、ワークステーションのガベージコレクションは同時実行ガベージコレクションをサポートしていました。これにより、別のスレッドでバックグラウンドでガベージコレクションが実行されました。 .NET Framework 4 では、同時実行ガベージコレクションがバックグラウンド GC に置き換えられました。これにより、別のスレッドでバックグラウンドでガベージコレクションが実行されます。 .NET Framework 4.5 以降では、サーバーのガベージコレクションでバックグラウンドコレクションを使用できるようになりました。 **GcConcurrent**要素は、ランタイムが同時実行ガベージコレクションとバックグラウンドガベージコレクションのどちらを実行するか、またはフォアグラウンドでガベージコレクションを実行するかどうかを制御します。

### <a name="to-disable-background-garbage-collection"></a>バックグラウンドガベージコレクションを無効にするには

> [!WARNING]
> .NET Framework 4 以降では、同時実行ガベージコレクションはバックグラウンドガベージコレクションに置き換えられます。 .NET Framework のドキュメントでは、*同時実行*と*背景*という用語が同じ意味で使用されます。 バックグラウンドガベージコレクションを無効にするには、この記事で説明されているように、 **gcConcurrent**要素を使用します。

既定では、ランタイムは同時実行ガベージ コレクションまたはバックグラウンド ガベージ コレクションを使用します。これは待機時間について最適化されています。 アプリケーションでユーザーとのやり取りが多い場合は、同時実行ガベージ コレクションを有効にして、ガベージ コレクションを実行するためのアプリケーションの停止時間を最小限に抑えます。 `enabled` **GcConcurrent**要素の属性をに設定すると `false` 、ランタイムは非同時実行ガベージコレクションを使用します。これは、スループットのために最適化されています。

次の構成ファイルは、バックグラウンドガベージコレクションを無効にします。

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

マシン構成ファイルに**gcConcurrentSetting**設定がある場合は、すべての .NET Framework アプリケーションの既定値が定義されます。 マシン構成ファイルの設定は、アプリケーション構成ファイルの設定をオーバーライドします。

同時実行ガベージコレクションとバックグラウンドガベージコレクションの詳細については、「[バックグラウンドガベージコレクション](../../../../standard/garbage-collection/background-gc.md)」を参照してください。

## <a name="example"></a>例

次の例では、バックグラウンドガベージコレクションを有効にします。

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [ガベージ コレクションの基礎](../../../../standard/garbage-collection/fundamentals.md)
