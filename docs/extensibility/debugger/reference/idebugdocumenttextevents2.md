---
title: IDebugDocumentTextEvents2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f34bb09847659fdfc1dfcbd036aef2a47c8bd5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107671"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
このインターフェイスは、Visual Studio には、デバッグ エンジンによって提供されるソース ドキュメントの変更に関する通知を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、ソース コードに変更を加えてをサポートするためにこのインターフェイスを実装します。 このインターフェイスは、同じオブジェクトを実装するには実装通常、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 呼び出すことによってこのインターフェイスを取得、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>メソッドです。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>インターフェイスがへの呼び出しから取得した、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>メソッドです。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスを呼び出すことによって取得、 [QueryInterface](/cpp/atl/queryinterface)メソッドを[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDocumentTextEvents2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|ドキュメント全体が破棄されたことを示します。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|デバッグ パッケージに、テキストがドキュメントに挿入されたことを通知します。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|テキストがドキュメントから削除されているデバッグ パッケージに通知します。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|デバッグ パッケージ、ドキュメント内のテキストが置き換えられたことを通知します。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|ドキュメント内のテキスト属性が更新されているデバッグ パッケージに通知します。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|ドキュメントの属性が更新されているイベントの受信側に通知します。|  
  
## <a name="remarks"></a>コメント  
 だけで、各自のドキュメントを提供するデバッグ エンジンを活用、`IDebugDocumentTextEvent2`インターフェイスです。 この例は、スクリプトのデバッグ エンジンになります。 スクリプトを解釈するには、処理を行って新しいソース コードを生成できますが、ディスク ファイルに存在しないと、DE のみが知っていること。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)