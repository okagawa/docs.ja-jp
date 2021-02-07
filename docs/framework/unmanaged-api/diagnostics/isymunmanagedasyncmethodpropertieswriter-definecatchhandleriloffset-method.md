---
description: '詳細について: ISymUnmanagedAsyncMethodPropertiesWriter::D efineCatchHandlerILOffset メソッド'
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: fcb2c6efa7ea83252a46a9b08cdfa7b2c14f09d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737793"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド

非同期メソッドをラップする、コンパイラによって生成される catch ハンドラーの IL オフセットを設定します。  
  
 生成された catch の IL オフセットは、ユーザーコードメソッドで発生する可能性があっても、ユーザーコード以外のコードであると仮定して、catch を処理するためにデバッガーによって使用されます。 特に、 **CatchHandlerFound** exception イベントに応答して使用されます。  
  
## <a name="syntax"></a>構文  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>戻り値  

 `HRESULT` が返されます。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](isymunmanagedasyncmethodpropertieswriter-interface.md)
