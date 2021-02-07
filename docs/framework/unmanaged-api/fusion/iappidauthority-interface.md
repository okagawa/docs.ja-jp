---
description: '詳細情報: IAppIdAuthority インターフェイス'
title: IAppIdAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
ms.openlocfilehash: 238885c7f080571b414511c24f9772dbc19b4683
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761006"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority インターフェイス

アプリケーション id と参照のキーを生成して比較するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|指定した2つの [IDefinitionAppId](idefinitionappid-interface.md) インスタンスが等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::AreReferencesEqual`|指定した2つの [IReferenceAppId](ireferenceappid-interface.md) インスタンスが等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|指定した2つの文字列定義が等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|指定した2つの文字列参照が等しいかどうかを示す値を取得します。 フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。|  
|`IAppIdAuthority::CreateDefinition`|現在のスコープ内のアセンブリを表す、新しく生成されたインスタンスへのインターフェイスポインターを取得し `IDefinitionAppId` ます。|  
|`IAppIdAuthority::CreateReference`|現在のスコープ内のアセンブリを表す、新しく作成されたへのインターフェイスポインターを取得し `IReferenceAppId` ます。|  
|`IAppIdAuthority::DefinitionToText`|指定した `IDefinitionAppId` フラグ値を使用して、指定したの文字列バージョンを取得します。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|指定した `IDefinitionAppId` とが同じアセンブリを表しているかどうかを示す値を取得し `IReferenceAppId` ます。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|指定した定義文字列と参照文字列が同じアセンブリを表しているかどうかを示す値を取得します。|  
|`IAppIdAuthority::GenerateDefinitionKey`|指定したインスタンスを表す文字列キーを取得し `IDefinitionAppId` ます。|  
|`IAppIdAuthority::GenerateReferenceKey`|指定したインスタンスを表す文字列キーを取得し `IReferenceAppId` ます。|  
|`IAppIdAuthority::HashDefinition`|指定したインスタンスのハッシュキーを取得し `IDefinitionAppId` ます。|  
|`IAppIdAuthority::HashReference`|指定したインスタンスのハッシュキーを取得し `IReferenceAppId` ます。|  
|`IAppIdAuthority::ReferenceToText`|指定した `IReferenceAppId` フラグ値を使用して、指定したの文字列バージョンを取得します。|  
|`IAppIdAuthority::TextToDefinition`|`IDefinitionAppId`指定した文字列キーによって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。|  
|`IAppIdAuthority::TextToReference`|`IReferenceAppId`指定した文字列キーによって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
