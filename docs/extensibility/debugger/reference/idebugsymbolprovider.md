---
title: IDebugSymbolProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de77e30f0e9f52af10eef1757048a078d6d4a583
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Ten interfejs reprezentuje dostawcę symbol, który zawiera symbole i typy, zwracając je jako pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symbol muszą implementować ten interfejs podanie symbol i podać informacje, aby ewaluatora wyrażeń.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest uzyskać za pomocą modelu COM `CoCreateInstance` — funkcja (dla dostawców symbol niezarządzanego) lub przez ładowanie odpowiednie zarządzany zestaw kodu i tworzenia wystąpienia dostawcy symbol, w oparciu o informacje znajdujące się w tym zestawie. Aparat debugowania tworzy wystąpienie dostawcy symbol do pracy w połączeniu z ewaluatora wyrażenia. Zobacz przykład jeden ze sposobów tworzenia wystąpienia tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugSymbolProvider`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|`Initialize`|Przestarzałe. Nie używać.|  
|`Uninitialize`|Przestarzałe. Nie używać.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Pobiera pola, które zawiera adres debugowania.|  
|`GetField`|Przestarzałe. Nie używać.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapuje położenie dokumentu na tablicę adresów debugowania.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapuje kontekstu dokumentu na tablicę adresów debugowania.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapuje adres debugowania do kontekstu dokumentu.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Pobiera język używany do kompilowania kodu pod adresem debugowania.|  
|`GetGlobalContainer`|Przestarzałe. Nie używać.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Pobiera pole reprezentujący nazwę FQDN metody.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Pobiera typ pola Klasa reprezentująca w pełni kwalifikowaną nazwę klasy.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Tworzy moduł wyliczający dla przestrzeni nazw skojarzonych z tym adresem debugowania.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapuje nazwy symbolu typ symbolu.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Pobiera adres debugowania, znajdujący się na adres danego debugowania w metodzie.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs mapuje pozycji dokumentu na adresy debugowania i na odwrót.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak można utworzyć wystąpienia dostawcy symbol danego identyfikatora GUID (aparat debugowania musi znać tej wartości).  
  
```cpp  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugSymbolProvider *pProvider = NULL;  
    if (pSymbolProviderGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetSPMetric(*pSymbolProviderGuid,  
                      storetypeFile,  
                      metricCLSID,  
                      &clsidProvider,  
                      strRegistrationRoot);  
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {  
            // No file type provider, try metadata provider.  
            ::GetSPMetric(*pSymbolProviderGuid,  
                          ::storetypeMetadata,  
                          metricCLSID,  
                          &clsidProvider,  
                          strRegistrationRoot);  
        }  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugSymbolProvider> spSymbolProvider;  
            spSymbolProvider.CoCreateInstance(clsidProvider);  
            if (spSymbolProvider != NULL) {  
                pProvider = spSymbolProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)