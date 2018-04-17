---
title: Argumenty wiersza polecenia do menedżera zawartości pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/01/2017
ms.technology:
- vs-help-viewer
ms.topic: conceptual
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25600941543698b4592e38a9952024754a5d2bbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argumenty wiersza polecenia do menedżera zawartości pomocy
Można określić sposób wdrażania i zarządzania nimi zawartość lokalnej pomocy przy użyciu argumentów wiersza polecenia do menedżera zawartości pomocy (*HlpCtntMgr.exe*). Należy uruchomić skrypty dla tego narzędzia wiersza polecenia z uprawnieniami administratora, a nie można uruchamiać te skrypty jako usługa. Za pomocą tego narzędzia, można wykonywać następujące zadania:  
  
-   Dodaj lub zaktualizuj zawartość lokalnej pomocy z dysku lub w chmurze.  
  
-   Usuń zawartość lokalnej pomocy.  
  
-   Przenieś lokalny magazyn zawartości pomocy.  
  
-   Dodawanie, aktualizowanie, usunąć lub przenieść zawartość lokalnej pomocy w trybie dyskretnym.  
  
Składnia:  
  
```  
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint  
```  
  
Na przykład:  
  
```  
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha  
```  
  
## <a name="switches-and-arguments"></a>Przełączniki i argumenty  
W poniższej tabeli opisano, przełączniki i argumentów, które służą do narzędzia wiersza polecenia do menedżera zawartości pomocy:  
  
|Przełącznik|Wymagany?|Argumenty|  
|------------|---------------|---------------|  
|/Operation|Tak|-   **Zainstaluj**— dodaje do lokalnego magazynu zawartości książek z określone źródło instalacji.<br />     Ten przełącznik wymaga argumentu /booklist, argument/sourceuri lub obu. Jeśli nie zostanie określony argument/sourceuri, domyślny Visual Studio identyfikator URI jest używany jako źródło instalacji. Jeśli nie zostanie określony /booklist argument, zostaną zainstalowane wszystkie książki na / sourceuri.<br />-   **Odinstaluj**— usuwa książek, które określają z lokalnego magazynu zawartości.<br />     Ten przełącznik wymaga /booklist argument lub argument/sourceuri.  Jeśli określisz argument/sourceuri wszystkie źródłowe zostały usunięte, a /booklist argument jest ignorowany.<br />-   **Przenieś**— przenosi magazynu lokalnego do określonej ścieżki. Domyślna ścieżka magazynu lokalnego jest ustawiony jako katalog w *ProgramData %*<br />     Ten przełącznik wymaga argumentów/locationpath i/catalogname. Komunikaty o błędach będą rejestrowane w dzienniku zdarzeń, jeśli określona ścieżka jest nieprawidłowa lub dysk nie zawiera wystarczającej ilości wolnego miejsca do przechowywania zawartości.<br />-   **Odśwież**— aktualizacje tematów, które uległy zmianie od czasu zostały zainstalowane lub ostatnio zaktualizowany.<br />     Ten przełącznik wymaga, aby argument/sourceuri.|  
|/ catalogname|Tak|Określa nazwę katalogu zawartości.|  
|/ Locale|Nie|Określa ustawienia regionalne produktu, który służy do wyświetlania i zarządzania nimi zawartości dla bieżącego wystąpienia podglądu pomocy. Na przykład określić `EN-US` dla Polski.<br /><br /> Jeśli nie określisz ustawień regionalnych ustawieniach regionalnych systemu operacyjnego jest używany. Jeśli nie można określić ustawień regionalnych, `EN-US` jest używany.<br /><br /> Jeśli określisz ustawień regionalnych, których nie jest prawidłowa, komunikat o błędzie jest rejestrowane w dzienniku zdarzeń.|  
|/e|Nie|Funkcje menedżera zawartości pomocy do uprawnień administracyjnych, jeśli bieżący użytkownik nie ma poświadczeń administracyjnych.|  
|/ sourceuri|Nie|Określa adres URL, z którego zawartość jest zainstalowany (interfejs API usługi) lub ścieżkę do pliku instalacyjnego zawartości (*.msha*). Adres URL może wskazywać do grupy produktów (węzeł najwyższego poziomu) lub książek produktu (liść węzła) w punkt końcowy stylu programu Visual Studio 2010. Nie trzeba zawierać ukośnika (/) na końcu adresu URL. Jeśli dołączysz ukośnika, będzie odpowiednio obsługiwany.<br /><br /> Komunikat o błędzie jest rejestrowany w przypadku dziennika Jeśli określony plik nie zostanie odnaleziony, jest nieprawidłowa lub jest niedostępny lub, jeśli połączenie z Internetem jest niedostępne lub zostało przerwane, gdy zawartość jest zarządzana.|  
|użycia|Nie|Określa dostawcę zawartości produktu, który zostanie usunięty (na przykład `Microsoft`). Argument domyślny dla tego przełącznika firma Microsoft.|  
|/ ProductName|Nie|Określa nazwę produktu książek, które zostaną usunięte. Nazwa produktu został określony w *helpcontentsetup.msha* lub *books.html* pliki, które zostały wydane z zawartością. Jednocześnie można usunąć książek z tylko jednego produktu. Aby usunąć książek z wielu produktów, należy wykonać kilka instalacji.|  
|/booklist|Nie|Określa nazwy książek, które mają być zarządzane, rozdzielając je spacjami. Wartości muszą być zgodne nazwy książek znajdujących się na nośniku instalacyjnym.<br /><br /> Jeśli ten argument nie jest określony, zostaną zainstalowane wszystkie książki zalecane dla określonego produktu w / sourceuri.<br /><br /> Jeśli nazwa książki zawiera co najmniej jedną spację, należy ująć ją w podwójne cudzysłowy proste ("), aby odpowiednio rozdzielana listy.<br /><br /> Komunikaty o błędach zostanie zarejestrowane, jeśli określisz/sourceuri, który jest nieprawidłowy lub nie jest dostępny.|  
|/skuId|Nie|Określa magazynowa jednostka SKU produktu ze źródła instalacji, a filtry książek, które identyfikują przełącznika/sourceuri.|  
|/Membership|Nie|-   **Minimalna**— instaluje minimalny zestaw oparte na określonej za pomocą przełącznika /skuId jednostki SKU zawartości pomocy. Mapowanie między jednostki SKU i zestawu zawartości jest widoczna w interfejsie API usługi.<br />-   **Zalecane**— instaluje zestaw książek zalecane dla określonej za pomocą argumentu /skuId jednostki SKU. Źródło instalacji jest interfejs API usługi lub *. MSHA*.<br />-   **Pełna**— instaluje cały zestaw książek dla określonej za pomocą argumentu /skuId jednostki SKU. Źródło instalacji jest interfejs API usługi lub *. MSHA*.|  
|/ locationpath|Nie|Określa domyślny folder lokalnej zawartości pomocy. Ta opcja zostanie użyta tylko do zainstalowania lub przenieść zawartość. Jeśli określisz ten przełącznik, należy także określić silent przełącznika.|  
|/silent|Nie|Instaluje lub usuwa bez monitowania użytkownika lub wyświetlanie elementów interfejsu użytkownika, w tym ikonę w obszarze powiadomień stanu zawartości pomocy. Dane wyjściowe jest rejestrowany w pliku *% Temp %* katalogu. **Ważne:** do przeprowadzenia instalacji dyskretnej zawartości, należy użyć podpisanych cyfrowo *cab* pliki nie *.mshc* plików.|  
|/launchingApp|Nie|Definiuje aplikację i kontekstu katalogu po uruchomieniu Podglądu pomocy bez aplikacji nadrzędnej. Argumenty dla tego przełącznika *NazwaFirmy*, *ProductName*, i *Numerwersji* (na przykład `/launchingApp Microsoft,VisualStudio,15.0`).<br /><br /> Jest to wymagane dla zainstalowania zawartości z silent parametru.|  
|/ wait *sekund*|Nie|Wstrzymuje zainstalować, odinstalować, a następnie Odśwież operacji. Jeśli operacja jest już w toku dla katalogu, proces oczekuje na daną liczbę sekund, aby kontynuować. Użycie wartości 0 będzie czekać w nieskończoność.|  
|/?|Nie|Wyświetla listę przełączników i ich opisy narzędzie wiersza polecenia do menedżera zawartości pomocy.|  
  
### <a name="exit-codes"></a>Kody zakończenia  
Po uruchomieniu narzędzia wiersza polecenia do menedżera zawartości pomocy w trybie dyskretnym, zwraca następujący kod zakończenia:  
  
```
Success = 0,  
  
FailureToElevate = 100  
InvalidCmdArgs = 101,  
FailOnFetchingOnlineContent = 110,  
FailOnFetchingContentFromDisk = 120,  
FailOnFetchingInstalledBooks = 130,  
NoBooksToUninstall = 200,  
NoBooksToInstall = 300,  
FailOnUninstall = 400,  
FailOnInstall = 500,  
FailOnMove = 600,  
FailOnUpdate = 700,  
FailOnRefresh = 800,  
Cancelled = 900,  
Others = 999,  
ContentManagementDisabled = 1200,  
OnlineHelpPreferenceDisabled = 1201  
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```  
  
## <a name="see-also"></a>Zobacz także  
[Przewodnik administratora podglądu pomocy](../ide/help-viewer-administrator-guide.md)  
[Zastąpienia menedżera zawartości pomocy](../ide/help-content-manager-overrides.md)  
[Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)