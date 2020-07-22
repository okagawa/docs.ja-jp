---
title: IPv6 の有効化と無効化
description: 次の構成手順に従って、IPv6 プロトコルの使用を有効にします。これには、コンピューターまたはアプリケーションの構成ファイルの変更も含まれます。
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 7729647b09df20a98d5d639a641cb0a31f557330
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502614"
---
# <a name="enabling-and-disabling-ipv6"></a>IPv6 の有効化と無効化
IPv6 プロトコルを使用するには、IPv6 をサポートしているオペレーティング システムのバージョンを実行していることを確認し、オペレーティング システムとネットワーク クラスが正しく構成されていることを確認してください。  
  
## <a name="configuration-steps"></a>構成手順  
 次の表に、さまざまな構成を示します。  
  
|オペレーティング システムが IPv6 に対応しているか|ネットワーク クラスが IPv6 に対応しているか|説明|  
|-------------------------------------|---------------------------------------|-----------------|  
|いいえ|いいえ|IPv6 アドレスを解析できます。|  
|いいえ|はい|IPv6 アドレスを解析できます。|  
|はい|いいえ|IPv6 アドレスを解析し、旧式マークが付けられていない名前解決のメソッドを使用して、IPv6 アドレスを解決できます。|  
|はい|はい|IPv6 アドレスを解析し、旧式マークが付けられているものも含め、すべてのメソッドを使用して IPv6 アドレスを解決できます。|  
  
 System.Net 名前空間のすべてのクラスに対して IPv6 のサポートを有効にするには、コンピューターの構成ファイルまたはアプリケーションの構成ファイルを変更する必要があることに注意してください。 アプリケーション構成ファイルは、コンピューターの構成ファイルよりも優先されます。  
  
 IPv6 のサポートを有効にするようにコンピューター構成ファイル *machine.config* を変更する方法の例については、「[方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)」を参照してください。 また、オペレーティング システムの IPv6 のサポートが有効になっていることを確認してください。  
  
 .NET Framework には、構成ファイル内に次のように設定された構成スイッチがあります。  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 .NET Framework バージョン 1.1 以前では、**ipv6 enabled** 構成スイッチの値で <xref:System.Net.Dns?displayProperty=nameWithType> クラスのメンバーが IPv6 アドレスを返すかどうかを指定します。  
  
 .NET Framework バージョン 2.0 以降では、Windows が IPv6 をサポートしている場合、<xref:System.Net.Dns?displayProperty=nameWithType> クラスのメンバー (<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> メソッドなど) が 1 つの制限付きで IPv6 アドレスを返します。 DNS <xref:System.Net.Dns?displayProperty=nameWithType> の古いメンバー (<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> メソッドなど) は、構成ファイル内の ipv6 enabled 設定の値を読み取り、認識します。  
  
## <a name="see-also"></a>関連項目

- [インターネット プロトコル バージョン 6](internet-protocol-version-6.md)
- [ソケット](sockets.md)
- [ネットワーク設定スキーマ](../configure-apps/file-schema/network/index.md)
- [\<ipv6> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
