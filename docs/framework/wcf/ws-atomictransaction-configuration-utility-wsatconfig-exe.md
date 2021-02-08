---
description: 詳細については、「WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)」を参照してください。
title: WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 8b315e5aa5df23a4d9bb032db41b7067accfa010
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792961"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)

WS-AtomicTransaction 構成ユーティリティは、基本的な WS-AtomicTransaction サポート設定を構成するために使用されます。  
  
## <a name="syntax"></a>構文  
  
```console  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>解説

 このコマンドラインツールを使用すると、ローカルコンピューターでのみ基本的な WS-AT 設定を構成できます。 ローカルコンピューターとリモートコンピューターの両方で設定を構成する必要がある場合は、「 [WS-Atomic のトランザクションサポートの構成](./feature-details/configuring-ws-atomic-transaction-support.md)」の説明に従って、MMC スナップインを使用する必要があります。  
  
 コマンドラインツールは、Windows SDK のインストール場所にあります。
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe
  
 次の表は、WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe) で使用できるオプションを示します。  
  
> [!NOTE]
> 選択したポートに SSL 証明書を設定すると、そのポートに関連付けられたオリジナルの SSL 証明書が上書きされます。  
  
|オプション|説明|  
|-------------|-----------------|  
|企業\<account,>|WS-AtomicTransaction に追加できるアカウントをコンマで区切って指定します。 これらのアカウントの有効性の確認は行われません。|  
|-accountsCerts: \<thumb>&#124; "Issuer\SubjectName", >|WS-AtomicTransaction に追加できる証明書をコンマで区切って指定します。 証明書は、サムプリントまたは Issuer\SubjectName ペアで示されます。 空の場合は、サブジェクト名に {EMPTY} を使用します。|  
|-endpointCert: <マシン&#124;\<thumb>&#124; "Issuer\SubjectName" >|コンピューターの証明書を使用するか、サムプリントまたは Issuer\SubjectName ペアで指定される別のローカル エンドポイントの証明書を使用します。 空の場合は、サブジェクト名に {EMPTY} を使用します。|  
|maxTimeout\<sec>|最大タイムアウトを秒単位で指定します。 有効な値は 0 ~ 3600 です。|  
|ネットワーク\<enable&#124;disable>|WS-AtomicTransaction ネットワーク サポートを有効または無効にします。|  
|ポート\<portNum>|WS-AtomicTransaction の HTTPS ポートを設定します。<br /><br /> このツールを実行する前にファイアウォールが既に有効な場合、ポートは例外の一覧に自動的に登録されます。 このツールを実行する前にファイアウォールが無効な場合は、ファイアウォールに関する追加の構成はありません。<br /><br /> WS-AT の構成後にファイアウォールを有効にする場合は、このツールを再度実行し、このパラメーターを使用してポート番号を指定する必要があります。 WS-AT の構成後にファイアウォールを無効にする場合は、入力を追加しないで WS-AT の動作を続行します。|  
|タイムアウト\<sec>|既定のタイムアウトを秒単位で指定します。 有効な値は 1 ～ 3600 の範囲です。|  
|traceActivity\<enable&#124;disable>|アクティビティ イベントのトレースを有効または無効にします。|  
|-traceLevel: \<Off&#124;Error&#124;Critical&#124;Warning&#124;Information&#124; Verbose&#124;All> }|トレース レベルを指定します。|  
|-tracePII:\<enable&#124;disable>|個人を特定できる情報のトレースを有効または無効にします。|  
|-traceProp:\<enable&#124;disable>|伝達イベントのトレースを有効または無効にします。|  
|-restart|MSDTC を再起動して変更を直ちに反映します。 これが指定されていない場合、変更は、MSDTC が再起動されたときに有効になります。|  
|-show|現在の WS-AtomicTransaction プロトコル設定を表示します。|  
|virtualServer\<virtualServer>|DTC リソース クラスター名を指定します。|  
  
## <a name="see-also"></a>関連項目

- [WS-AtomicTransaction の使用](./feature-details/using-ws-atomictransaction.md)
- [WS-AtomicTransaction サポートの構成](./feature-details/configuring-ws-atomic-transaction-support.md)
