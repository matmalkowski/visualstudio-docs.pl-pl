---
title: IDebugComPlusSymbolProvider2::IsAddressSequencePoint | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::IsAddressSequencePoint
- IsAddressSequencePoint
ms.assetid: 89b27c57-5295-428b-8229-a402500d8cd3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b6c3fc4743ca66f490813324b3183dbd8632a802
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcomplussymbolprovider2isaddresssequencepoint"></a>IDebugComPlusSymbolProvider2::IsAddressSequencePoint
Określa, czy adres określony debugowania punktu sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsAddressSequencePoint(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsAddressSequencePoint(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Debugowanie adres, który jest reprezentowany przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli adres debugowania jest punktu sekwencji, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę do **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfejsu.  
  
```cpp  
HRESULT CDebugSymbolProvider::IsAddressSequencePoint(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pAddress, E_INVALIDARG );  
  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsSequencePoint( address.addr.addr.addrMethod.tokMethod,  
                                   address.addr.addr.addrMethod.dwVersion,  
                                   address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates this is not a sequence point  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)