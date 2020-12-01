---
title: トラブルシューティング:Windows サービスをデバッグする場合
description: Windows サービスのデバッグを開始します。 Windows サービス アプリケーションをデバッグするとき、サービスと Windows Service Manager の間でやり取りが行われます。
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
ms.openlocfilehash: 2c1180ef8e3e44c50f10a263d86dcae830d9cd0e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270394"
---
# <a name="troubleshooting-debugging-windows-services"></a>トラブルシューティング:Windows サービスをデバッグする場合

Windows サービス アプリケーションをデバッグするとき、サービスと **Windows Service Manager** の間でやり取りが行われます。 **Service Manager** は <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドを呼び出してサービスを開始した後、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドから戻るのを 30 秒間待ちます。 この時間内にメソッドから戻らない場合、Manager はサービスを開始できないというエラーを表示します。  
  
 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドについて「[方法:Windows サービス アプリケーションをデバッグする](how-to-debug-windows-service-applications.md)」の説明に従ってデバッグする場合、この 30 秒間のことを認識しておく必要があります。 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドにブレークポイントを設定し、30 秒以内にメソッドを最後までステップ実行しないと、Manager はサービスを開始しません。  
  
## <a name="see-also"></a>関連項目

- [方法: Windows サービス アプリケーションをデバッグする](how-to-debug-windows-service-applications.md)
- [Windows サービス アプリケーションの概要](introduction-to-windows-service-applications.md)
