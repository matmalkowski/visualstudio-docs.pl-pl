---
title: Compilanddetails — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b1288a3bde1a8d17f40971744298adb1e1ecffb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468811"
---
# <a name="compilanddetails"></a>CompilandDetails
Compiland informacje są dzielone symbole z `SymTagCompiland` tag (szczegóły niski) i `SymTagCompilandDetails` tag (wysoki poziom szczegółów). `SymTagCompilandDetails` wymaga dodatkowych symbole ładowania. Jednak zapewnia szereg informacji o compiland, który nie jest dostępny z `SymTagCompiland` symbolu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numer kompilacji wewnętrznych kompilatora.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Wewnętrzny główny numer wersji kompilatora.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Zaplecza podrzędny numer wersji kompilatora.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nazwa kompilatora wytworzonego tego compiland (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Jeśli Edytuj i Kontynuuj zostały włączone w kompilacji.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numer kompilacji frontonu kompilatora.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Frontonu główny numer wersji kompilatora.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Frontonu podrzędny numer wersji kompilatora.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Jeśli ta compiland ma informacje o debugowaniu (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Jeśli ta compiland zawiera kodu zarządzanego (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Jeśli compiland został skompilowany z [/GS (Sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Jeśli compiland została przekonwertowana z kodu wspólnego języka pośredniego (CIL) do kodu natywnego.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Jeśli zostały wyrównywana typy danych zdefiniowane przez użytkownika (UDT) niektóre określone granic pamięci (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Jeśli compiland został skompilowany z [/hotpatch (Utwórz obraz możliwych)](/cpp/build/reference/hotpatch-create-hotpatchable-image) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Jeśli compiland został skompilowany z [opcję/LTCG (Generowanie kodu w czasie Link)](/cpp/build/reference/ltcg-link-time-code-generation) przełącznika kompilatora (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Wartość TRUE, jeśli compiland jest moduł Microsoft języka pośredniego (MSIL) (tylko w DIA SDK w wersji 8.0 lub nowszej).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Język kodu źródłowego.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol compiland.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator nadrzędnego leksykalne symbolu.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Platformy, na którym został skompilowany compiland (jeden z [cv_cpu_type_e — wyliczenie](../../debugger/debug-interface-access/cv-cpu-type-e.md) wartości).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symboli.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagCompilandDetails` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
  
## <a name="remarks"></a>Uwagi  
 Kompilatory często mają w postaci znany jako kompilatora przebiegu dwa; w niektórych wersjach kompilatora każdego przebiegu jest obsługiwany przez inny program. Te są nazywane kompilatory frontonu i zaplecza, odpowiednio, dlatego właściwości symbolu numerów wersji wewnętrzną i zewnętrzną.  
  
## <a name="see-also"></a>Zobacz też  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)