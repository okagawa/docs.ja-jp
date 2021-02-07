---
description: '詳細情報: SetManifestFile メソッド'
title: SetManifestFile メソッド
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: fe91c7f2b4e6f58a0a740de84e055ead49adb77d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662326"
---
# <a name="setmanifestfile-method"></a>SetManifestFile メソッド

リンカーがアセンブリを作成するときに使用するマニフェストファイルを指定またはリセットできます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  

 `pszFile`  
  
 コンテンツが Win32 リソース blob に格納されるマニフェストファイルの名前。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK を返します。  
  
## <a name="remarks"></a>解説  

 Win32ResBlob を要求する前に、これを呼び出します。 パラメーターの値 `pszFile` は、コンテンツが読み取られ、ID が RT_MANIFEST の Win32 リソースに配置されるマニフェストファイルの名前です。 NULL のパラメーターを使用して呼び出されると、以前に読み取られたマニフェストはクリアされます。 これにより、1つのリンカーの状態を初期化時間にリセットできます。  
  
## <a name="requirements"></a>要件  

 ALink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink3 インターフェイス](ialink3-interface.md)
- [ALink API](index.md)
- [IALink インターフェイス](ialink-interface.md)
- [Al.exe (アセンブリ リンカー)](../../tools/al-exe-assembly-linker.md)
