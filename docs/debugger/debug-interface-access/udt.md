---
title: UDT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SymTagUDT symbol
- user-defined type (UDT) symbol
- unions, as symbols
- UDT symbol
- structs [C++]
ms.assetid: f12459dd-c64d-4cc9-9ee3-a56e19e9e573
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a2892a72a07f11a9026b6c76c9e991729b16e1a6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="udt"></a>UDT
Każdej klasy, struktury i Unii jest identyfikowany przez `SymTagUDT` symbolu. Każdy element członkowski, funkcja danych, lub typu zagnieżdżonego i każdej klasy podstawowej, pojawia się jako element podrzędny klasy typ zdefiniowany przez użytkownika (UDT).  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono dodatkowe prawidłowe właściwości dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol nadrzędnej klasy, jeśli istnieje.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator klasy nadrzędnej symbolu.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE`Jeśli UDT ma on konstruktora.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`Jeśli UDT jest oznaczona jako stała.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE`Jeśli UDT ma wszystkie operatory przypisania zdefiniowane.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE`Jeśli UDT ma wszystkie operatory rzutowania zdefiniowane.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE`Jeśli UDT ma definicji typów zagnieżdżonych.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Rozmiar w bajtach typu.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol otaczającej [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa typu.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE`Jeśli UDT jest zagnieżdżony.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE`Jeśli przeciążone operatory są zdefiniowane dla typu.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE`Jeśli spakowane UDT.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE`Jeśli UDT pojawia się w zakresie leksykalne nieglobalnych.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagUDT` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Wskazuje, czy jest to struktura, klasy lub union; Aby uzyskać więcej informacji, zobacz [udtkind — wyliczenie](../../debugger/debug-interface-access/udtkind.md).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`w przypadku niewyrównany UDT.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Typ wirtualnej tabeli.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|Identyfikator tabeli wirtualnej symbol kształtu.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`Jeśli UDT jest oznaczona jako trwałe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)