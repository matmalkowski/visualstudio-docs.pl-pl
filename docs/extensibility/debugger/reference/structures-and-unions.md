---
title: "Struktury i złożenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1cae50d4ff122ebea1fa11291570ac23f556f6f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="structures-and-unions"></a>Struktury i Unii
Poniżej przedstawiono struktur i Unii w Visual Studio SDK debugowania.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Określa identyfikator procesu, który może być identyfikator systemu lub identyfikatora GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Opisuje warunki, w których zostanie zastosowana punktu przerwania.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Opisuje rozwiązanie przerwania błędu, takie jak lokalizacja, program i wątku.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Określa typ struktury, używane do opisywania lokalizacji punktu przerwania.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Określa składniki, które opisują lokalizację punktu przerwania pod adresem w kodzie.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Określa lokalizację punktu przerwania powiązanej bezpośrednio z adresu w programie debugowany.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Określa lokalizację punktu przerwania w wierszu w pliku kodu źródłowego.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Określa lokalizację przesunięcia punkt przerwania w funkcji w kodzie.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Używana do ustawiania punktów przerwania kodu na podstawie ciągu, który użytkownik może wprowadzić z IDE.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Używana do ustawiania punkty przerwania danych, które są oparte na ciąg, który użytkownik może wprowadzić z IDE.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Opisuje rozwiązanie punkt przerwania w określonej lokalizacji.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Opisuje liczbę i warunki, na których zostanie wyzwolone punkt przerwania po został wcześniej przekazany.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Zawiera informacje wymagane do zaimplementowania punktu przerwania.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Zawiera informacje wymagane do zaimplementowania punktu przerwania (taki sam jak [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktura ale zawiera identyfikator GUID, ograniczenia i śledzenia informacje na temat dostawcy).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Określa lokalizację punktu przerwania w kodzie.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Przedstawia wynik powiązanie punktu przerwania danych.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Zawiera opis informacji powiązania punktu przerwania dla punktu przerwania kodu lub punktu przerwania danych.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Określa struktury rozwiązania lokalizacji punktu przerwania.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 W tym artykule opisano tablicy ciągów.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Określa informacje dotyczące typu pola pobierana z metadanych.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Opisuje wywołanie metody lub funkcji.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 W tym artykule opisano komputera, na którym działa debugera.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 W tym artykule opisano listę identyfikatorów GUID.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Opisuje kontekstu pamięci lub kontekst kodu.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Zawiera opis adresu w programie debugowany.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Reprezentuje jedną z wielu różnych rodzajów adresów.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Identyfikuje podglądu niestandardowego lub wpisz wizualizatora.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Opisuje właściwości debugowania, która z kolei opisuje obiekt natury hierarchicznej mającą nazwę, typ i wartość.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 W tym artykule opisano odwołanie.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 W tym artykule opisano dezasemblacji do środowiska IDE do wyświetlenia.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Zawiera opis wyjątku lub błędów czasu wykonywania zgłoszony przez debugowany program.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Opisuje zmiennej lokalnej, parametr lub inne pole.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 W tym artykule opisano ramki stosu.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 W tym artykule opisano tablicę unikatowych identyfikatorów dla aparatami debugowania dostępne.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Służy do określania informacji o JustMyCode dla modułu.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 W tym artykule opisano określonego komputera.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Opis elementu tablicy w tablicy.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Zawiera opis adresu pola klasy lub struktury.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Zawiera opis adresu lokalnej zmiennej w zakresie (zazwyczaj funkcji lub metody).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Zawiera opis adresu metody klasy.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Opisuje parametr metody lub funkcji.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 W tym artykule opisano wartość zwracana z metody lub funkcji.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Opisuje typ pola pobierana z metadanych.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 W tym artykule opisano danego modułu (plik DLL, EXE lub zestawu).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 W tym artykule opisano informacje dotyczące ścieżki wyszukiwania symboli, które Przeszukano stanu.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Zawiera opis adresu natywnego.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Opisuje typ pola z symboli PDB.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Zawiera opis stanu punktu przerwania, który jest gotowy do powiązania do lokalizacji kodu.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Opisuje proces.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 W tym artykule opisano listę [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekty reprezentujące węzłów programu.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Zawiera opis procesów uruchomionych na komputerze.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Określa lokalizację wierszy i kolumn w podanym tekście.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Opisuje właściwości wątku.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Opisuje typ pola.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Opisuje adres fizyczny.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Zawiera opis adresu, który jest względem `this` wskaźnika (`Me` w języku Visual Basic).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówka: msdbg.h, sh.h lub ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)