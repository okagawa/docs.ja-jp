---
description: '詳細情報: Iidentity Authority インターフェイス'
title: IIdentityAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
ms.openlocfilehash: 3064a3d95ebe9a098a7cac0766f18654c6fab8b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800137"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority インターフェイス

コードオブジェクトの id キーを管理します。

## <a name="methods"></a>メソッド

|メソッド|説明|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|指定した2つの [IDefinitionIdentity](idefinitionidentity-interface.md) インスタンスが等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::AreReferencesEqual`|指定した2つの [IReferenceIdentity](ireferenceidentity-interface.md) インスタンスが等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|指定した2つの文字列定義 id 表現が等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::AreTextualReferencesEqual`|指定した2つの文字列参照 id 表現が等しいかどうかを示す値を取得します。|
|`IIdentityAuthority::CreateDefinition`|現在のスコープ内のコードオブジェクトを表す新しいインスタンスへのポインターを取得し `IDefinitionIdentity` ます。|
|`IIdentityAuthority::CreateReference`|現在のスコープ内のコードオブジェクトを表す新しいインスタンスへのポインターを取得し `IReferenceIdentity` ます。|
|`IIdentityAuthority::DefinitionToText`|指定したの書式設定された文字列バージョンを取得し `IDefinitionIdentity` ます。|
|`IIdentityAuthority::DefinitionToTextBuffer`|指定したワイド文字バッファーに、指定したの文字列バージョンを格納し `IDefinitionIdentity` ます。|
|`IIdentityAuthority::DoesDefinitionMatchReference`|指定した `IDefinitionIdentity` と `IReferenceIdentity` インスタンスが同じコードオブジェクトを参照しているかどうかを示す値を取得します。|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|指定した文字列が同じコードオブジェクトを参照しているかどうかを示す値を取得します。|
|`IIdentityAuthority::GenerateDefinitionKey`|指定したに対して新しく作成された文字列キーへのポインターを取得し `IDefinitionIdentity` ます。|
|`IIdentityAuthority::GenerateReferenceKey`|指定したに対して新しく作成された文字列キーへのポインターを取得し `IReferenceIdentity` ます。|
|`IIdentityAuthority::HashDefinition`|指定したのハッシュ値を取得し `IDefinitionIdentity` ます。|
|`IIdentityAuthority::HashReference`|指定したのハッシュ値を取得し `IReferenceIdentity` ます。|
|`IIdentityAuthority::ReferenceToText`|指定したの書式設定された文字列バージョンを取得し `IReferenceIdentity` ます。|
|`IIdentityAuthority::ReferenceToTextBuffer`|指定したワイド文字バッファーに、指定したの文字列バージョンを格納し `IReferenceIdentity` ます。|
|`IIdentityAuthority::TextToDefinition`|`IDefinitionIdentity`指定した書式設定された文字列から生成されたインスタンスへのインターフェイスポインターを取得します。|
|`IIdentityAuthority::TextToReference`|`IReferenceIdentity`指定した書式設定された文字列から生成されたインスタンスへのインターフェイスポインターを取得します。|

## <a name="requirements"></a>要件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** 分離 .h

**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
