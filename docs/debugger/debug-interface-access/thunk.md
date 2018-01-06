---
title: Thunk | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thunk properties [DIA SDK]
- thunk symbol
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2dc847378510a6c7b0c07834a7658874f94b764e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="thunk"></a>Thunk
Każdy `thunk` jest identyfikowany przez `SymTagThunk` tagu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Atrybut modyfikator dostępu do jednego z [cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md) wartości (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięcie część lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Część sekcji lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Otaczającej klasy nadrzędnej, czy dowolne (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator otaczającego symbol nadrzędnej klasy (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|Wartość TRUE, jeśli konwersja jest oznaczona jako stała (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|Wartość TRUE, jeśli konwersja jest wprowadzenie do funkcji wirtualnych (tylko w DIA SDK w wersji 8.0 lub nowszym)|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|Wartość TRUE, jeśli konwersja jest uznawane za statyczne (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Liczba bajtów kodu w thunk.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol otaczającego compiland, bloku lub funkcji.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Punkty końcowe mają statyczne lokalizacji. Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md) wyliczenia.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa thunk.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|Wartość TRUE, jeśli konwersja jest czysto wirtualny (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie tego thunk jego modułu.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagThunk` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Część lokalizacji docelowej thunk przesunięcia.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Względne wirtualny adres docelowy thunk w jego otaczającym bloku.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Część sekcji thunk obiektu docelowego.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Pozycja elementu docelowego thunk w obrazu wykonywalnego.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Konwersji bitowej typu, zgodnie z definicją w [thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Typ tego thunk (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator typu symbolu (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`Jeśli konwersja nie jest wyrównany (tylko w DIA SDK w wersji 8.0 lub nowszego)|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`Jeśli konwersja jest wirtualna (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja tego thunk w obrębie obrazu wykonywalnego.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Przesunięcie w tabeli wirtualnej do tego thunk (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`Jeśli konwersja jest oznaczona jako volatile (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [Thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)