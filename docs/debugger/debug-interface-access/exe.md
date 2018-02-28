---
title: Exe | Dokumentacja firmy Microsoft
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
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5e2675d821a29b53926b2145366ae98f3d8adceb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exe"></a>Exe
Exe jest jedynym symbolu bez leksykalne lub klasy nadrzędnej, ponieważ reprezentuje on globalnego zakresu pliku .exe lub .dll. Istnieje tylko jeden symbol o `SymTagExe` tagu dla każdego pliku. [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) metoda zwraca symbol.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Wiek plik wykonywalny.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID`z tego pliku wykonywalnego.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE`Jeśli pliku symboli skojarzony z tego pliku wykonywalnego zawiera typy C (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE`Jeśli symboli prywatnych ma zostały usunięte z pliku symboli skojarzone z tego pliku wykonywalnego (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Wartość wskazująca Procesora docelowego (jeden z [cv_cpu_type_e — wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md) wartości).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa pliku .exe.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Podpis pliku wykonywalnego.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Pełna ścieżka do pliku PDB lub .dbg pliku .exe.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagExe` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)