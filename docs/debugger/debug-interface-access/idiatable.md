---
title: "Idiatable — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be24edc89328f08199316df8bdedf2ab6391907b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiatable"></a>IDiaTable
Wylicza DIA tabeli źródła danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaTable`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Pobiera [interfejsu interfejsu IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) wersji ten moduł wyliczający.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Pobiera nazwę tabeli.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Pobiera liczbę elementów w tabeli.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Pobiera odwołanie do indeksu określonego wpisu.|  
  
## <a name="remarks"></a>Uwagi  
 Implementuje ten interfejs `IEnumUnknown` metody wyliczania w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop. `IEnumUnknown` Interfejs wyliczenie jest bardziej wydajny Iterowanie po spisu treści niż [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) i [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md) metody.  
  
 Interpretacji `IUnknown` interfejsu zwrócony z albo `IDiaTable::Item` metody lub `Next` — metoda (w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop) jest zależny od typu tabeli. Na przykład jeśli `IDiaTable` interfejsu reprezentuje listę wprowadzony źródeł `IUnknown` interfejsu powinny być odpytywane dla [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie przez wywołanie metody tego interfejsu [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) lub [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) metody.  
  
 Następujące interfejsy są implementowane przy użyciu `IDiaTable` interfejsu (to znaczy można zbadać `IDiaTable` interfejs dla jednego z następujących interfejsów):  
  
-   [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [Idiaenumsourcefiles —](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [Idiaenumsectioncontribs —](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [Idiaenumsegments —](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [Idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [Idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Przykład  
 Pierwsza funkcja `ShowTableNames`, wyświetla nazwy wszystkich tabel w sesji. Druga funkcja `GetTable`, przeszukuje wszystkie tabele dla tabeli, który implementuje interfejs określony. Trzeci funkcji `UseTable`, przedstawia sposób użycia `GetTable` funkcji.  
  
> [!NOTE]
>  `CDiaBSTR`jest klasa, która opakowuje `BSTR` i automatycznie obsługuje zwalnianie ciąg, gdy podczas tworzenia wystąpienia wykracza poza zakres.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)