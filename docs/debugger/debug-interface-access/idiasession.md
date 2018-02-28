---
title: "Idiasession — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f3939ab86cd9f0948a2be44756b9ed94d143ecc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasession"></a>IDiaSession
Udostępnia kontekst zapytania dla symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDiaSession`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Pobiera adres obciążenia dla pliku wykonywalnego, który odpowiada symboli w tym magazynie symboli. To jest taka sama jak wartość została przekazana do `put_loadAddress` metody.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Ustawia adres obciążenia dla pliku wykonywalnego, który odpowiada symboli w tym magazynie symboli. **Uwaga:** ważne jest, aby wywołać tę metodę, gdy zostanie wyświetlony `IDiaSession` obiektu i przed rozpoczęciem korzystania z obiektu.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Pobiera odwołanie do zakresu globalnego.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Pobiera moduł wyliczający dla wszystkich tabel znajdujących się w magazynie symboli.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Pobiera moduł wyliczający dla wszystkie nazwane symbole w lokalizacjach statycznych.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Pobiera wszystkie elementy podrzędne elementu identyfikator określonego elementu nadrzędnego, zgodnych z typem nazwę i symbol.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Pobiera typ określony symbol, który zawiera lub zbliżony do określonego adresu.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Pobiera typ określony symbol, który zawiera lub zbliżony do określonej wirtualnej adresem względnym (RVA).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Pobiera typ określony symbol, który zawiera lub najbliższy określony adres wirtualny (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Pobiera symbol, który zawiera token określonych metadanych.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Sprawdza, czy dwa symbole są równoważne.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Pobiera symbol przez jego unikatowy identyfikator.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Pobiera typ określony symbol, który zawiera lub najbliższy określony wirtualny adres względny i przesunięcie.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Pobiera typ określony symbol, który zawiera lub najbliższy określony wirtualny adres i przesunięcie.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Pobiera compiland i nazwa pliku źródłowego.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Pobiera pliku źródłowego przez identyfikator pliku źródłowego.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Pobiera numerów wierszy w ramach określonej źródłowe i compiland identyfikator pliku.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Pobiera wierszy w określonych compiland, które zawierają określony adres.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Pobiera wierszy w określonych compiland, które zawierają określony wirtualny adres względny.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Odnajduje informacje numer wiersza dla wierszy zawartych w dla określonego zakresu adresów.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Pobiera wierszy w określonych compiland przez źródło pliku i numer wiersza.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Pobiera źródło, który został umieszczony w magazynie symboli przez dostawców atrybut lub innych części procesu kompilacji.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Pobiera sekwencję wyliczany debugowania strumieni danych.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Pobiera wyliczenie umożliwia klientowi iterację wszystkie ramki wbudowane w podanym adresem.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Pobiera wyliczenie umożliwia klientowi iterację wszystkie ramki wbudowane w określonej wirtualnej adresem względnym (RVA).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Pobiera wyliczenie umożliwia klientowi iterację wszystkie ramki wbudowane na określony adres wirtualny (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Pobiera wyliczenie umożliwia klientowi Iterowanie za pomocą informacji o numerze linii wszystkie funkcje, które są wbudowane, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Pobiera wyliczenie umożliwia klientowi Iterowanie za pomocą informacji o numerze linii wszystkie funkcje, które są wbudowane, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego i znajdują się w zakresie określonego adresu.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Pobiera wyliczenie umożliwia klientowi Iterowanie za pomocą informacji o numerze linii wszystkie funkcje, które są wbudowane, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego, który są zawarte w określonej wirtualnej adres względny (RVA).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Pobiera wyliczenie umożliwia klientowi Iterowanie za pomocą informacji o numerze linii wszystkie funkcje, które są wbudowane, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego i znajdują się w określonym wirtualnego adresu (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Pobiera wyliczenie umożliwia klientowi iterację informacja o numerach wierszy wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio w określonym źródle liczbę plików i wierszy.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Pobiera wyliczenie umożliwia klientowi iterację informacja o numerach wierszy wszystkich funkcji śródwierszowych, zgodne określonej nazwy.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Zwraca wyliczenie symboli dla zmiennej, która odpowiada wartości określonego tagu w obiekcie nadrzędnym funkcja stub akceleratora.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Biorąc pod uwagę odpowiadającą mu wartość tagu, ta metoda zwraca wyliczenie symboli, które są zawarte w funkcji stub akceleratora określonego elementu nadrzędnego pod określonym adresem względnym wirtualnego.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Zwraca wyliczenie symboli dla ramki wbudowane odpowiadający wbudowanego określonej nazwy funkcji.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Zwraca wyliczenie symboli dla ramek wbudowanych, które odpowiadają na określoną lokalizacją źródłową.|  
  
## <a name="remarks"></a>Uwagi  
 Ważne jest, aby wywołać [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metody po utworzeniu `IDiaSession` obiektu — i wartość przekazana do `put_loadAddress` metoda musi być różna od zera — wszystkie właściwości wirtualnego adresu (VA) symboli jako dostępny. Adres obciążenia pochodzi z niezależnie od programu załadowany plik wykonywalny debugowania. Na przykład można wywołać funkcji Win32 `GetModuleInformation` można pobrać adresu obciążenia dla pliku wykonywalnego, podane dojście do pliku wykonywalnego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak uzyskać `IDiaSession` interfejsu jako część ogólne inicjowanie DIA SDK.  
  
```C++  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Wywołanie pliku exe](../../debugger/debug-interface-access/exe.md)   
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)