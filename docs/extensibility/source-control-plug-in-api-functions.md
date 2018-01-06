---
title: "Funkcje interfejsu API wtyczkę kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beaab13c76b3d50f97662e66c1f72dc83161e96d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-api-functions"></a>Funkcje API wtyczkę kontroli źródła
Interfejs API dodatku typu Plug-in kontroli źródła udostępnia następujące funkcje, które musi być implementowana przez wtyczki zgodnie z tego interfejsu API kontroli źródła. Podpisy każdej funkcji oraz semantykę skojarzone z flagi bitów i inne parametry zostały szczegółowo opisane w tym dokumencie.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inicjowanie i celów funkcji  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zamyka projektu.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Monituje użytkownika o zaawansowane opcje dla danego polecenia.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Zwraca wersję kontroli źródła wtyczek.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicjuje wtyczkę kontroli źródła. Jest to jeden raz dla każdego wystąpienia wtyczki.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Zostanie otwarty projekt.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Funkcja generyczna służy do określania szeroką gamę opcji. Każda opcja rozpoczyna się od `SCC_OPT_xxx` i ma własną zdefiniowanego zestawu wartości.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wywołuje się po po wtyczka do kontroli źródła musi zostać odłączone.|  
  
## <a name="core-source-control-functions"></a>Podstawowe funkcje kontroli źródła  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Dodaje tablicę pliki określone przez w pełni kwalifikowana nazwy do systemu kontroli źródła.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umożliwia użytkownikowi przeglądanie w poszukiwaniu plików, które znajdują się już w systemie kontroli źródła, a następnie wprowadź te pliki częścią bieżącego projektu.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Sprawdza, czy w tablicy plików.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Umożliwia wyewidencjonowanie tablicy plików.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Przedstawia różnice między plikami użytkownika lokalnego określone w pełni kwalifikowana nazwa i wersja pod kontrolą źródła.|  
|[SccGet](../extensibility/sccget-function.md)|Pobiera kopię grupy plików tylko do odczytu.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Sprawdza stan plików, które wywołującego poprosił o (za pośrednictwem `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Powoduje, że wtyczka do kontroli źródła do monitowania użytkownika o ścieżkę projektu, która jest poprawne dla określonej wtyczki.|  
|[SccHistory](../extensibility/scchistory-function.md)|Pokazuje historię tablicę nazw FQDN pliku lokalnego.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Sprawdza, czy lista plików dla ich bieżącego stanu. Ponadto używa `pfnPopulate` funkcji, aby powiadomić wywołującego, jeśli plik nie pasuje do kryteriów dla `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Zawiera właściwości pliku FQDN.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Sprawdza, czy lista pełną plików dla ich bieżącego stanu.|  
|[SccRemove](../extensibility/sccremove-function.md)|Usuwa tablica pełną plików z systemu kontroli źródła.|  
|[SccRename](../extensibility/sccrename-function.md)|Zmienia nazwę danego pliku na nową nazwę w systemie kontroli źródła.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Uzyskuje dostęp do pełnego zakresu funkcji systemu kontroli źródła.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Cofa wyewidencjonowanie tablicy plików.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkcje, które obsługuje dodatkowe możliwości (w wersji 1.2 API wtyczkę kontroli źródła)  
 Ta grupa funkcji określa dodatkowe funkcje uwzględnione w wersji 1.2 API dodatku typu Plug-in kontroli źródła. Zapewniają dostęp do bardziej zaawansowane funkcje kontroli źródła i możliwości.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Rozpoczyna operację partii.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Tworzy podprojektu o podanej nazwie w ramach istniejącego projektu nadrzędnego.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Przedstawia różnice między katalogu użytkownika lokalnego określone w pełni kwalifikowana nazwa i lokalizacja bazy danych kontroli źródła.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Sprawdza, czy lista katalogów w pełni kwalifikowaną ich bieżącego stanu.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Kończy operację wsadową.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Zwraca element nadrzędny ścieżki dany projekt (projekt musi istnieć).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Sprawdza, czy można używać wielu wyewidencjonowania pliku.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Sprawdza, czy dodatek utworzy MSSCCPRJ. Pliki SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkcje, które obsługują zaawansowane możliwości (w wersji 1.3 interfejsu API wtyczkę kontroli źródła)  
 Ta grupa funkcji określa dodatkowe funkcje uwzględnione w wersji 1.3 API dodatku typu Plug-in kontroli źródła. Zapewniają dostęp do bardziej zaawansowane funkcje kontroli źródła i możliwości.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Dodaje listę plików z kontroli źródła do bieżącego projektu.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Pobiera listę plików z kontroli źródła bez interfejsu użytkownika.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Pobiera listę plików w kontroli źródła, które różnią się od plików lokalnych.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Pobiera flagi określające, rozszerzone możliwości obsługiwane przez wtyczkę kontroli źródła.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Pobiera opcje specyficzne dla użytkownika.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Sprawdza, czy lista katalogów i plików w projekcie, lub projektów, które są pod kontrolą źródła. Znaleziono nazwy katalogów i plików jest przekazany do funkcji wywołania zwrotnego.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Sprawdza, czy nazwa zmian do listy plików. Nazwy plików są przekazywane do funkcji wywołania zwrotnego z jej zmiana stanu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: scc.h  
  
 (Podany w zestawie SDK środowiska common folderu, domyślnie zawiera *[dysk]*\Program Files\VSIP 8.0\EnvSDK\common\inc; dostarczyć także w folderze VSIP próbki MSSCCI *[dysk]*\Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Zobacz też  
 [Plug-in kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)