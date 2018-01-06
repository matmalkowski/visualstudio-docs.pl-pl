---
title: Etykieta (Debug Interface Access SDK) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 090ed3ca526a2fb7d36a2b6c81d2563ba254dc07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="label-debug-interface-access-sdk"></a>Etykieta (Zestaw SDK dostępu do interfejsu debugowania)
Lokalizacja w kodzie programu jest identyfikowany przez `SymTagLabel` symbolu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięcie część lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Część sekcji lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Jeśli etykieta używa konwencji wywoływania niestandardowych.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Jeśli etykieta wykonuje dalekiego powrotu.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Jeśli etykieta zawiera typ zwracany przerwania.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol otaczającego compiland, bloku lub funkcji.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Etykiety mają statyczne lokalizacji; Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md) wyliczenia.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa etykiety.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Jeśli nie określono etykiety z [noinline](/cpp/cpp/noinline) atrybutu.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Jeśli nie określono etykiety z [noreturn](/cpp/cpp/noreturn) atrybutu.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Jeśli nigdy nie nosi nazwę etykiety.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Przesunięcie symbolu w pamięci. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Jeśli kod ma informacje debugowania zoptymalizowanego kodu.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie tej etykiety jego modułu.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagFuncDebugLabel` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja ta etykieta obrazu wykonywalnego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)