---
title: Trust プロトコルが混在するフェデレーション シナリオ
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248176"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Trust プロトコルが混在するフェデレーション シナリオ

シナリオによっては、フェデレーション クライアントが、Trust バージョンの一致しないサービスやセキュリティ トークン サービス (STS: Security Token Service) と通信する場合があります。 たとえば、サービス WSDL に、STS とは異なるバージョンの WS-Trust 要素を持つ `RequestSecurityTokenTemplate` アサーションが含まれることがあります。 このような場合、Windows Communication Foundation (WCF) クライアントは、から受信した WS-Trust 要素 `RequestSecurityTokenTemplate` を、STS 信頼バージョンと一致するように変換します。 WCF は、標準バインディングに対してのみ、不一致の信頼バージョンを処理します。 WCF によって認識されるすべての標準アルゴリズムパラメーターは、標準バインディングの一部です。 このトピックでは、サービスと STS の間のさまざまな信頼設定を使用した WCF の動作について説明します。  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP 2005/02 および STS 2005/02  

 証明書利用者 (RP: Relying Party) の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 WCF では、クライアントとサービスの両方のパラメーターを区別できません。すべてのパラメーターが追加され、(RST) に送信され `RequestSecurityTokenTemplate` ます。  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP Trust 1.3 および STS Trust 1.3  

 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParameters` 要素が含まれます。  
  
 `EncryptionAlgorithm` `CanonicalizationAlgorithm` `KeyWrapAlgorithm` これらが要素内に存在する場合、WCF は、RST の最上位の要素から、、およびの各要素を削除し `SecondaryParameters` ます。 WCF は、 `SecondaryParameters` 変更されていない送信 RST に要素を追加します。  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP Trust 2005/02 および STS Trust 1.3  

 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 WCF では、クライアント構成ファイルからサービスパラメーターとクライアントパラメーターを区別できません。 したがって、WCF は、すべてのパラメーターを信頼バージョン1.3 名前空間に変換します。  
  
 WCF は `KeyType` 、、、およびの各要素を次のように処理し `KeySize` `TokenType` ます。  
  
- WSDL をダウンロードし、バインディングを作成して、`KeyType`、`KeySize`、および `TokenType` を RP パラメーターから割り当てます。 その後、クライアント構成ファイルが生成されます。  
  
- この時点で、クライアントは構成ファイル内のパラメーターを変更できます。  
  
- 実行時に、WCF は、、、およびを除く、クライアント構成ファイルのセクションに指定されたすべてのパラメーターをコピーし `AdditionalTokenParameters` `KeyType` `KeySize` `TokenType` ます。これは、これらのパラメーターは構成ファイルの生成時に考慮されるためです。  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP Trust 1.3 および STS Trust 2005/02  

 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParamters` 要素が含まれます。  
  
 WCF は、セクション内で指定されたすべてのパラメーター `SecondaryParameters` を最上位の RST 要素にコピーしますが、2005 WS-Trust 名前空間には変換しません。
