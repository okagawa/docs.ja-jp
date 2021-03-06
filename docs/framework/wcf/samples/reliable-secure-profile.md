---
title: Reliable Secure Profile
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 9ddd0d78396bba6712650620e6b46c62f13337e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144215"
---
# <a name="reliable-secure-profile"></a>Reliable Secure Profile

このサンプルでは、WCF および[信頼性のあるセキュリティで保護されたプロファイル (RSP) を](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html)構成する方法を示します。 このサンプルでは、信頼できるメッセージングと共に構成できる[接続の作成](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf)チャネルの実装と、必要に応じて RSP 仕様に基づいて信頼できるセキュリティで保護されたバインドを作成するセキュリティで保護されたチャネルを示します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>ディスカッション  
 このサンプルでは、信頼できる非同期の双方向メッセージ交換シナリオを示します。 サービスには双方向コントラクトがあり、クライアントには双方向コールバック コントラクトが実装されます。 クライアントからサービスに対して要求が開始され、要求に対しては個別の接続で応答する必要があります。 要求メッセージは信頼できる方法で送信されます。 クライアントでは、終端にある待機エンドポイントを開きません。 したがって、クライアントは "Make Connection" 要求を使用してサービスをポーリングし、サービスはこの "Make Connection" 要求のバック チャネルで応答を返信します。 このサンプルでは、クライアントで待機エンドポイントを公開せずに (また、ファイアウォールの例外を設けずに)、HTTP を介してセキュリティで保護された信頼できる双方向通信を実現する方法を示します。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. ソリューション**を**開きます。  
  
2. **ソリューション エクスプローラ**で **[サービス**プロジェクト] を右クリックし、コンテキスト メニューから [**デバッグ**] を選択し、[**新しいインスタンスの開始**] を選択します。 サービス ホストが開始されます。  
  
3. **ソリューション エクスプローラ**で **[クライアント プロジェクト**] を右クリックし、コンテキスト メニューから [**デバッグ**] を選択し、[**新しいインスタンスの開始**] を選択します。 クライアントが開始されます。  
  
4. クライアント コンソール ウィンドウのプロンプトに任意の文字列を入力し、Enter キーを押します。入力文字列がサービスに送信され、この文字列のハッシュが計算されます。  
  
5. クライアント コンソール ウィンドウに結果を表示するためにサービスから双方向コールバック コントラクト操作がコールバックされたら、クライアント ウィンドウで結果を確認します。 実行に時間のかかるデータ処理操作を再現するために、サービスからの応答は意図的に遅延されます。  
  
6. HTTP トラフィックの監視 (ネットワーク モニター、Fiddler などのオンライン ネットワーク監視ツールを使用) により、Reliable Secure Profile で規定されているように通信のシーケンスがクライアントとサービスの間で確立されていること、およびどのようにクライアントが "Make Connection" 要求を使用してサービスをポーリングしているかが示されます。 サービスでは、処理した応答を返信できる状態になると、最後の "Make Connection" 要求のバック チャネルを使用して、結果を返信します。  
  
7. サービス コンソール ウィンドウで Enter キーを押してサービスを終了します。 クライアント コンソール ウィンドウで Enter キーを押してクライアントを終了します。
