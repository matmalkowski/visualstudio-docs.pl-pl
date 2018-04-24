---
title: Element TypeDef (Debug Interface Access SDK) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Typedef symbol [DIA SDK]
ms.assetid: 9ab441b9-cc72-47fa-83e2-87b3c2b891b4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: edca4602363dae069fa4b214a95a94453ef9a1b9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="typedef-debug-interface-access-sdk"></a>Typedef (Zestaw SDK dostępu do interfejsu debugowania)
Symbole z `SymTagTypedef` tagi wprowadzenie nazwy dla innych typów.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono dodatkowe prawidłowe właściwości dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Jeden z [basictype — wyliczenie](../../debugger/debug-interface-access/basictype.md) wartości.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Klasy nadrzędne tego TypeDef, jeśli istnieje.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator klasy nadrzędnej symbolu.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` Jeśli ten element typedef ma on konstruktora.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Jeśli ten element typedef jest oznaczony jako stała.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` Jeśli ten element typedef ma operatora przypisania.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE` Jeśli ten element typedef ma operatora rzutowania.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE` Jeśli ten element typedef ma typów zagnieżdżonych.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Długość tej typedef w bajtach.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol compiland otaczającej.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa typedef.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` Jeśli ten element typedef jest zagnieżdżony w zakresie leksykalne.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` Jeśli ten element typedef ma Przeciążony operator.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE` Jeśli ten element typedef jest pakowane.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|`BOOL`|`TRUE` Jeśli ten element typedef jest odwołanie.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` Jeśli ten element typedef jest w zakresie leksykalne nieglobalnych.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagTypedef` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol typu bazowego.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator typu symbolu.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Jeden z [udtkind — wyliczenie](../../debugger/debug-interface-access/udtkind.md) wartości.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Jeśli ten element typedef nie jest wyrównany.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Symbol, który opisuje kształtu tabeli wirtualnej.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|Identyfikator tabeli wirtualnej symbol kształtu.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Jeśli ten element typedef jest oznaczony jako nietrwałe.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ typem typedef może reprezentować klasę, wskaźnika lub typ zdefiniowany przez użytkownika (UDT), symbol jako element typedef współużytkuje te same właściwości jako jeden z tych typów symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)