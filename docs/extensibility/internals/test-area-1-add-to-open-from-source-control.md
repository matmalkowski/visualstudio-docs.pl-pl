---
title: "Obszar test 1: Dodaj do Otwórz z kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 959387176e079d76263a2a5c499b5a0723fd7ad7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Obszar test 1: Dodaj do / Otwórz z kontroli źródła
Ta-wtyczka do kontroli źródła testu obszar obejmuje umieszczenie rozwiązań lub projektów pod kontrolą źródła i pobierania ich z kontroli źródła.  
  
## <a name="command-menu-access"></a>Dostęp do poleceń Menu  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programowanie zintegrowanego środowiska menu ścieżki są używane w przypadku testowego:  
  
-   Dla [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Otwórz z kontroli źródła: **pliku**, **Otwórz**, **projektu**/**rozwiązania**; poszukać w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizacji.  
  
-   Inne źródła formantu wtyczek, Otwórz z kontroli źródła: **pliku**, **kontroli źródła**, **Otwórz z kontroli źródła**.  
  
-   Dodaj do kontroli źródła: **pliku**, **kontroli źródła**, **Dodaj rozwiązanie do pliku kontroli źródła**, **kontroli źródła**, **Dodaj Wybrane projekty do kontroli źródła**.  
  
-   Menu skrótów (projektu/rozwiązania) **Dodaj rozwiązanie do kontroli źródła**.  
  
-   Dodaj z kontroli źródła: **pliku**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**.  
  
-   Dla [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], Dodaj ze źródła formantu jest również dostępna z **pliku**, **Dodaj**, **istniejący projekt**; poszukać w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] lokalizacji.  
  
    > [!NOTE]
    >  Ścieżka pliku lokalnego lub lokalne usługi IIS (serwer sieci web) służy w tym teście.  
  
## <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
-   Dla każdego typu obsługiwanych projektu użytkownik powinien móc "Dodawanie do" i "Otwórz w" kontroli źródła.  
  
-   Gdy projekt zostanie dodany do kontroli źródła, odpowiadający jej \< *ProjectName*> utworzono pliki (plik projektu wskazówka). Zawiera wyłączenia pliku listy oraz informacje o połączeniu. Nie usuwaj tego pliku, ponieważ zawiera on informacje specyficzne dla projektu.  
  
-   Po dodaniu rozwiązania do kontroli źródła, odpowiadający jej \< *Nazwa rozwiązania*> jest tworzony plik .vssscc (triple S). Plik tekstowy zawierający informacje o połączeniu i pliku listy wykluczeń, podobnie jak plik projektu wskazówki. Ten plik jest tymczasowe i istnieje tylko w bazie danych kontroli źródła.  
  
-   Po otwarciu rozwiązania z kontroli źródła, \< *Nazwa rozwiązania*> plik .vsscc (dwa razy S), który istnieje tylko w bazie danych kontroli źródła, jest tworzony lokalnie w pliku tymczasowym. Ten plik zawiera ścieżkę z folderu rozwiązania połączenia do pliku rozwiązania. Ten plik jest tymczasowe i lokalna kopia zostanie usunięta po zakończeniu operacji "Otwórz z kontroli źródła".  
  
-   Po projekt zostanie dodany do kontroli źródła, można wykonać żadnych działań kontroli źródła na nim (wyewidencjonowania, Get i tak dalej).  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych do dodawania / Otwórz z kontroli źródła testu obszaru.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Przypadek 1a: Dodaj rozwiązanie do kontroli źródła  
 Przypadek testowy koncentruje się na dodawanie rozwiązania do kontroli źródła.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dodaj rozwiązanie zawierające projekt klienta do kontroli źródła|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj rozwiązanie do kontroli źródła**).|Rozwiązanie lub projekt został dodany do kontroli źródła.|  
|Dodaj rozwiązanie zawierające System plików lub lokalnym projekt sieci Web usług IIS do kontroli źródła|1.  Utworzyć systemu plików lub lokalnym projektu sieci Web usług IIS (Użyj przycisku Przeglądaj, aby wskazać lokalizację projektu; ścieżka Określa, jaki typ projektu sieci Web jest tworzony).<br />2.  Dodaj rozwiązanie do kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj rozwiązanie do kontroli źródła**).|Rozwiązanie lub projekt został dodany do kontroli źródła.|  
|Dodaj rozwiązanie zawierające projekt zdalnej witryny sieci Web do kontroli źródła|1.  Utwórz projekt zdalnej witryny sieci Web.<br />2.  Dodaj rozwiązanie do kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj rozwiązanie do kontroli źródła**).<br />3.  Kliknij przycisk **OK** okno dialogowe ostrzeżenia dostępu FrontPage.|Rozwiązanie zostało dodane do kontroli źródła.<br /><br /> Projekt witryny zdalnej nie jest pod kontrolą źródła. (Projekty lokacji zdalnej, muszą być kontrolowane z własnego serwera usług IIS).|  
|Dodaj rozwiązanie pojedynczego projektu za pomocą kontroli źródła **Dodaj wybrane projekty do kontroli źródła**.|1.  Tworzenie rozwiązania pojedynczego projektu.<br />2.  Dodaj tylko rozwiązanie do kontroli źródła jako zaznaczenia (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**). Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Dodaj projekt do kontroli źródła jako wybór (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**).<br />4.  Kliknij przycisk **tak** można dodać projektu do tej samej lokalizacji.<br />5.  Kliknij przycisk **Wyewidencjonuj** w **Sprawdź limit edytować** okno dialogowe.|`Result from Step 2:`<br /><br /> Projekt i wszystkie pliki w projekcie mają wyewidencjonowany się wskaźnik kontroli źródła i jest wyświetlana etykieta "nie pod kontrolą źródła".<br /><br /> `Result from Step 5:`<br /><br /> Plik projektu i rozwiązania są w tym samym folderze, w kontroli źródła.|  
|Anuluj dodawanie rozwiązania do kontroli źródła|1.  Tworzenie rozwiązania pojedynczego projektu.<br />2.  Spróbuj dodać projekt i rozwiązanie do kontroli źródła. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Anuluj po systemu kontroli źródła.|`Result from Step 2:`<br /><br /> Tylko raz zostanie wyświetlone okno dialogowe zestawu projektu lokalizacji źródła formantu.<br /><br /> `Result from Step 3:`<br /><br /> Projekt Dodawanie anulowane, projektu i rozwiązania nie jest pod kontrolą źródła i wszystkie dodawanie do menu kontroli źródła jest nadal dostępne.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>Wielkość 1b. Otwórz rozwiązanie z kontroli źródła  
 Przypadek testowy koncentruje się na otwieranie rozwiązań z kontroli źródła.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Otwórz rozwiązanie zawierające projekt klienta z kontroli źródła|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|Otwarte rozwiązanie lub projekt z kontroli źródła.|  
|Otwórz rozwiązanie zawierające lokalnego lub projektu sieci Web usług IIS z kontroli źródła|1.  Utwórz lokalny lub projektu sieci Web usług IIS.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|Otwarte rozwiązanie lub projekt z kontroli źródła.|  
|Otwórz rozwiązanie zawierające projekt zdalnej witryny sieci Web z kontroli źródła|1.  Utwórz projekt zdalnej witryny sieci Web.<br />2.  Dodaj rozwiązanie do kontroli źródła. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Zamknij rozwiązanie.<br />4.  Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|`Result from Step 2:`<br /><br /> Zdalnej witryny sieci Web nie jest pod kontrolą źródła.<br /><br /> `Result from Step 4:`<br /><br /> Otworzyć rozwiązanie z kontroli źródła.<br /><br /> Projekt witryny zdalnej został załadowany, ale nie jest pod kontrolą źródła.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Przypadek 1c: Dodaj rozwiązanie z kontroli źródła  
 Przypadek testowy koncentruje się na dodawanie rozwiązania z kontroli źródła.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dodaj do puste rozwiązanie — rozwiązania pojedynczego projektu|1.  Tworzenie rozwiązania pojedynczego projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz drugi puste rozwiązanie.<br />5.  Dodaj wcześniej kontrolowane rozwiązanie z kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**).|Dodany projekt jest wyświetlany w **Eksploratora rozwiązań** i jest zaewidencjonowany.|  
|Dodaj do rozwiązania z pojedynczego projektu — pojedynczego projektu|1.  Tworzenie rozwiązania z pojedynczego projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz drugi puste rozwiązanie.<br />5.  Dodaj wcześniej kontrolowane rozwiązanie z kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**).|Dodany projekt jest wyświetlany w **Eksploratora rozwiązań** i jest zaewidencjonowany.|  
|Dodaj do rozwiązania — rozwiązanie dodane do kontroli źródła według wyboru|1.  Tworzenie rozwiązania z projektem.<br />2.  Dodaj tylko rozwiązanie do kontroli źródła jako zaznaczenia. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz nowe rozwiązanie.<br />5.  Dodaj wcześniej kontrolowane rozwiązanie z kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj projekt z kontroli źródła**).|`Result from Step 2:`<br /><br /> Projekt nie jest pod kontrolą źródła.<br /><br /> `Result from Step 5:`<br /><br /> Pierwsze rozwiązanie, gdyby elementy rozwiązania, nie można ich dodać z kontroli źródła, więc nie są wyświetlane.<br /><br /> Projekt z pierwsze rozwiązanie zostanie wyświetlony jako niedostępny.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik po testowym dla plug-in kontroli źródła](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)