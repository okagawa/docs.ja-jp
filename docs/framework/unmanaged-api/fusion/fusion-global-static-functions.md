---
description: 詳細については、「Fusion グローバル静的関数」を参照してください。
title: Fusion グローバル静的関数
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: c696908f72d67ecff5e7383e7a2754dd5436b819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761084"
---
# <a name="fusion-global-static-functions"></a>Fusion グローバル静的関数

このセクションでは、fusion API が使用するアンマネージグローバル静的関数について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [ClearDownloadCache 関数](cleardownloadcache-function.md)  
 ダウンロードされたアセンブリのグローバルアセンブリキャッシュを消去します。  
  
 [CompareAssemblyIdentity 関数](compareassemblyidentity-function.md)  
 2つのアセンブリ id を比較して、それらが等しいかどうかを判断します。  
  
 [CreateApplicationContext 関数](createapplicationcontext-function.md)  
 内部でのみ使用されます。 (この関数は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません)。  
  
 [CreateAssemblyCache 関数](createassemblycache-function.md)  
 グローバルアセンブリキャッシュを表す新しい [Iassemblycache](iassemblycache-interface.md) インスタンスへのポインターを取得します。  
  
 [CreateAssemblyEnum 関数](createassemblyenum-function.md)  
 指定したアセンブリ内に存在するオブジェクトのリストを表す [Iassemblyenum](iassemblyenum-interface.md) インスタンスへのポインターを取得します。  
  
 [CreateAssemblyNameObject 関数](createassemblynameobject-function.md)  
 指定した名前のアセンブリの一意の id を表す [IAssemblyName](iassemblyname-interface.md) インスタンスへのポインターを取得します。  
  
 [CreateHistoryReader 関数](createhistoryreader-function.md)  
 指定されたファイルの履歴リーダーを作成します。  
  
 [CreateInstallReferenceEnum 関数](createinstallreferenceenum-function.md)  
 指定したアセンブリへのアプリケーションの参照のリストを表す [Iinstallreferenceenum](iinstallreferenceenum-interface.md) インスタンスへのポインターを取得します。  
  
 [GetAppIdAuthority 関数](getappidauthority-function.md)  
 アプリケーション id と参照のキーを管理する [Iappidauthority](iappidauthority-interface.md) インスタンスへのポインターを取得します。  
  
 [GetAssemblyIdentityFromFile 関数](getassemblyidentityfromfile-function.md)  
 指定した `IUnknown` `IID` ファイルパスのアセンブリ内で、指定したを持つオブジェクトへのポインターを取得します。  
  
 [GetCachePath 関数](getcachepath-function.md)  
 指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。  
  
 [GetHistoryFileDirectory 関数](gethistoryfiledirectory-function.md)  
 アプリケーション履歴ディレクトリのパスを取得します。  
  
 [GetIdentityAuthority 関数](getidentityauthority-function.md)  
 コードオブジェクトのキーを管理する [Iidentity authority](iidentityauthority-interface.md) インスタンスへのポインターを取得します。  
  
 [IsFrameworkAssembly 関数](isframeworkassembly-function.md)  
 指定したアセンブリが管理されているかどうかを示す値を取得します。  
  
 [NukeDownloadedCache 関数](nukedownloadedcache-function.md)  
 共通言語ランタイムのダウンロードキャッシュを削除します。  
  
 [PreBindAssemblyEx 関数](prebindassemblyex-function.md)  
 アセンブリのポリシー後の表示名を取得します。  
  
## <a name="related-sections"></a>関連項目  

 [Fusion インターフェイス](fusion-interfaces.md)  
  
 [fusion 列挙体](fusion-enumerations.md)  
  
 [Fusion 構造体](fusion-structures.md)  
  
 [グローバル アセンブリ キャッシュ](../../app-domains/gac.md)
