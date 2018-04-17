---
title: Testowanie przewodnik plug-in kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37af6a289b59b6066a71836e4d44e380b584ec70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="test-guide-for-source-control-plug-ins"></a>Przewodnik po testowym dla plug-in kontroli źródła
Ta sekcja zawiera wskazówki dotyczące testowania z wtyczka do kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Podano szeroką gamę omówienie najczęściej obszarów testowych, jak również niektórych bardziej skomplikowanych obszarów, które mogą powodować problemy. W tym omówieniu nie stanowi wyczerpującej listy przypadków testowych.  
  
> [!NOTE]
>  Niektóre poprawek usterek i usprawnień w najnowszej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE może ujawnić problemy z istniejącego źródła formantu dodatków plug-in napotkanych wcześniej nie podczas korzystania z poprzednich wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Zdecydowanie zaleca się przetestowanie istniejących wtyczka do kontroli źródła dla obszarów wymienionych w tej sekcji, nawet jeśli żadne zmiany nie zostały wprowadzone do wtyczki od poprzedniej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Przygotowanie wspólnej  
 Maszyna o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i wtyczkę kontroli źródła docelowy zainstalowany, jest wymagana. Podobnie skonfigurowane drugiej maszyny może służyć do niektórych otwierania z kontroli źródła testów.  
  
## <a name="definition-of-terms"></a>Definicje terminów  
 Na potrzeby tego przewodnika testu należy użyć następujących definicje terminów:  
  
 Projekt klienta  
 Typ dostępne w żadnego projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługującej integracji kontroli źródła (na przykład [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], lub [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Projekt sieci Web  
 Istnieją cztery typy projektów sieci Web: System plików, lokalne usługi IIS, lokacje zdalne i FTP.  
  
-   Projekty systemu plików są tworzone na ścieżkę lokalną, ale nie wymagają Internet Information Services (IIS) do zainstalowania są wewnętrznie dostępne za pośrednictwem ścieżki UNC i można umieścić pod kontrolą źródła z poziomu środowiska IDE, podobnie jak projektów klienckich.  
  
-   Lokalnego projektów usług IIS pracy z programem IIS zainstalowane na tym samym komputerze, które są dostępne przy użyciu adresu URL wskazujący na komputerze lokalnym.  
  
-   Projekty lokacji zdalnej również powstają w ramach usług IIS, ale zostały one umieszczone pod kontrolą źródła na komputerze z serwerem usług IIS, a nie z wewnątrz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
-   Projekty FTP są dostępne za pośrednictwem zdalnego serwera FTP, ale nie może być umieszczone pod kontrolą źródła.  
  
 Funkcja rejestracji  
 Inna nazwa rozwiązania lub projektu pod kontrolą źródła.  
  
 Magazyn wersji  
 Bazy danych kontroli źródła, która jest uzyskiwany za pośrednictwem interfejsu API dodatku typu Plug-in kontroli źródła.  
  
## <a name="test-areas-covered-in-this-section"></a>Testowanie obszarów opisanych w tej sekcji  
  
-   [Obszar test 1: Dodaj do / Otwórz z kontroli źródła](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Przypadek 1a: Dodaj rozwiązanie do kontroli źródła  
  
    -   Przypadek 1b: Otwórz rozwiązanie z kontroli źródła  
  
    -   Przypadek 1c: Dodaj rozwiązanie z kontroli źródła  
  
-   [Obszar testowy 2: pobieranie z kontroli kodu źródłowego](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Obszar testu 3: Zapoznaj się z / cofnąć wyewidencjonowania](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Przypadek 3: Pobierz / cofnąć wyewidencjonowania  
  
    -   Przypadek 3a: Zapoznaj się z  
  
    -   Przypadek 3b: rozłączone wyewidencjonowanie  
  
    -   Przypadek 3c: Edycja/zapytania Zapisz (QEQS)  
  
    -   Przypadek 3d: Wyewidencjonowanie dyskretnej  
  
    -   Przypadek 3e: odwrócenia wyewidencjonowania  
  
-   [Obszar testowy 4: ewidencjonowanie](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Przypadek 4a: zmodyfikowane elementy  
  
    -   Przypadek 4b: Dodawanie plików  
  
    -   Przypadek 4c: dodawanie projektów  
  
-   [Obszar testowy 5: zmienianie kontroli kodu źródłowego](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Przypadek 5a: Bind  
  
    -   Przypadek 5b: Usuń powiązanie  
  
    -   Przypadek 5c: ponownie powiązać  
  
-   [Obszar testowy 6: usuwanie](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Obszar testowy 7: udostępnianie](../../extensibility/internals/test-area-7-share.md)  
  
-   [Obszar testowy 8: przełączanie wtyczki](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Przypadek 8a: automatyczna zmiana  
  
    -   Przypadek 8b: rozwiązania na podstawie zmiany  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)