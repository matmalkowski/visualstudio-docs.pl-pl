---
title: "Porady: Instalowanie dodatku Plug-in kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab02b65e4a40f15da857038a45d9bcc2b88b1b83
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-a-source-control-plug-in"></a>Porady: Instalowanie dodatku Plug-in kontroli źródła
Tworzenie wtyczki kontroli źródła obejmuje trzy kroki:  
  
1.  Utwórz bibliotekę DLL z funkcji zdefiniowanych w sekcji odwołania API dodatku typu Plug-in kontroli źródła niniejszej dokumentacji.  
  
2.  Implementuje funkcje zdefiniowane przez interfejs API dodatku typu Plug-in kontroli źródła. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wywołania, Udostępnij interfejsów i okien dialogowych z wtyczki.  
  
3.  Zarejestruj plik DLL, wprowadzając wpisy rejestru odpowiednie.  
  
## <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje źródła formantu wtyczek zgodnych z interfejsem API dodatku typu Plug-in kontroli źródła.  
  
### <a name="registering-the-source-control-plug-in"></a>Rejestrowanie wtyczkę kontroli źródła  
 Przed uruchomionych zintegrowane środowisko programistyczne (IDE) można wywołać w systemie kontroli źródła, musi najpierw odnaleźć źródła kontrolować biblioteki DLL dodatku, który eksportuje interfejsu API.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Aby zarejestrować biblioteki DLL dodatku kontroli źródła  
  
1.  Dodaj dwa wpisy w kluczu HKEY_LOCAL_MACHINE w podkluczu oprogramowania określający Twojej podklucz nazwa firmy następuje z podklucz nazwę produktu. Wzorzec jest klucza HKEY_LOCAL_MACHINE\SOFTWARE\\*[nazwa firmy]*\\*[nazwa produktu]*\\*[entry]* = wartość. Dwa wpisy zawsze są nazywane SCCServerName i SCCServerPath. Każdy jest regularne ciągu.  
  
     Na przykład jeśli nazwą firmy jest firmy Microsoft i produktu kontroli źródła nosi nazwę SourceSafe, a następnie ta ścieżka rejestru będzie HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe. W tym podkluczu pierwszej pozycji SCCServerName, to ciąg czytelny dla użytkownika nazwy produktu. Drugi wpis SCCServerPath, jest pełna ścieżka do źródła kontrolować wtyczki DLL, która ma nawiązać IDE. Poniżej przedstawiono przykładowe wpisy rejestru:  
  
    |Przykładowy wpis rejestru|Przykładowa wartość|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath jest pełną ścieżką do SourceSafe wtyczki. Wtyczka do kontroli źródła będzie używać różnych nazwach firmy, ale tej samej ścieżki wpis rejestru.  
  
2.  Następujące wpisy rejestru opcjonalne może służyć do modyfikowania zachowania wtyczka do kontroli źródła. Te wpisy Przejdź w tym samym podkluczu jako SccServerName i SccServerPath.  
  
    -   Wpis HideInVisualStudioregistry mogą być używane, gdy nie chcesz źródła formantu typu plug w celu są wyświetlane na liście wyboru wtyczek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ten wpis ma wpływ na automatyczne przełączenie do wtyczkę kontroli źródła. Jeden możliwe użycie ten wpis jest Jeśli podasz pakietu kontroli źródła, który zastępuje wtyczka do kontroli źródła, ale ma w celu ułatwienia użytkownikowi migracji używana jest wtyczka do kontroli źródła do kontroli źródła pakietu. Po zainstalowaniu pakietu kontroli źródła, ustawia ten wpis rejestru, która ukrywa wtyczki.  
  
         HideInVisualStudio jest wartość DWORD i ma ustawioną wartość 1, aby ukryć wtyczki lub 0, aby wyświetlić wtyczki. Jeśli nie ma wpisu rejestru, domyślne zachowanie jest Pokaż wtyczki.  
  
    -   Wpis rejestru DisableSccManager można wyłączyć lub ukrywanie **uruchamianie \<serwera kontroli źródła >** opcji menu, która zwykle jest wyświetlany w obszarze **pliku**  ->   **Kontroli źródła** podmenu. Wybranie tego menu opcji wywołania [SccRunScc](../../extensibility/sccrunscc-function.md) funkcji. Wtyczka do kontroli źródła może nie obsługiwać programu zewnętrznego i w związku z tym można wyłączyć lub nawet Ukryj **uruchamianie** opcji menu.  
  
         DisableSccManager jest ustawiono wartość DWORD na 0 Aby włączyć **uruchamianie \<serwera kontroli źródła >** opcji menu, ustaw wartość 1, aby wyłączyć opcję menu i wartość 2, aby ukryć opcji menu. Jeśli nie ma tego wpisu rejestru, domyślne zachowanie jest Pokaż opcji menu.  
  
    |Przykładowy wpis rejestru|Przykładowa wartość|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Dodaj podklucz, SourceCodeControlProvider, w kluczu HKEY_LOCAL_MACHINE w podkluczu oprogramowania.  
  
     W podkluczu ten wpis rejestru ProviderRegKey ustawiono ciąg reprezentujący podklucza, który można umieścić w rejestrze w kroku 1. Wzorzec jest HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = oprogramowania\\*[nazwa firmy]*\\*[nazwa produktu]*.  
  
     Poniżej przedstawiono przykładowe zawartość dla tego podklucza.  
  
    |Wpis rejestru|Przykładowa wartość|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Wtyczka do kontroli źródła będzie używać tego samego podklucz i wpis nazwy, ale wartość będą inne.  
  
4.  Utwórz podklucz o nazwie InstalledSCCProviders w podkluczu SourceCodeControlProvider, a następnie umieść jeden wpis w tym podkluczu.  
  
     Nazwa tego wpisu jest czytelny dla użytkownika nazwę dostawcy (taka sama jak wartość określona dla wpisu SCCServerName), a wartość to jeszcze raz podklucz utworzonego w kroku 1. Wzorzec jest HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[Nazwa wyświetlana]* = oprogramowania\\*[nazwa firmy]* \\ *[nazwa produktu]*.  
  
     Na przykład:  
  
    |Przykładowy wpis rejestru|Przykładowa wartość|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Może istnieć wiele źródła formantu dodatków plug-in zarejestrowanych w ten sposób. Jest to sposób [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] znajduje wszystkie zainstalowane wtyczki na podstawie interfejsu API dodatku typu Plug-in kontroli źródła.  
  
## <a name="how-an-ide-locates-the-dll"></a>Jak IDE lokalizuje biblioteki DLL  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ma dwa sposoby znajdowania źródło kontrolować biblioteki DLL dodatku:  
  
-   Znajdź kontroli źródła domyślnej wtyczki i nawiązać z nią dyskretnej.  
  
-   Znajdź wszystkie zarejestrowane źródło wtyczki kontroli, z której użytkownik wybiera jeden.  
  
 Aby zlokalizować biblioteki DLL w pierwszym sposobie, IDE wygląda w podkluczu HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider wpisu ProviderRegKey. Wartość tego wpisu wskazuje innego podkluczu. Następnie IDE wyszukuje wpis o nazwie SccServerPath w tej drugiej podklucza w HKEY_LOCAL_MACHINE. Wartość tego wpisu punktów IDE do pliku DLL.  
  
> [!NOTE]
>  IDE nie załadować biblioteki dll z ścieżek względnych (na przykład.\NewProvider.DLL). Należy określić pełną ścieżkę do pliku DLL (na przykład c:\Providers\NewProvider.DLL). To ich bezpieczeństwo środowiska IDE, zapobiegając ładowania nieautoryzowani lub personifikowanej DLL dodatku plug-in.  
  
 Aby zlokalizować biblioteki DLL w drugim sposobem, IDE wygląda w podkluczu HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders wszystkie wpisy*.* Każdy wpis ma nazwę i wartość. IDE Wyświetla listę tych nazw użytkownikowi*.* Po wybraniu nazwy IDE wyszukuje wartość dla wybranej nazwy, który wskazuje podklucz. IDE wyszukuje wpis o nazwie SccServerPath w tym podklucza w HKEY_LOCAL_MACHINE. Wartość tego wpisu wskazuje IDE poprawne biblioteki DLL.  
  
 Wtyczka do kontroli źródła musi obsługiwać obu metod odnajdywania biblioteki DLL i ustawiany ProviderRegKey, zastępując wszelkie poprzednie ustawienie. Co ważniejsze go należy dodać się na liście InstalledSccProviders, użytkownik może mieć wybór które wtyczka do kontroli źródła do użycia.  
  
> [!NOTE]
>  Ponieważ jest używany klucz HKEY_LOCAL_MACHINE, wtyczka do kontroli źródła tylko jeden może być zarejestrowany jako domyślny wtyczkę kontroli źródła na danym komputerze (jednak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pozwala określić, które wtyczka do kontroli źródła będzie używał faktycznie dla danego rozwiązania). Podczas procesu instalacji sprawdź, jeśli jest już skonfigurowana wtyczka do kontroli źródła; Jeśli tak, poproś użytkownika czy nie można ustawić nowy kontroli źródła wtyczki instalowane domyślnie. Podczas dezinstalacji nie należy usuwać innych podkluczy rejestru, które są wspólne dla wszystkich źródła formantu wtyczek w HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; Usuń tylko z określonym podklucz SCC.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Jak IDE wykrywa obsługę wersji 1.2/1.3  
 Jak jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wykryć, czy do funkcji wersji 1.2 i 1.3 API dodatku typu Plug-in kontroli źródła wtyczek obsługuje? Aby zadeklarować zaawansowane możliwości, wtyczkę kontroli źródła musi implementować odpowiednich funkcji.  
  
 Najpierw [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sprawdza wartość zwrócona przez wywołanie metody [SccGetVersion](../../extensibility/sccgetversion-function.md). Go musi być większa lub równa 1.2.  
  
 Następnie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Określa, czy konkretnego nowa funkcja jest obsługiwana przez sprawdzenie `lpSccCaps` argumentu [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Jeśli oba te warunki są spełnione, można wywołać nowe funkcje obsługiwane w wersji 1.2 i 1.3.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)