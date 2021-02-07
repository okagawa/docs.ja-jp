---
description: 詳細については、「IAppDomainSetup インターフェイス」を参照してください。
title: IAppDomainSetup インターフェイス
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 8fd224308ea68f7b56ae174c7f71fc4f89630101
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760585"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup インターフェイス

<xref:System.AppDomain?displayProperty=nameWithType> [ICorRuntimeHost:: CreateDomainEx](icorruntimehost-createdomainex-method.md)メソッドを呼び出して作成する前に、ホストが型を構成できるようにするプロパティを提供します。  
  
## <a name="properties"></a>プロパティ  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|アプリケーションが格納されているディレクトリの名前を取得または設定します。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|アプリケーションの名前を取得または設定します。|  
|<xref:System.AppDomainSetup.CachePath%2A>|ファイルがシャドウコピーされるアプリケーション固有の領域の名前を取得または設定します。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|アプリケーションの構成ファイルの名前を取得または設定します。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|動的に生成されたファイルが格納およびアクセスされるディレクトリの名前を取得または設定します。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|このドメインに関連付けられているライセンスファイルへのパスを取得または設定します。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|プライベートアセンブリをプローブするディレクトリと結合されたディレクトリの一覧を取得または設定し <xref:System.AppDomainSetup.ApplicationBase%2A> ます。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<xref:System.AppDomainSetup.ApplicationBase%2A>アプリケーションの検索パスに含めたり、検索パスから除外したりする文字列値を取得または設定します。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|シャドウコピーされるアセンブリを含むディレクトリの名前を取得または設定します。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|シャドウコピーをオンまたはオフにするかどうかを示す文字列を取得または設定します。 有効な値は "true" または "false" です。|  
  
## <a name="remarks"></a>解説  

 インターフェイスは、 `IAppDomainSetup` <xref:System.IAppDomainSetup> 型が実装するマネージインターフェイスに対応 <xref:System.AppDomainSetup> します。 <xref:System.IAppDomainSetup?displayProperty=nameWithType>プロパティの詳細については、「」を参照してください。  
  
 `IAppDomainSetup` 作成前にインスタンスに追加できるアセンブリバインディング情報を表し <xref:System.AppDomain> ます。 たとえば、ホストは、プロパティを設定して、 <xref:System.AppDomainSetup.ApplicationBase%2A> マネージアセンブリの共通言語ランタイム (CLR) プローブがルートディレクトリを確立することができます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [ホスト インターフェイス](hosting-interfaces.md)
