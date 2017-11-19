---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LoadSymbolsFromCallback
- IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
ms.assetid: 905315ba-8e9b-4889-b9da-98e1441950ad
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed597883afa0b0a1e208285e8e94d17e7b0d0299
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromcallback"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
Ładunki debugowania symboli za pomocą metody określonej wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadSymbolsFromCallback(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   BSTR      bstrModuleName,  
   BSTR      bstrSymSearchPath,  
   IUnknown* pCallback  
);  
```  
  
```csharp  
int LoadSymbolsFromCallback(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   object pUnkMetadataImport,  
   object pUnkCorDebugModule,  
   string bstrModuleName,  
   string bstrSymSearchPath,  
   object pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ulAppDomainID`  
 [in] Identyfikator domeny aplikacji.  
  
 `guidModule`  
 [in] Unikatowy identyfikator modułu.  
  
 `pUnkMetadataImport`  
 [in] Obiekt zawierający metadane symbolu.  
  
 `pUnkCorDebugModule`  
 [in] Obiekt, który implementuje [ICorDebugModule — interfejs](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).  
  
 `bstrModuleName`  
 [in] Nazwa modułu.  
  
 `bstrSymSearchPath`  
 [in] Ścieżka wyszukiwania pliku symboli.  
  
 `pCallback`  
 [in] Obiekt, który reprezentuje metodę wywołania zwrotnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę do **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfejsu.  
  
```cpp  
HRESULT CDebugSymbolProvider::LoadSymbolsFromCallback(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IUnknown *pMetadataImport,  
    IUnknown * _pCorModule,  
    BSTR bstrModule,  
    BSTR bstrSearchPath,  
    IUnknown *pCallback)  
{  
    EMIT_TICK_COUNT("Entry -- Loading symbols for the following target:");  
    USES_CONVERSION;  
    EmitTickCount(W2A(bstrModule));  
  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    bool fSymbolsLoaded = false;  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pMetadataImport, E_INVALIDARG );  
    IfFalseGo( _pCorModule, E_INVALIDARG );  
  
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**)&pMetadata) );  
  
    IfFailGo( _pCorModule->QueryInterface( IID_ICorDebugModule,  
                                           (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    //  
    //  We are now allowing modules to be created that do not have SymReaders.  
    //  It is likely there are a number of corner cases being ignored  
    //  that will require knowledge of the hr result below.  
    //  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
    HRESULT hrLoad = pmoduleNew->Create( idModule,  
                                         dwCurrentState,  
                                         pMetadata,  
                                         pCorModule,  
                                         bstrModule,  
                                         bstrSearchPath,  
                                         pCallback );  
  
    if (hrLoad == S_OK)  
    {  
        fSymbolsLoaded = true;  
    }  
  
    // Remove the old module  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule( pmodule );  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    if (SUCCEEDED(hr) && !fSymbolsLoaded)  
    {  
        hr = hrLoad;  
    }  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
    EMIT_TICK_COUNT("Exit");  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)