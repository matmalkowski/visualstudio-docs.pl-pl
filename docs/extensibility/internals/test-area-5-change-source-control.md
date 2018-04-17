---
title: 'Obszar testu 5: Zmiana kontroli źródła | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7fd014bf520ee2f0515e284f2fb5430961cd407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-5-change-source-control"></a>Testu obszar 5: Zmień kontrolę źródła
Ten obszar testu wtyczkę kontroli źródła obejmuje zmiana kontroli źródła, za pomocą **Zmień kontrolę źródła** polecenia.  
  
 **Zmiana kontroli źródła** polecenia zawiera cztery podstawowe funkcje dla użytkownika:  
  
-   **Powiąż:**  
  
     Umożliwia użytkownikowi ustanawiania lub ponownie ustanowić połączenia kontroli źródła między rozwiązania/projektu i magazynu wersji.  
  
-   **Usuń powiązanie:**  
  
     Usuwa projekt/rozwiązanie z kontroli źródła na poszczególnych połączeń.  
  
-   **Łączenie lub rozłączanie:**  
  
 Włącza lub wyłącza połączone lub w trybie offline stan kontrolowane rozwiązania, które jest opisane w obszarze 3. Aby uzyskać więcej informacji, zobacz [testu obszaru 3: Zapoznaj się z / cofnąć wyewidencjonowania](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Dostęp do poleceń Menu  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programowanie zintegrowane środowisko menu Ścieżka jest używana w przypadku testowego.  
  
 Zmień kontrolę źródła:**pliku**, **kontroli źródła**, **zmiana kontroli źródła**.  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych dla **Zmień kontrolę źródła** polecenia obszaru testu.  
  
### <a name="case-5a-bind"></a>Przypadek 5a: Bind  
 BIND zezwala użytkownikowi na dodawanie informacji o kontroli kodu źródłowego do wybranych projektów i rozwiązań. Użytkownik jest monitowany zwykle do identyfikowania projektu w kontroli źródła, do której są do dodania. Użytkownik nie może utworzyć nowego projektu w kontroli źródła w ramach tej operacji (kontrast Dodaj do kontroli źródła).  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Powiąż puste miejsce|1.  Tworzenie projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />4.  Kliknij przycisk **usunięcia powiązania**.<br />5.  Jeśli wygląda na to, należy zaakceptować okno dialogowe ostrzeżenia.<br />6.  Wybierz wszystkie elementy.<br />7.  Kliknij przycisk **powiązać**.<br />8.  Przejdź do lokalizacji pusta w magazynie kontroli źródła.<br />9. Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />10. Kliknij przycisk **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />11. Kliknij przycisk **OK** w oknie dialogowym ostrzeżenia, jeśli zostanie wyświetlona.<br />12. Zaewidencjonuj wszystko. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />13. Otwórz rozwiązanie z kontroli źródła do nowej lokalizacji.|`Result from Step 12:`<br /><br /> Rozwiązania i projektu są powiązane z i zapisywane do nowego docelowego w magazynie wersji.<br /><br /> Rozwiązanie i pliki projektu jest zaewidencjonowany.<br /><br /> Wersja magazynu projektu hierarchii odpowiada hierarchię folderów projektu na dysku.<br /><br /> `Result from Step 13:`<br /><br /> Wszystkie elementy projektu zostaną pobrane.|  
|Powiązanie do lokalizacji, która jest zsynchronizowany z klienta|1.  Tworzenie projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Utwórz kopię rozwiązania i projektu w magazynie wersji (Udostępnianie i gałęzi, jeśli przy użyciu [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />5.  Usunąć wszystkie powiązania.<br />6.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />7.  Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />8.  Zaznacz wszystkie.<br />9. Kliknij przycisk **powiązać**.<br />10. Przejdź do lokalizacji rozgałęzione rozwiązania i projektu (z kroku 3)<br />11. Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />12. Pobierz najnowsze rekursywnie dla wszystkich elementów.|Zawartość pliku po get jest taka sama, jak przed get.|  
|Powiązanie do lokalizacji, która nie jest zsynchronizowany z klientem|1.  Tworzenie projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Utwórz kopię rozwiązania i projektu w magazynie wersji (Udostępnianie i gałęzi, jeśli przy użyciu [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Modyfikowanie plików w projekcie rozgałęzione w magazynie wersji.<br />5.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />6.  Usunąć wszystkie powiązania.<br />7.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />8.  Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />9. Zaznacz wszystkie.<br />10. Kliknij przycisk **powiązać**.<br />11. Przejdź do lokalizacji dla projektów i rozwiązań, rozgałęzionych.<br />12. Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />13. Jeśli wygląda na to, należy zaakceptować okno dialogowe ostrzeżenia.<br />14. Pobierz najnowsze cykliczne dla wszystkich elementów.|Pliki, które zostały zmodyfikowane w kroku 4 są również zmodyfikować lokalnie.|  
|Powiąż rozwiązania, które były nigdy nie pod kontrolą źródła|1.  Utwórz pusty folder w kontroli źródła.<br />2.  Utwórz projekt klienta.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe (**pliku**, **kontroli źródła**, **Zmień kontrolę źródła**).<br />4.  Powiązać rozwiązania lokalizacji pusta w kontroli źródła.<br />5.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />6.  Kliknij przycisk **Kontynuuj z tymi powiązaniami** w oknie dialogowym potwierdzenia.<br />7.  Kliknij przycisk **OK** w oknie dialogowym ostrzeżenia, jeśli zostanie wyświetlona.|Rozwiązanie jest dodane do kontroli źródła.<br /><br /> Rozwiązania i projektu są wyewidencjonowane.|  
|Anuluj Bind|1.  Tworzenie projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz okno dialogowe zmiana kontroli źródła.<br />4.  Usunąć wszystkie powiązania.<br />5.  Kliknij przycisk **OK** przycisk, aby zamknąć okno dialogowe. Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />6.  Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />7.  Powiązać niepowiązanych lokalizacji.<br />8.  Kliknij przycisk **anulować**.|`Result from Step 5:`<br /><br /> Rozwiązanie nie jest już pod kontrolą źródła<br /><br /> `Result from Step 8:`<br /><br /> Rozwiązanie jest nadal nie w kontroli źródła.|  
  
### <a name="case-5b-unbind"></a>Przypadek 5b: Usuń powiązanie  
 Usuń powiązanie informacje o kontroli kodu źródłowego powoduje usunięcie z projektów i ich rozwiązania. Dotyczy projekty i rozwiązania są oparte na różnych wybór użytkownika i jak zostały dodane do kontroli źródła.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Usuń powiązanie rozwiązanie zawierające jeden System plików lub lokalnego projektu sieci Web usług IIS i jeden klient projektu|1.  Utworzyć systemu plików lub lokalnym projektu sieci Web usług IIS.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt klienta do rozwiązania.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować Sprawdź z rozwiązania.<br />5.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />6.  Kliknij przycisk **usunięcia powiązania**.<br />7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />8.  Próba wyewidencjonowania rozwiązania, projektu, elementy rozwiązania, elementy projektu.|Rozwiązanie i projekty nie są pod kontrolą źródła.<br /><br /> Polecenia menu kontroli źródła nie są wyświetlane.|  
|Usuń powiązanie Anuluj|1.  Tworzenie projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />4.  Kliknij przycisk **usunąć wszystkie powiązania**.<br />5.  Kliknij przycisk **anulować**.|Rozwiązanie jest pod kontrolą źródła.|  
  
### <a name="case-5c-rebind"></a>Przypadek 5c: ponownie powiązać  
 Ponownie Utwórz wiązanie jest po prostu kombinację unbind i powiązania — proces ponownego projekt/rozwiązanie, które wcześniej były pod kontrolą źródła i został niepowiązanych.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Ponownie powiązać rozwiązanie i projekty bez zamykania **Zmień kontrolę źródła** — okno dialogowe|1.  Tworzenie projektu.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />4.  Kliknij przycisk **usunięcia powiązania**.<br />5.  Wybierz wszystkie wiersze.<br />6.  Kliknij przycisk **powiązać**.<br />7.  Kliknij przycisk **OK** zamknąć **Zmień kontrolę źródła** okno dialogowe.<br />8.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowania.|Rozwiązania i projektu są pod kontrolą źródła.|  
|Ponownie powiązać projekt tylko bez zamknięcia **Zmień kontrolę źródła** — okno dialogowe|1.  Tworzenie projektu.<br />2.  Dodaj tylko projektu do korzystania z kontroli źródła (Plik -> źródło sterowania -> Dodaj wybrane projekty do kontroli źródła.<br />3.  Otwórz okno dialogowe zmiana kontroli źródła.<br />4.  Usuń powiązanie tylko dla projektu.<br />5.  Powiąż tylko dla projektu.|Niekontrolowany pozostaje rozwiązania.<br /><br /> Projekt pozostaje kontrolowany.|  
|Ponownie powiązać rozwiązanie tylko bez zamykania **Zmień kontrolę źródła** — okno dialogowe|1.  Tworzenie projektu.<br />2.  Dodaj tylko rozwiązanie przy użyciu kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**.<br />3.  Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />4.  Usuń powiązanie tylko rozwiązanie (nie zamykaj **Zmień kontrolę źródła** okno dialogowe.)<br />5.  Powiąż tylko rozwiązania.<br />6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />7.  Wyewidencjonuj rozwiązanie i elementy rozwiązania (jeśli istnieje)|Rozwiązanie pozostaje kontrolowany.<br /><br /> Niekontrolowany pozostaje projektu.|  
|Ponownie powiązać rozwiązanie lub projekt docelowy tylko w tym samym katalogu|1.  Tworzenie projektu.<br />2.  Dodaj tylko projektu do korzystania z kontroli źródła (**pliku**, **kontroli źródła**, **Dodaj wybrane projekty do kontroli źródła**.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz nowe rozwiązanie z co najmniej dwa projekty.<br />5.  Dodaj rozwiązanie do kontroli źródła.<br />6.  Dodaj projekt utworzony w kroku 1 z kontroli źródła.<br />7.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonować rozwiązania.<br />8.  Sprawdź w całym rozwiązaniu.<br />9. Otwórz **Zmień kontrolę źródła** okno dialogowe.<br />10. Wybierz dodany projekt (z kroku 6), a następnie kliknij przycisk **Unbind**.<br />11. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.<br />12. Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie.<br />13. Otwórz ponownie **Zmień kontrolę źródła** okno dialogowe.<br />14. Wybierz dodany projekt (z kroku 6), a następnie kliknij przycisk **powiązać**.<br />15. Wybierz oryginalnej lokalizacji.|Rozwiązanie i projekty pozostaną kontrolowany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)