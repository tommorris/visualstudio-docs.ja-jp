---
title: IDebugSymbolProvider::GetAddressesFromPosition |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 129ed233361991f5e58a258c73838bc9739112de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118532"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
このメソッドは、デバッグのアドレスの配列を作成するドキュメントの位置をマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pDocPos`  
 [in]ドキュメントの位置。  
  
 `fStatmentOnly`  
 [in]TRUE の場合は、1 つのステートメントにデバッグ アドレスを制限します。  
  
 `ppEnumBegAddresses`  
 [out]このステートメントまたは行に関連付けられている開始デバッグ アドレスの列挙子を返します。  
  
 `ppEnumEndAddresses`  
 [out]返します、 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)このステートメントまたは行に関連付けられている終了デバッグ アドレスの列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ドキュメントの位置は、通常、ソース行の範囲を示します。 このメソッドは、開始し、これらの行に関連付けられているアドレスのデバッグを終了します。 一部の言語では、ステートメントで複数の行または複数のステートメントを含む行にまたがるできるようにします。 このメソッドは、1 つのステートメントにデバッグ アドレスを制限するためのフラグを提供します。  
  
 テンプレートの場合と同様に、デバッグの複数のアドレスを 1 つのステートメントのことができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)