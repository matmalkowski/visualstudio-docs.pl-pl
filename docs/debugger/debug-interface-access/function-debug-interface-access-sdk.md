---
title: Funkcja (Debug Interface Access SDK) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5989a2c03c5a6e3f829c0183c797204e3311f5d2
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="function-debug-interface-access-sdk"></a>Funkcja (Zestaw SDK dostępu do interfejsu debugowania)
Każda funkcja jest określana przez `SymTagFunction` symbolu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|`Data type`|Opis|  
|--------------|-----------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Jedna z wartości z [cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md), jeśli funkcja jest funkcją członkowską.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięcie część lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Część sekcji lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol dla tej klasy, jeśli funkcja jest funkcją członkowską.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator klasy nadrzędnej symbolu.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`Jeśli funkcja jest oznaczona jako stała.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Jeśli funkcja używa niestandardowych Konwencja wywoływania (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Jeśli funkcja wykonuje dalekiego powrotu (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE`Jeśli funkcja korzysta z funkcji alokacji pamięci (uinnder DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE`Jeśli funkcja zawiera wyjątek C++ stylu obsługi (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE`Jeśli funkcja zawiera, obsługa wyjątków asynchronicznych (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE`Jeśli funkcja zawiera zestaw wbudowany (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE`Jeśli funkcja zawiera [longjmp](/cpp/c-runtime-library/reference/longjmp) wywołania (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`Jeśli funkcja zawiera kontroli zabezpieczeń (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE`Jeśli funkcja zawiera wyjątek Win32 stylu strukturę obsługi (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE`Jeśli funkcja zawiera [setjmp](/cpp/c-runtime-library/reference/setjmp) wywołania (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Jeśli funkcja ma typ zwracany przerwań (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE`Jeśli funkcja jest wprowadzenie wirtualnego.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE`Jeśli funkcja została oznaczona z jednym z [w tekście, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp) atrybutów.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE`Jeśli funkcja jest oznaczony atrybutem [naked](/cpp/cpp/naked-cpp) atrybutu (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`Jeśli funkcja jest statyczny (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Liczba bajtów kodu funkcji, zaczynając od lokalizacji.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol compiland otaczającej.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Funkcje mogą mieć statyczny lub metadane lokalizacji; Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa funkcji.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Jeśli funkcja nie jest wbudowaną funkcją (tylko n DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Jeśli funkcja nie jest dostępny (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Jeśli funkcja nie zwraca wartości (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE`Jeśli funkcja został skompilowany z sprawdzanie zabezpieczeń bufora, ale kolejność stosu nie może być wykonana.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Jeśli kod ma informacje debugowania zoptymalizowanego kodu (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE`Jeśli funkcja jest czysty wirtualnego.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie tej funkcji w ramach jego moduł.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagFunction` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Token metadanych dla funkcji.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol dla podpisu funkcji.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator typu symbolu.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`Jeśli funkcja znajduje się niewyrównany.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Formularzu bez nazwy funkcji (tylko w DIA SDK w wersji 8.0 lub nowszym)|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Część lub całość formularzu bez nazwy funkcji (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`Jeśli funkcję wirtualną.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja tej funkcji w ramach obrazu wykonywalnego.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Jeśli funkcją wirtualną, a następnie przesunięcie w tabeli funkcji wirtualnych.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`Jeśli funkcja jest oznaczona jako trwałe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)