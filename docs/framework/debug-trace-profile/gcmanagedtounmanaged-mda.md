---
title: gcManagedToUnmanaged MDA
description: GcManagedToUnmanaged マネージデバッグアシスタントを確認します。 この MDA は、アンマネージコードへの遷移中にガベージコレクションが途中で発生したためにアクティブになる場合があります。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
ms.openlocfilehash: 76c621a1f2bb780d38228f2a84d4c77441774770
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415915"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
`gcManagedToUnmanaged` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、スレッドがマネージド コードからアンマネージド コードに遷移する時に、毎回ガベージ コレクションがなされるようにします。  
  
## <a name="symptoms"></a>現象  
 アンマネージド ユーザー コンポーネントは、COM に公開されたマネージド オブジェクトを使おうとすると、アクセス違反をスローします。 COM オブジェクトはリリース済みのように表示されます。 アクセス違反は非確定です。  
  
## <a name="cause"></a>原因  
 アンマネージド コンポーネントがマネージド COM オブジェクトを正しくカウントする参照でない場合、ランタイムは、アンマネージド コンポーネントがオブジェクトへの参照を保持していると、COM に公開されたマネージド オブジェクトを収集できます。 ランタイムはガベージ コレクション中に <xref:System.Runtime.InteropServices.Marshal.Release%2A> を呼び出すので、ユーザー コンポーネントがガベージ コレクションの発生前にオブジェクトを使用すると、それは収集されないことになります。 これが非確定の原因です。  
  
## <a name="resolution"></a>解決策  
 このアシスタントを有効にすると、オブジェクトが収集の対象になってから <xref:System.Runtime.InteropServices.Marshal.Release%2A> が呼び出されるまでの時間が短縮し、収集されるオブジェクトへのアクセスを最初に試みるアンマネージ コンポーネントの追跡に役立ちます。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 スレッドがマネージド コードからアンマネージド コードに遷移する時に、毎回ガベージ コレクションがなされるようになります。  
  
## <a name="output"></a>出力  
 この MDA は、出力を生成しません。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [マネージド デバッグ アシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md)
- [相互運用マーシャリング](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
