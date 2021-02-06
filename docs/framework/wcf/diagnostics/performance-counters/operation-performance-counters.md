---
description: 詳細については、「操作のパフォーマンスカウンター」を参照してください。
title: 操作パフォーマンス カウンター
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: e0a503d4d8b178d5d3f4ef240bf84c4b02a581ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655202"
---
# <a name="operation-performance-counters"></a>操作パフォーマンス カウンター

操作パフォーマンス カウンターは、パフォーマンス モニター (Perfmon.exe) を使用して表示した場合、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。 それぞれの操作に個別のインスタンスがあります。 つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。 オブジェクトのインスタンスには次のパターンの名前が付いています。  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。  
  
> [!CAUTION]
> パフォーマンス カウンターのインスタンス名の長さには制限があります。 Windows Communication Foundation (WCF) カウンターインスタンス名が最大長を超えると、WCF はインスタンス名の一部をハッシュ値に置き換えます。  
  
## <a name="see-also"></a>関連項目

- [パフォーマンス カウンター](index.md)
