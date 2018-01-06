---
title: "Idiaenumsectioncontribs — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSectionContribs interface
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c1e1497092e94a176ab3024da65e068f5c982fc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumsectioncontribs"></a>IDiaEnumSectionContribs
Wylicza różnych wkładów sekcji zawarte w źródle danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaEnumSectionContribs`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaEnumSectionContribs::get__NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Pobiera [interfejsu interfejsu IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) wersji ten moduł wyliczający.|  
|[IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|Pobiera liczbę sekcji udziały.|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Pobiera wkładów sekcji za pomocą indeksu.|  
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|Pobiera określoną liczbę sekcji wkładów w kolejności wyliczenia.|  
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|Pomija określoną liczbę sekcji wkładów w kolejności wyliczenia.|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="note-for-callers"></a>Uwaga dla wywoływania  
 Uzyskaj ten interfejs z [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metody. Zapoznaj się z przykładem, aby uzyskać szczegółowe informacje.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak uzyskać ( `GetEnumSectionContribs` funkcji) i użyj ( `ShowSectionContribs` funkcji) `IDiaEnumSectionContribs` interfejsu. Aby uzyskać bardziej szczegółowy przykład przy użyciu sekcji wkładów, zobacz [idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md) interfejsu.  
  
```C++  
  
      IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);  
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
  
void ShowSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pEnumSectionContribs;  
  
    pEnumSectionContribs = GetEnumSectionContribs(pSession);  
    if (pSectionContrib != NULL)  
    {  
        IDiaSectionContrib* pSectionContrib;  
        ULONG celt = 0;  
  
        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintSectionContrib(pSectionContrib, pSession);  
            pSectionContrib->Release();  
        }  
        pSectionContrib->Release();   
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)