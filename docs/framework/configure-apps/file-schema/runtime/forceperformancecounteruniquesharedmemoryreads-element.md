---
description: '詳細情報: <forcePerformanceCounterUniqueSharedMemoryReads> 要素'
title: <forcePerformanceCounterUniqueSharedMemoryReads> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 63fe695cc993faa851a9ea3196294397d2992c45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787033"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> 要素

PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> PerfCounter.dll が category Options レジストリ設定を使用して、カテゴリ固有の共有メモリまたはグローバルメモリのパフォーマンスカウンターデータを読み込むかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|PerfCounter.dll では、[カテゴリオプション] レジストリ設定を使用しません。これが既定値です。|  
|`true`|PerfCounter.dll では、[カテゴリオプション] レジストリ設定を使用します。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  

 .NET Framework 4 より前の .NET Framework のバージョンでは、読み込まれた PerfCounter.dll のバージョンは、プロセスに読み込まれたランタイムにこれされています。 コンピューターに .NET Framework バージョン1.1 と .NET Framework 2.0 の両方がインストールされている場合、.NET Framework 1.1 アプリケーションは .NET Framework 1.1 バージョンの PerfCounter.dll を読み込みます。 .NET Framework 4 以降では、インストールされている PerfCounter.dll の最新バージョンが読み込まれます。 これは、コンピューターに .NET Framework 4 がインストールされている場合に、.NET Framework 1.1 アプリケーションによって .NET Framework 4 バージョンの PerfCounter.dll が読み込まれることを意味します。  
  
 .NET Framework 4 以降では、パフォーマンスカウンターを使用する場合、PerfCounter.dll は各プロバイダーの [カテゴリオプション] レジストリエントリを確認して、カテゴリ固有の共有メモリまたはグローバル共有メモリから読み取るかどうかを判断します。 .NET Framework 1.1 PerfCounter.dll は、カテゴリ固有の共有メモリを認識しないため、そのレジストリエントリを読み取りません。常に、グローバルな共有メモリから読み取ります。  
  
 旧バージョンとの互換性のために、.NET Framework 4 PerfCounter.dll は .NET Framework 1.1 アプリケーションで実行されているときに、カテゴリオプションのレジストリエントリをチェックしません。 .NET Framework 1.1 PerfCounter.dll と同様に、グローバルな共有メモリを使用するだけです。 ただし、要素を有効にすることで、レジストリ設定を確認するように .NET Framework 4 PerfCounter.dll に指示でき `<forcePerformanceCounterUniqueSharedMemoryReads>` ます。  
  
> [!NOTE]
> 要素を有効 `<forcePerformanceCounterUniqueSharedMemoryReads>` にしても、カテゴリ固有の共有メモリが使用されることは保証されません。 を有効に設定する `true` と、PerfCounter.dll がカテゴリオプションのレジストリ設定を参照するだけになります。 カテゴリのオプションの既定の設定では、カテゴリ固有の共有メモリを使用します。ただし、カテゴリのオプションを変更して、グローバルな共有メモリを使用する必要があることを示すことができます。  
  
 [カテゴリオプション] の設定を含むレジストリキーは、<の HKEY_LOCAL_MACHINE\System\CurrentControlSet\Servicesの \\ 区分 \> \ パフォーマンスです。 既定では、カテゴリのオプションは3に設定されています。これは、PerfCounter.dll がカテゴリ固有の共有メモリを使用するように指示します。 [カテゴリ] オプションが0に設定されている場合、PerfCounter.dll はグローバル共有メモリを使用します。 インスタンスデータが再利用されるのは、作成されるインスタンスの名前が再利用されるインスタンスと同一である場合だけです。 すべてのバージョンがカテゴリに書き込むことができます。 Category オプションが1に設定されている場合、グローバル共有メモリが使用されますが、カテゴリ名が再利用されるカテゴリと同じ長さの場合は、インスタンスデータを再利用できます。  
  
 設定0および1を使用すると、メモリリークが発生し、パフォーマンスカウンターのメモリがいっぱいになる可能性があります。  
  
## <a name="example"></a>例  

 次の例は、カテゴリ固有の共有メモリを使用する必要があるかどうかを判断するために、PerfCounter.dll が category Options レジストリエントリを参照するように指定する方法を示しています。  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
