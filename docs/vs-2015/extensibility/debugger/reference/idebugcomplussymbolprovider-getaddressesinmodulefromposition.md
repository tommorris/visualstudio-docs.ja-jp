---
title: IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetAddressesInModuleFromPosition
- IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
ms.assetid: f901c66e-f53c-4ea0-8004-d8fcbf46f916
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c865704e8845e56c93132e3be370783f2dcbd66e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544484"
---
# <a name="idebugcomplussymbolprovidergetaddressesinmodulefromposition"></a>IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition)します。  
  
デバッグ アドレスの配列を指定したモジュールのドキュメントの位置をマップします。  
  
## <a name="syntax"></a>構文  
  
```  
[C++]  
HRESULT GetAddressesInModuleFromPosition(  
   ULONG32                  ulAppDomainID,  
   GUID                     guidModule,  
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```  
[C#]  
int GetAddressesInModuleFromPosition(  
   uint                    ulAppDomainID,  
   Guid                    guidModule,  
   IDebugDocumentPosition2 pDocPos,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ulAppDomainID`  
 [in]アプリケーション ドメインの識別子です。  
  
 `guidModule`  
 [in]モジュールの一意の識別子。  
  
 `pDocPos`  
 [in]ドキュメントの位置。  
  
 `fStatmentOnly`  
 [in]場合`TRUE`、1 つのステートメントにデバッグ アドレスを制限します。  
  
 `ppEnumBegAddresses`  
 [out]このステートメントまたは行に関連付けられているデバッグの開始アドレスの列挙子を返します。  
  
 `ppEnumEndAddresses`  
 [out]このステートメントまたは行に関連付けられている終了のデバッグ アドレスの列挙子を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CDebugSymbolProvider**を公開するオブジェクト、 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)インターフェイス。  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPosition(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugDocumentPosition2* pDocPos,  
    BOOL fStatementOnly,  
    IEnumDebugAddresses** ppEnumBegAddresses,  
    IEnumDebugAddresses** ppEnumEndAddresses  
)  
{  
    GUID guidNULL = {0};  
  
    if (guidNULL == guidModule)  
    {  
        return GetAddressesInAppDomainFromPosition( ulAppDomainID,  
                pDocPos,  
                fStatementOnly,  
                ppEnumBegAddresses,  
                ppEnumEndAddresses );  
    }  
    else  
    {  
        return GetAddressesInModuleFromPositionHelper( ulAppDomainID,  
                guidModule,  
                pDocPos,  
                fStatementOnly,  
                ppEnumBegAddresses,  
                ppEnumEndAddresses );  
    }  
}  
  
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugDocumentPosition2* pDocPos,  
    BOOL fStatementOnly,  
    IEnumDebugAddresses** ppEnumBegAddresses,  
    IEnumDebugAddresses** ppEnumEndAddresses  
)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrFileName;  
    TEXT_POSITION posBeg;  
    TEXT_POSITION posEnd;  
    DWORD dwLine;  
    USHORT segRet = 0;  
    ULONG offRet = 0;  
    CAddrList listAddr;  
    CAddrList listAddrEnd;  
    CAddrList* plistAddrEnd = NULL;  
    bool fFileFound = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    DWORD dwListCount;  
    bool fFoundAddresses = false;  
    CComPtr<CModule> pmodule;  
    DWORD dwBegCol = 0;  
    DWORD dwEndCol = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pDocPos, IDebugDocumentPosition2));  
    ASSERT(IsValidWritePtr(ppEnumBegAddresses, IEnumDebugAddresses*));  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper);  
  
    // Bail on Invalid Args  
  
    IfFalseGo( pDocPos && ppEnumBegAddresses, E_INVALIDARG );  
  
    *ppEnumBegAddresses = NULL;  
    if (ppEnumEndAddresses)  
    {  
        *ppEnumEndAddresses = NULL;  
        plistAddrEnd = &listAddrEnd;  
    }  
  
    // Get the Position  
  
    IfFailGo( pDocPos->GetFileName(&bstrFileName) );  
    IfFailGo( pDocPos->GetRange(&posBeg, &posEnd) );  
  
    // Iterate over the module list accumulating addresses  
    // that match the position  
  
    dwLine = posBeg.dwLine;  
    IfFailGo( GetModule( idModule, &pmodule ) );  
    dwListCount = listAddr.GetCount();  
  
    if ( fStatementOnly )  
    {  
        dwBegCol = posBeg.dwColumn;  
        dwEndCol = posBeg.dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);  
    }  
    else  
    {  
        dwBegCol = 0;  
        dwEndCol = DWORD( -1);  
    }  
  
    while (!fFoundAddresses && dwLine <= posEnd.dwLine )  
    {  
        hr = pmodule->GetAddressesFromLine( bstrFileName,  
                                            dwLine,  
                                            posEnd.dwLine,  
                                            dwBegCol,  
                                            dwEndCol,  
                                            &listAddr,  
                                            plistAddrEnd );  
  
        dwLine++;  
        dwBegCol = 0;  
        dwEndCol = dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);  
  
        if (hr == E_SH_INVALID_POSITION)  
        {  
            fFileFound = true;  
            break;  
        }  
  
        if (FAILED(hr))  
        {  
            // Move on to the next module  
            break;  
        }  
  
        fFileFound = true;  
        fFoundAddresses = listAddr.GetCount() != dwListCount;  
    }  
  
    // Distinguish no file from bad position in the file  
    IfFalseGo( fFileFound, E_SH_FILE_NOT_FOUND);  
  
    // If the list is empty the position is bad  
    IfFalseGo( listAddr.GetCount(), E_SH_INVALID_POSITION );  
  
    // Create enumerators  
    IfFailGo( CreateEnumerator( ppEnumBegAddresses, &listAddr ) );  
    if (ppEnumEndAddresses)  
    {  
        IfFailGo( CreateEnumerator( ppEnumEndAddresses, &listAddrEnd ) );  
    }  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper, hr);  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

