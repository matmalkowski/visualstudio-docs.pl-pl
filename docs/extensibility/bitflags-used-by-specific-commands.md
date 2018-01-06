---
title: "Używane przez określonego polecenia flag bitowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be102b5eaf39db2fc7495c62c456e35e54ffd0f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bitflags-used-by-specific-commands"></a>Używane przez określonego polecenia flag bitowych
Zachowanie kilka funkcji w interfejsie API dodatku typu Plug-in kontroli źródła może być modyfikowany przez ustawienie jednego lub więcej bitów w pojedynczej wartości. Te wartości są określane jako flag bitowych. Różne flag bitowych używany przez interfejs API dodatku typu Plug-in kontroli źródła są szczegółowo opisane w tym miejscu pogrupowane według funkcji, która używa ich.  
  
## <a name="checked-out-flag"></a>Wyewidencjonowano flagi  
 Ta flaga można ustawić dla dowolnego [SccAdd](../extensibility/sccadd-function.md) lub [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Zachowaj ten plik wyewidencjonowany.|  
  
## <a name="add-flags"></a>Dodaj flagi  
 Te flagi są używane przez [SccAdd](../extensibility/sccadd-function.md).  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|Wtyczka do kontroli źródła powinien automatycznie wykrywa, czy plik jest tekstowy czy binarny.|  
|`SCC_FILETYPE_TEXT`|0x01|Typ pliku jest tekst.|  
|`SCC_FILETYPE_BINARY`|0x04|Typ pliku jest plikiem binarnym. **Uwaga:** `SCC_FILETYPE_TEXT` i `SCC_FILETYPE_BINARY` flagi wzajemnie się wykluczają. Należy ustawić dokładnie jedną lub nie.|  
|`SCC_ADD_STORELATEST`|0x02|Przechowywanie tylko najnowszą wersję (nie wystąpiły).|  
  
## <a name="diff-flags"></a>Flagi różnicowego  
 [SccDiff](../extensibility/sccdiff-function.md) używa tych flag do zdefiniowania zakresu operacja diff. `SCC_DIFF_QD_xxx` Flagi wzajemnie się wykluczają. Jeśli określono jednej z nich, nie wizualne jest podawana. W "szybkie różnicowego" (QD), wtyczka nie określa, jak ten plik ma różne, tylko jeśli jest inny. Jeśli żadna z tych flag jest określony, odbywa się "różnicowego visual"; szczegółowy plik różnice są obliczane i wyświetlane. Jeśli żądanego QD nie jest obsługiwana, wtyczkę przechodzi do następnego najlepsze. Na przykład jeśli IDE żądań sumy kontrolnej, i wtyczki nie obsługuje, wtyczka ma pełny spis treści sprawdź (nadal znacznie szybciej niż wyświetlanie).  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0X0002|Ignoruj wielkość różnice.|  
|`SCC_DIFF_IGNORESPACE`|0X0004|Ignoruj różnice biały znak. **Uwaga:** `SCC_DIFF_IGNORECASE` i `SCC_DIFF_IGNORESPACE` flagi są opcjonalne flag bitowych.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD porównując zawartość całego pliku.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD przez sumy kontrolnej.|  
|`SCC_DIFF_QD_TIME`|0x0040|QD przez sygnatury czasowej pliku.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|To jest używany do sprawdzania wszystkich flag bitowych QD maski. Nie powinien zostać przekazany do funkcji; trzy flag bitowych QD wzajemnie się wykluczają. QD oznacza zawsze nie wyświetlania interfejsu użytkownika.|  
  
## <a name="populatelist-flag"></a>Flaga PopulateList  
 Ta flaga jest wykorzystywana przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) w `fOptions` parametru.  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|IDE jest przekazanie katalogów, nie pliki.|  
  
## <a name="populatedirlist-flags"></a>Flagi PopulateDirList  
 Te flagi są używane przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w `fOptions` parametru.  
  
|Wartość opcji|Wartość|Opis|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Sprawdź, czy tylko jeden poziom katalogów dla katalogów (jest to wartość domyślna).|  
|SCC_PDL_RECURSIVE|0X0001|Rekursywnie Sprawdź, czy wszystkie katalogi w ramach każdego danego katalogu.|  
|SCC_PDL_INCLUDEFILES|0X0002|Dołącz nazwy pliku w procesie badania.|  
  
## <a name="openproject-flags"></a>Flagi OpenProject  
 Te flagi są używane przez [SccOpenProject](../extensibility/sccopenproject-function.md) w `dwFlags` parametru.  
  
|Wartość opcji|Wartość|Opis|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Jeśli projekt nie istnieje w kontroli źródła, należy go utworzyć. Jeśli ta flaga nie jest ustawiona, monit użytkownika dla projektu do tworzenia (chyba że `SCC_OP_SILENTOPEN` określono flagę).|  
|SCC_OP_SILENTOPEN|0x00000002L|Nie monituj użytkownika, aby utworzyć projekt; Zwróć `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Pobierz flagi  
 Te flagi są używane przez [SccGet](../extensibility/sccget-function.md) i [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|IDE nie pliki, jest przekazanie katalogi: Pobierz wszystkie pliki w tych katalogach.|  
|`SCC_GET_RECURSIVE`|0x00000002L|IDE jest przekazanie katalogi: uzyskanie tych katalogów oraz ich podkatalogów.|  
  
## <a name="noption-values"></a>Wartości nOption  
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `nOption` parametru.  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Ustaw stan kolejki zdarzeń.|  
|`SCC_OPT_USERDATA`|0x00000002L|Określ dane użytkownika dla `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE może obsłużyć Anuluj|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ustaw wywołania zwrotnego w przypadku zmiany nazwy.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Wyłącz wyewidencjonowanie interfejsu użytkownika dodatku plug-in kontroli źródła i nie należy ustawiać katalog roboczy.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Dodaj z systemu kontroli źródła, aby określić katalog roboczy. Spróbuj udostępnianie w projekcie skojarzone jest bezpośredni obiekt podrzędny.|  
  
## <a name="dwval-bitflags"></a>dwVal flag bitowych  
 Te flagi są używane przez [SccSetOption](../extensibility/sccsetoption-function.md) w `dwVal` parametru.  
  
|Flaga|Wartość|Opis|Używane przez `nOption` wartość|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Wstrzymuje działanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Umożliwia rejestrowanie kolejki zdarzeń.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Ustawienie domyślne) Trybem nie Anuluj; wtyczkę należy podać w razie potrzeby.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|IDE obsługuje anulowania.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Ustawienie domyślne) OK, aby zapoznać się z poziomu interfejsu użytkownika wtyczek; katalog roboczy jest ustawiona.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Nie wtyczki wyewidencjonowania interfejsu użytkownika, nie katalog roboczy.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)