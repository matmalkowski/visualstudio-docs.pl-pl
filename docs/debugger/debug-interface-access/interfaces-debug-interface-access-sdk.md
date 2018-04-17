---
title: Interfejsy (zestaw SDK dostępu do interfejsu debugowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09f1d0496595f3026c7066f4ccfdeb7bc3add6d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)
Metody należą alfabetycznie każdego interfejsu w tabeli treści i na stronie interfejsu w kolejności Vtable.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Zapewnia kontrolę nad jak DIA SDK oblicza wirtualnych i względną wirtualnych adresów dla obiektów debugowania.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Inicjuje dostęp do źródła symboli debugowania.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Zapewnia dostęp do rekordów w strumieniu danych debugowania.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Wylicza różnych strumienie debugowania zawarte w źródle danych.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Wylicza różne elementy danych ramki zawarte w źródle danych.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Wyliczanie różnych źródeł wprowadzony zawarte w źródle danych.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Wylicza różne numery wierszy zawartych w źródle danych.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Wylicza różnych wkładów sekcji zawarte w źródle danych.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Wylicza różnych segmentów zawarte w źródle danych.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Wylicza różnych plików źródłowych zawarte w źródle danych.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Wylicza różnych dostępnych ramek stosu.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Wylicza różne symbole zawarte w źródle danych.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Wylicza według adresu różne symbole zawarte w źródle danych.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Wylicza w różnych tabelach zawartych w źródle danych.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Przedstawia szczegóły ramki stosu.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Przedstawia szczegółowe informacje o podstawowej przesunięcia lokalizacji i pamięci modułu lub obrazu.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Uzyskuje dostęp do kodu źródłowego program przechowywane w źródle danych DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Uzyskuje dostęp do informacji opisano proces mapowania z bloku bajtów tekstu obrazu numer wiersza pliku źródłowego.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Odbiera wywołania zwrotne z symboli DIA lokalizowanie procedury, umożliwiając w ten sposób raport dotyczący postępu próba lokalizacji do interfejsu użytkownika.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Odbiera wywołania zwrotne z symboli DIA lokalizowanie procedury w celu umożliwienia ograniczenia nałożone na lokalizowania procesu.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Umożliwia odczytanie trwałej właściwości zestaw właściwości DIA.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Umożliwia aplikacji klienta przekazać plik wykonywalny określony przez położenie pliku w bajtach.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Umożliwia aplikacji klienta umożliwiają określanie wartości bajtów plik wykonywalny określony przez wirtualny adres względny.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Pobiera dane opisujące wkład sekcji, to znaczy ciągłego bloku pamięci przyczyniły się do obrazu przez compiland.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Mapuje dane z numer sekcji do segmentów przestrzeni adresowej.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Udostępnia kontekst zapytania dla symboli debugowania.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Reprezentuje plik źródłowy.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Opisuje właściwości ramki stosu.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Zapewnia metody do stosu zaprezentuje przy użyciu pliku PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Przechowuje stosu kontekstu między wywołań [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metody.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Umożliwia przejście ze stosu przy użyciu pliku bazy danych (PDB) debugowania programu.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Opisuje właściwości instancji symbolu.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Wylicza DIA tabeli źródła danych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Opisuje, wyliczenia i struktury używane przez różne interfejsy DIA SDK.  
  
 [Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 W tym artykule opisano dostępne w DIA SDK stałe.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)