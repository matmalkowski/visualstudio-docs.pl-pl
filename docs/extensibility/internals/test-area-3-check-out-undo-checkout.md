---
title: 'Obszar testu 3: Wyboru wyjściowego odwrócenia wyewidencjonowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d769fdc52ac92053c258a3f82fa53cec5c56fa7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134968"
---
# <a name="test-area-3-check-outundo-checkout"></a>Obszar testu 3: Zapoznaj się z / cofnąć wyewidencjonowania
Ten obszar testu wtyczkę kontroli źródła obejmuje edycji i cofanie elementy z magazynu wersji za pomocą **Wyewidencjonuj** i **Cofnij wyewidencjonowanie** poleceń.  
  
 **Wyewidencjonuj**: znaczniki elementu w magazynie wersji jako wyewidencjonowane, należy kopii lokalnej do odczytu/zapisu modyfikuje.  
  
 **Cofnij wyewidencjonowanie**: oznacza element w magazynie wersji jako zaewidencjonowany, umożliwia przywrócenie kopii lokalnej do stanu przed wyewidencjonowanie (w zależności od opcji).  
  
## <a name="command-menu-access"></a>Dostęp do poleceń Menu  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programowanie zintegrowanego środowiska menu ścieżki są używane w przypadku testowego.  
  
##### <a name="check-out"></a>Wymelduj się:  
  
-   **Plik**, **kontroli źródła**, **wyewidencjonować**.  
  
-   **Plik**, **wyewidencjonować**.  
  
-   Menu skrótów **wyewidencjonować**.  
  
-   Cofnięcie wyewidencjonowania: **pliku**, **kontroli źródła**, **odwrócenia wyewidencjonowania**.  
  
## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie  
  
-   Po operacji wyewidencjonowanie plików docelowych i/lub folderów są oznaczone jako wyewidencjonowane w magazynie wersji.  
  
-   Magazyn wersji atrybuty wyewidencjonowanie do odpowiednich użytkowników.  
  
-   Godzina i Data wyewidencjonowania są prawidłowe (ustawienia dla każdego użytkownika).  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych dla obszaru testu wyewidencjonowania/cofnięcie wyewidencjonowania.  
  
### <a name="case-3a-check-out"></a>Przypadek 3a: Zapoznaj się z  
 W tej sekcji koncentruje się na operację polecenia wyewidencjonowywania.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Sprawdź limit wyłącznego (COE) projektu klienta|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z całego projektu wyłącznie (**pliku**, **Wyewidencjonuj**).|Wyewidencjonowanie występuje.|  
|Wyewidencjonowania na wyłączność (COE), System plików lub lokalnym projektu sieci Web usług IIS|1.  Ustaw połączenie z serwerem sieci Web do udziału w pliku **narzędzia**, **opcje**, **projekty**, **sieci Web ustawienia**.<br />2.  Utwórz projekt sieci Web.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Zapoznaj się z całego projektu wyłącznie (**pliku**, **kontroli źródła**, **Wyewidencjonuj**).|Wyewidencjonowanie występuje.|  
|Zapoznaj się z elementów rozwiązania w rozwiązaniu (Nowa metoda obsługi innych plików)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z rozwiązania.<br />4.  Dodaj kilka elementów rozwiązania.<br />5.  Sprawdź w nowo dodanych elementów.<br />6.  Wybranie wielu elementów rozwiązania.<br />7.  Zapoznaj się z wybranych elementów (Menu skrótów **Wyewidencjonuj**).|Wybrane pliki są wyewidencjonowane.|  
|Sprawdź limit lokalnej wersji (Jeśli wtyczka w ramach testu obsługuje tę funkcję)|1.  Użytkownik 1: Tworzenie projektu klienta.<br />2.  Użytkownik 1: Dodaj rozwiązanie do kontroli źródła.<br />3.  Użytkownik 2: Otwórz rozwiązanie z kontroli źródła do innej lokalizacji.<br />4.  Użytkownik 2: Zapoznaj się z plikiem.<br />5.  Użytkownik 2: Modyfikowanie plików.<br />6.  Użytkownik 2: Sprawdź w pliku.<br />7.  Użytkownik 1: Zapoznaj się z lokalną wersją pliku (Sprawdź **Sprawdź lokalnej wersji** zaawansowanych opcji w **Wyewidencjonuj** okno dialogowe).|Lokalna wersja pliku jest wyewidencjonowany.<br /><br /> Modyfikacje przez użytkownika 2 nie są stosowane do plików użytkownika 1.|  
  
### <a name="case-3b-disconnected-check-out"></a>Przypadek 3b: rozłączone wyewidencjonowanie  
 Działających w trybie odłączenia pozwala użytkownikom pewnego poziomu obsługi kontroli źródła ciągłego, gdy nie jest dołączony bezpośrednio do magazynu wersji. Jest to realizowane przez lokalne buforowanie wszystkich odpowiednich informacji o zarejestrowane rozwiązanie i projekty.  
  
 Wyewidencjonowanie na wyłączność operacje może występować tylko w przypadku, gdy połączone z magazynu kontroli źródła. Udostępniony wyewidencjonowanie operacje może wystąpić w dowolnym momencie, czy połączone lub rozłączone. W związku z tym podczas połączenia z magazynu wersji tylko **Sprawdź wychodzących udostępnionych** (COS) polecenie jest włączone. Gdy odłączony, **Cofnij wyewidencjonowanie** jest wyłączona, ponieważ nie można pobrać starą wersję zastąpić zmiany wprowadzone przez użytkownika.  
  
 Gdy użytkownik połączy się ponownie do wersji magazynu stanów wyewidencjonowania, wszystkie zarejestrowane rozwiązania i projekty są synchronizowane. Jest to niezbędne aktualizacje w magazynie wyewidencjonowania, wykonywane przez użytkownika. Po synchronizacji miało miejsce, użytkownik będzie mógł kontynuować pracę w zwykły (Połączono).  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
-   Nie można użyć **Sprawdź się wyłącznie** polecenia bez połączenia z magazynu wersji.  
  
-   Nie można użyć **Cofnij wyewidencjonowanie** polecenia bez połączenia z magazynu wersji.  
  
-   **Udostępnione Wyewidencjonuj** polecenie działa.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Gdy odłączony, wyewidencjonować plik, a następnie podłącz do synchronizowania|1.  Odłącz projekt pod kontrolą źródła za pomocą okna dialogowego Zmiana kontroli źródła (**pliku**, **kontroli źródła**, **zmiany źródła Contro**l).<br />2.  Wyewidencjonuj plik.<br />3.  Kliknij polecenie Wyewidencjonuj (odłączony) w oknie dialogowym ostrzeżenia.<br />4.  Edytuj plik.<br />5.  Połącz przy użyciu okna dialogowego Zmiana kontroli źródła.<br />6.  Pobierz najnowszą wersję edytowanego pliku.|Typowe oczekiwane zachowanie|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Przypadek 3c: Edycja/zapytania Zapisz (QEQS)  
 Elementy pod kontrolą źródła są śledzone do edycji, zmiany, i zapisuje, aby ułatwić użytkownikom łatwe zarządzanie swoich plików. Podczas edycji jest kontrolowany przez element, który "zaewidencjonowania" QEQS przechwytuje próba edycji i pyta użytkownika, czy chce wyewidencjonować plik, aby go edytować. W zależności od **narzędzia**, **opcje** ustawienia, użytkownik jest wymuszone, aby sprawdzić wyjściowy plik, aby można było edytować lub może mieć możliwość edytowania kopii w pamięci i wyewidencjonowania później. Jeśli użytkownik **narzędzia**, **opcje** ustawienie nie jest ustawiona, aby wyświetlić wyewidencjonowanie okno dialogowe i po prostu wyewidencjonuj go, a następnie użytkownik dokonuje jego edycji, plik automatycznie sprawdzi, jeśli to możliwe.  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
-   Po operacji wyewidencjonowanie plików docelowych i/lub folderów są oznaczone jako wyewidencjonowane w magazynie wersji.  
  
-   Magazyn wersji atrybuty wyewidencjonowanie do odpowiednich użytkowników.  
  
-   Godzinę i datę wyewidencjonowanie są prawidłowe (ustawienia dla każdego użytkownika).  
  
-   Lokalna kopia pliku lub folderu docelowego jest zapisywalny.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Edytuj plik tekstowy, który jest sprawdzany w|1.  Utwórz nowy projekt zawierający plik tekstowy.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **Zezwalaj na wyświetlanie plików można edytować podczas tylko do odczytu na dysku** do niezaznaczone.<br />4.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **Monituj o wyewidencjonowaniu** w **po zaznaczeniu tej opcji pliki sąedytowany** pola kombi.<br />5.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **Monituj o wyewidencjonowaniu** w **po zaznaczeniu tej opcji pliki są zapisywane** pola kombi.<br />6.  Otwórz plik tekstu w edytorze, próba wprowadź nowy tekst w pliku. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />7.  Kliknij przycisk **anulować** w **Wyewidencjonuj do edycji** okno dialogowe. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />8.  Ustaw **narzędzia**, **opcje**, **kontroli źródła**, **Zezwalaj na wyświetlanie plików można edytować podczas tylko do odczytu na dysku** do zaznaczenia.<br />9. Otwórz plik projektu w edytorze, próba wprowadź nowy tekst w pliku. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />10. Kliknij przycisk **Edytuj** w **Wyewidencjonuj do edycji** okno dialogowe. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />11. Edytuj plik tekstowy, a następnie spróbuj zapisać go.|`Result of step 6:`<br /><br /> Sprawdź, zostanie wyświetlone okno dialogowe Edycja.<br /><br /> `Result of step 7:`<br /><br /> Format pliku jest bez zmian.<br /><br /> `Result of step 9:`<br /><br /> Sprawdź, zostanie wyświetlone okno dialogowe Edycja.<br /><br /> `Result of step 10:`<br /><br /> Można edytować plik projektu w pamięci.<br /><br /> `Result of step 11:`<br /><br /> Zapisz wyewidencjonowanie na Zapisz — okno dialogowe pojawia się na.|  
|Edytuj plik rozwiązania, który jest sprawdzany w|Powtórz kroki opisane w poprzednim testu, ale zamiast modyfikowania pliku tekstowego, zmodyfikuj rozwiązania, zmieniając właściwości rozwiązania.|Sam, jak poprzedni test|  
|Edytuj plik projektu jest zaewidencjonowany|Powtórz kroki opisane w poprzednim testu, ale zamiast modyfikowania pliku tekstowego, modyfikować projektu, zmieniając właściwości projektu.|Taka sama jak poprzedni test.|  
  
### <a name="case-3d-silent-check-out"></a>Przypadek 3d: Dyskretnej wyewidencjonowania  
 Obszar podrzędne to obejmuje wyewidencjonowanie scenariusze gdzie **Wyewidencjonuj** okno dialogowe jest niewidoczny dla użytkownika **narzędzia**, **opcje**, **ustawień kontroli źródła** .  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
-   Po operacji wyewidencjonowanie plików docelowych i/lub folderów są oznaczone jako wyewidencjonowane w magazynie wersji.  
  
-   Magazyn wersji atrybuty wyewidencjonowanie do odpowiednich użytkowników.  
  
-   Godzinę i datę wyewidencjonowanie jest prawidłowa (ustawienia dla każdego użytkownika).  
  
-   Lokalna kopia pliku lub folderu docelowego jest zapisywalny.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dyskretnej wyewidencjonowania pliku|1.  Ustaw **narzędzia**, **opcje**, **kontroli źródła** do **wyewidencjonować pliki automatycznie na edycji**.<br />2.  Utwórz nowy projekt z plikiem.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Zapoznaj się z pliku.|Plik jest wyewidencjonowany dyskretnej (bez interfejsu użytkownika).|  
|Wyewidencjonowanie dyskretnej dla projektu|1.  Ustaw **narzędzia**, **opcje**, **kontroli źródła** do **wyewidencjonować pliki automatycznie na edycji**.<br />2.  Utwórz nowy projekt.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Zapoznaj się z projektu.|Plik jest wyewidencjonowany dyskretnej (bez interfejsu użytkownika).|  
  
### <a name="case-3e-undo-check-out"></a>Przypadek 3e: Cofnij wyewidencjonowanie  
 **Cofnij wyewidencjonowanie** służy do anulowania plik wyewidencjonowany stanu i uniknąć ewidencjonowanie zmiany wprowadzone w pliku.  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
-   Wartość domyślna jest oparta na użytkownika **Wyewidencjonuj lokalną wersję** ustawienie. Jeśli użytkownik wybrał Wyewidencjonuj lokalną wersję, wartością domyślną cofnięcie wyewidencjonowania jest zawsze przywrócić wersję wyewidencjonowany.  
  
-   Po zatwierdzeniu cofania, ikony w **Eksploratora rozwiązań** są aktualizowane, dla których to dotyczy plików, a element zostanie usunięty z **oczekujących zaewidencjonowań** okna.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Cofnij wyewidencjonowanie pojedynczy plik, który został wyewidencjonowany w trybie wyłączności|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z plikiem wyłącznie.<br />4.  Zmodyfikuj plik.<br />5.  Cofnij wyewidencjonowanie (**pliku**, **kontroli źródła**, **odwrócenia wyewidencjonowania**).|Typowe oczekiwane zachowanie.|  
|Cofnij wyewidencjonowanie pojedynczy plik, który został wyewidencjonowany Shared|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zapoznaj się z plikiem udostępnionych.<br />4.  Zmodyfikuj plik.<br />5.  Cofnij wyewidencjonowanie (**pliku**, **kontroli źródła**, **odwrócenia wyewidencjonowania**).|Typowe oczekiwane zachowanie.|  
|Cofnij wyewidencjonowanie projektu po dodaniu plików do projektu|1.  Utwórz nowy projekt, a następnie dodaj go do kontroli źródła.<br />2.  Zapoznaj się z projektu.<br />3.  Dodaj plik do projektu.<br />4.  Cofnij wyewidencjonowanie projektu.|Dodano plik zostanie usunięty z projektu w Eksploratorze rozwiązań.<br /><br /> Projekt został już wyewidencjonowany.|  
|Cofnij wyewidencjonowanie projektu po usunięciu plików z projektu|1.  Utwórz nowy projekt, a następnie dodaj go do kontroli źródła.<br />2.  Zapoznaj się z projektu.<br />3.  Usuń plik z projektu.<br />4.  Cofnij wyewidencjonowanie projektu.|Usunięto plik pojawia się w projekcie w Eksploratorze rozwiązań.<br /><br /> Projekt został już wyewidencjonowany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)