---
title: "Idiaenuminjectedsources — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumInjectedSources interface
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc5773f3cadaaf2c2a4a57c3fd8b381ca3f5d43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenuminjectedsources"></a>IDiaEnumInjectedSources
Wyliczanie różnych źródeł wprowadzony zawarte w źródle danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaEnumInjectedSources : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaEnumInjectedSources`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaEnumInjectedSources::get__NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Pobiera [interfejsu interfejsu IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) wersji ten moduł wyliczający.|  
|[IDiaEnumInjectedSources::get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Pobiera numer wprowadzony źródeł.|  
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Pobiera źródło wprowadzony za pomocą indeksu.|  
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Pobiera określoną liczbę źródeł wprowadzony w kolejności wyliczenia.|  
|[IDiaEnumInjectedSources::Skip](../../debugger/debug-interface-access/idiaenuminjectedsources-skip.md)|Pomija określoną liczbę źródeł wprowadzony w kolejności wyliczenia.|  
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs są uzyskiwane przez wywołanie metody [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md) metodę o nazwie pliku źródłowego określonej, przez wywołanie [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metody za pomocą identyfikatora GUID `IDiaEnumInjectedSources` interfejsu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak uzyskać ( `GetEnumInjectedSources` funkcji) i użyj ( `DumpAllInjectedSources` funkcji) `IDiaEnumInjectedSources` interfejsu. Zobacz [idiapropertystorage —](../../debugger/debug-interface-access/idiapropertystorage.md) interfejs dla implementacji `PrintPropertyStorage` funkcji. Dla danych wyjściowych alternatywnych, zobacz [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) interfejsu.  
  
```C++  
  
IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)  
{  
    IDiaEnumInjectedSources* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);  
    IDiaEnumTables*          pEnumTables = NULL;  
    IDiaTable*               pTable      = NULL;  
    ULONG                    celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
  
void DumpAllInjectedSources( IDiaSession* pSession)  
{  
    IDiaEnumInjectedSources* pEnumInjSources;  
  
    pEnumInjSources = GetEnumInjectedSources(pSession);  
    if (pEnumInjSources != NULL)  
    {  
        IDiaInjectedSource* pInjSource;  
        ULONG celt = 0;  
  
        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&  
              celt == 1)  
        {  
            IDiaPropertyStorage *pPropertyStorage;  
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),  
                                           (void **)&pPropertyStorage) == S_OK)  
            {  
                PrintPropertyStorage(pPropertyStorage);  
                pPropertyStorage->Release();  
            }  
            pInjSource->Release();  
        }  
        pEnumInjSources->Release();  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [Idiapropertystorage —](../../debugger/debug-interface-access/idiapropertystorage.md)   
 [Idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md)