---
description: '詳細情報: CompareAssemblyIdentity 関数'
title: CompareAssemblyIdentity 関数
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
ms.openlocfilehash: aa55d1ea0b1968ec4e50106139e154e29e159ec7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761214"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity 関数

2つのアセンブリ id を比較して、それらが等しいかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a>パラメーター  

 `pwzAssemblyIdentity1`  
 から比較対象の最初のアセンブリのテキスト id。  
  
 `fUnified1`  
 からのユーザー指定の統一を示すブール型のフラグ `pwzAssemblyIdentity1` 。  
  
 `pwzAssemblyIdentity2`  
 から比較対象の2番目のアセンブリのテキスト id。  
  
 `fUnified2`  
 からのユーザー指定の統一を示すブール型のフラグ `pwzAssemblyIdentity2` 。  
  
 `pfEquivalent`  
 入出力2つのアセンブリが等しいかどうかを示すブール型のフラグ。  
  
 `pResult`  
 入出力比較に関する詳細情報を含む [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) 列挙です。  
  
## <a name="return-value"></a>戻り値  

 `pfEquivalent` 2つのアセンブリが等しいかどうかを示すブール値を返します。 `pResult` 値の1つを返し `AssemblyComparisonResult` 、の値のより詳細な理由を指定し `pfEquivalent` ます。  
  
## <a name="remarks"></a>解説  

 `CompareAssemblyIdentity` とが等価かどうかを確認し `pwzAssemblyIdentity1` `pwzAssemblyIdentity2` ます。 `pfEquivalent` は `true` 、次の条件の1つ以上でに設定されます。  
  
- 2つのアセンブリ id は同等です。 厳密な名前が付けられたアセンブリの場合、等価性には、アセンブリ名、バージョン、公開キートークン、およびカルチャが同一である必要があります。 単純な名前付きアセンブリの場合、等価性にはアセンブリ名とカルチャの一致が必要です。  
  
- どちらのアセンブリ id も、.NET Framework で実行されるアセンブリを参照します。 この条件は `true` 、アセンブリのバージョン番号が一致しない場合でもを返します。  
  
- 2つのアセンブリはマネージアセンブリではありませんが、 `fUnified1` または `fUnified2` がに設定されてい `true` ます。  
  
 フラグは、 `fUnified` 厳密な名前が付けられたアセンブリのバージョン番号までのすべてのバージョン番号が、厳密に名前が付けられたアセンブリと同等であると見なされることを示します。 たとえば、の値 `pwzAssemblyIndentity1` が "MyAssembly, version = 3.0.0.0, culture = ニュートラル, publicKeyToken =..." で、の値がの場合、 `fUnified1` `true` バージョン0.0.0.0 から3.0.0.0 のすべてのバージョンの MyAssembly が同等として扱われることを示します。 このような場合、 `pwzAssemblyIndentity2` がと同じアセンブリを参照している場合は、 `pwzAssemblyIndentity1` バージョン番号が低い点が `pfEquivalent` に設定され `true` ます。 が `pwzAssemblyIdentity2` より上位のバージョン番号を参照している場合、 `pfEquivalent` の値がである場合にのみがに設定され `true` `fUnified2` `true` ます。  
  
 パラメーターには、 `pResult` 2 つのアセンブリが同等であるかどうかについての特定の情報が含まれます。 詳細については、「 [AssemblyComparisonResult 列挙型](assemblycomparisonresult-enumeration.md)」を参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](fusion-global-static-functions.md)
- [AssemblyComparisonResult 列挙型](assemblycomparisonresult-enumeration.md)
