---
title: タイム ゾーンの概要
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], about time zones
- transition time [.NET Framework]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET Framework], creating
- invalid time [.NET Framework]
- fixed rule [.NET Framework]
- ambiguous time [.NET Framework]
- floating rule [.NET Framework]
- daylight saving time [.NET Framework]
- adjustment rule [.NET Framework]
- time zones [.NET Framework], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
ms.openlocfilehash: 9cb50357931cb22fd2862ba7558154a4782e4557
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281038"
---
# <a name="time-zone-overview"></a>タイム ゾーンの概要

<xref:System.TimeZoneInfo>クラスは、タイムゾーンに対応したアプリケーションの作成を簡略化します。 クラスは、 <xref:System.TimeZone> ローカルタイムゾーンと世界協定時刻 (UTC) の操作をサポートします。 クラスは、 <xref:System.TimeZoneInfo> これらのゾーンと、レジストリで定義されている情報に関するタイムゾーンの両方をサポートします。 また <xref:System.TimeZoneInfo> 、を使用して、システムに関する情報がないカスタムタイムゾーンを定義することもできます。

## <a name="time-zone-essentials"></a>タイムゾーンの基本

タイム ゾーンは、同じ時刻が使用されている地域です。 常にではありませんが、通常、隣接するタイム ゾーンは 1 時間違いです。 世界のタイム ゾーンの時刻は、世界協定時刻 (UTC) からのオフセットとして表されます。

世界のタイム ゾーンの多くは、夏時間をサポートしています。 夏時間では、春や初夏には時刻を 1 時間進め、晩夏や秋には通常 (または標準) の時間に戻すことで、日中の時間を最大化しようと試みます。 こうした標準時間前後の変更は、調整規則と呼ばれます。

特定のタイム ゾーンの夏時間前後の移行は、固定調整規則または浮動調整規則で定義できます。 固定調整規則では、毎年、夏時間前後の移行が行われる特定の日付を設定します。 たとえば、毎年 10 月 25 日に行われる夏時間から標準時間への移行は、固定調整規則に従います。 浮動調整規則の方がはるかに一般的です。浮動調整規則では、夏時間への移行、または夏時間からの移行について特定の月の特定の週の特定の曜日が設定されます。 たとえば、3 月の第 3 日曜日に行われる標準時間から夏時間への移行は、浮動調整規則に従います。

調整規則をサポートするタイム ゾーンの場合、夏時間前後の移行によって、2 つの変則的な時刻が生じます。無効な時刻とあいまいな時刻です。 無効な時刻は、標準時間から夏時間への移行で生じる存在しない時刻です。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 3:00 に変更される場合、午前 2:00 から 午前 2:59:99 までの時刻は 無効です。 あいまいな時刻は、1 つのタイム ゾーンで 2 つの時刻にマップできる時刻です。 あいまいな時刻は夏時間から標準時間への移行で生じます。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 1:00 に変更される場合、午前 1:00 から 午前 1:59:99 までの時刻は 標準時間または夏時間のいずれにでも解釈できます。

## <a name="time-zone-terminology"></a>タイムゾーンの用語

次の表は、タイム ゾーンを使用し、タイム ゾーン対応アプリケーションを開発するときに一般的に使用される用語の定義一覧です。

| 項目            | 定義 |
| --------------- | ---------- |
| 調整規則 | 標準時間から夏時間へ、および夏時間から標準時間への移行が行われるタイミングを定義した規則。 各調整規則には、規則が適用されるタイミングを定義する開始日と終了日があります (たとえば、調整規則は、1986年1月1日から2006年12月31日まで)、デルタ (調整規則の適用結果として標準時間が変化する時間)、および調整期間中に遷移が発生する特定の日時に関する情報を示しています。 移行は、固定規則または浮動規則に従う可能性があります。 |
| あいまいな時刻  | 1 つのタイム ゾーンで 2 つの時刻にマップできる時刻です。 あいまいな時刻は、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 1:00 に変更される場合、午前 1:00 から 午前 1:59:99 までの時刻は 標準時間または夏時間のいずれにでも解釈できます。 |
| 固定規則      | 夏時間前後の移行について特定の日付を設定する調整規則。 たとえば、毎年 10 月 25 日に行われる夏時間から標準時間への移行は、固定調整規則に従います。 |
| 浮動規則   | 浮動調整規則の方がはるかに一般的です。浮動調整規則では、夏時間への移行、または夏時間からの移行について特定の月の特定の週の特定の曜日が設定されます。 たとえば、3 月の第 3 日曜日に行われる標準時間から夏時間への移行は、浮動調整規則に従います。 |
| 無効な時刻    | 標準時間から夏時間への移行中に生じる存在しない時刻。 無効な時刻は、あるタイム ゾーンの標準時間から夏時間に移行する際など、時計の時刻を前に進めるときに発生します。 たとえば、移行が特定の日付の午前 2:00 に行われ、 時刻が午前 3:00 に変更される場合、午前 2:00 から 午前 2:59:99 までの時刻は 無効です。 |
| 移行時間 | 特定のタイム ゾーンで実施される夏時間と標準時間の切り替えなど、特定の時間切り替えに関する情報。 |

## <a name="time-zones-and-the-timezoneinfo-class"></a>タイムゾーンと TimeZoneInfo クラス

.NET では、 <xref:System.TimeZoneInfo> オブジェクトはタイムゾーンを表します。 クラスには、 <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> オブジェクトの配列を返すメソッドが含まれてい <xref:System.TimeZoneInfo.AdjustmentRule> ます。 この配列の各要素は、特定の期間の夏時間との間の移行に関する情報を提供します。 (夏時間をサポートしていないタイムゾーンの場合、メソッドは空の配列を返します)。各オブジェクトには、 <xref:System.TimeZoneInfo.AdjustmentRule> <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> および <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> 夏時間との間の遷移の特定の日付と時刻を定義するプロパティとプロパティがあります。 プロパティは、 <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> その遷移が固定されているか、フローティング状態であるかを示します。

.NET は、Windows オペレーティングシステムによって提供され、レジストリに格納されているタイムゾーン情報に依存しています。 地球のタイムゾーンの数によっては、すべての既存のタイムゾーンがレジストリに表示されるわけではありません。 また、レジストリは動的な構造であるため、定義済みのタイムゾーンを追加または削除することができます。 最後に、レジストリに履歴のタイムゾーンデータが含まれているとは限りません。 たとえば、Windows XP では、レジストリにはタイムゾーン調整の1つのセットについてのみのデータが含まれています。 Windows Vista では、動的なタイムゾーンデータがサポートされています。つまり、1つのタイムゾーンには、特定の期間に適用される複数の調整規則を含めることができます。 ただし、Windows Vista レジストリで定義され、夏時間をサポートするほとんどのタイムゾーンには、定義済みの調整規則が1つまたは2つしかありません。

レジストリにクラスが依存していることは、 <xref:System.TimeZoneInfo> タイムゾーン対応アプリケーションが、特定のタイムゾーンがレジストリで定義されていることを特定できないことを意味します。 そのため、(ローカルのタイム ゾーンまたは UTC を示すタイム ゾーン以外の) 特定のタイム ゾーンをインスタンス化する場合、例外処理を使用する必要があります。 また、必要な <xref:System.TimeZoneInfo> オブジェクトをレジストリからインスタンス化できない場合に、アプリケーションの続行を可能にする方法も提供する必要があります。

必要なタイムゾーンが存在しない場合に対処するために、クラスには <xref:System.TimeZoneInfo> メソッドが含まれています。このメソッドを使用して、 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> レジストリに見つからないカスタムタイムゾーンを作成できます。 カスタムタイムゾーンの作成の詳細については、「[方法: 調整規則のないタイムゾーンを作成](create-time-zones-without-adjustment-rules.md)する」および「[方法: 調整規則を使用してタイムゾーンを作成する](create-time-zones-with-adjustment-rules.md)」を参照してください。 また、メソッドを使用して、 <xref:System.TimeZoneInfo.ToSerializedString%2A> 新しく作成されたタイムゾーンを文字列に変換し、データストア (データベース、テキストファイル、レジストリ、アプリケーションリソースなど) に保存することもできます。 次に、メソッドを使用して、 <xref:System.TimeZoneInfo.FromSerializedString%2A> この文字列をオブジェクトに変換して戻し <xref:System.TimeZoneInfo> ます。 詳細については、「[方法: 埋め込みリソースにタイムゾーンを保存](save-time-zones-to-an-embedded-resource.md)する」および「[方法: 埋め込みリソースからタイムゾーンを復元](restore-time-zones-from-an-embedded-resource.md)する」を参照してください。

各タイム ゾーンは、UTC からのベース オフセットと、既存の調整規則を反映した UTC からのオフセットによって表されるため、あるタイム ゾーンの時刻は、簡単に別のタイム ゾーンの時間に変換できます。 このため、オブジェクトには <xref:System.TimeZoneInfo> 次のようないくつかの変換メソッドが含まれています。

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>。 UTC を指定されたタイムゾーンの時刻に変換します。

- <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>。指定されたタイムゾーンの時刻を UTC に変換します。

- <xref:System.TimeZoneInfo.ConvertTime%2A>。指定されたタイムゾーンの時刻を、指定された別のタイムゾーンの時刻に変換します。

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>。オブジェクトではなくタイムゾーン id を <xref:System.TimeZoneInfo> パラメーターとして使用して、指定されたタイムゾーンの時刻を別の指定されたタイムゾーンの時刻に変換します。

タイム ゾーン間の時間を変換する方法の詳細については、「[タイム ゾーン間での時刻の変換](converting-between-time-zones.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [日付、時刻、およびタイム ゾーン](index.md)
