---
title: Dane (zestaw SDK dostępu do interfejsu debugowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cc11de394ab53b1f223b008535efc1d83936de2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="data-debug-interface-access-sdk"></a>Dane (Zestaw SDK dostępu do interfejsu debugowania)
Wszystkie zmienne, takie jak parametry, zmienne lokalne, zmienne globalne i elementów członkowskich klasy, są identyfikowane za pomocą `SymTagData` symboli. Wartości stałe (`LocIsConstant`) również są oznaczone symbolem tego typu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Jeśli pole, następnie jedną z wartości [cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięcie część lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Część sekcji lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE` Jeśli adres tych danych odwołuje się do niego inny symbol.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Pozycja bitu lokalizacji; Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) (nieobsługiwane w wersji 8.0 DIA SDK).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol dla tej klasy, jeśli jest to struktura, Unią lub pola klasy.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator klasy nadrzędnej symbolu.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` Jeśli dane zostały wygenerowane przez kompilator.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Jeśli danych jest oznaczona jako stała.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Jeden z [datakind — wyliczenie](../../debugger/debug-interface-access/datakind.md) wartości.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` Jeśli dane są częścią typu zagregowane dane (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` Jeśli dane są podzielone na agregacji wielu symboli (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Długość bitfield; Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol otaczającego compiland, funkcji lub bloku.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Typy dopuszczalnych lokalizacji; Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa zmiennej.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Przesunięcie od zawartości rejestru; Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Zarejestruj określenia lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie danych w ramach jego blok.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Pobiera numer gniazda danych.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagData` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Token metadanych reprezentujący dane.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol typu zmiennej.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator typu zmiennej symbolu.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Jeśli dane są niewyrównany.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Wartość stałej danych.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja danych w pliku wykonywalnego.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Jeśli dane są oznaczane jako trwałe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md)   
 [Datakind — wyliczenie](../../debugger/debug-interface-access/datakind.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)