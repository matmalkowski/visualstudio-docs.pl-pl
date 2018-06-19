---
title: Zarządzanie skojarzeń plików Side-by-Side | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9144125786e7aa5f2a70823a033d49ac3fa2990
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146809"
---
# <a name="managing-side-by-side-file-associations"></a>Zarządzanie skojarzeń plików Side-by-Side
Jeśli VSPackage udostępnia skojarzeń plików, należy zdecydować, jak obsługiwać urządzenia side-by-side, w których przypadku konkretnej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powinna być wywoływana w celu otwarcia pliku. Formaty plików niezgodne komplikuje problem.  
  
 Użytkownicy oczekują nowej wersji produktu, aby był zgodny z wcześniejszych wersji, aby istniejące pliki mogą być ładowane w nowej wersji bez utraty danych. W idealnym przypadku VSPackage można zarówno obciążenia i zapisać formatów plików starszych wersji. Jeśli nie jest spełniony, powinno oferować się uaktualnienie do nowej wersji VSPackage format pliku. Wadą tego podejścia interfejsu jest, że uaktualniony plik nie można otworzyć w starszej wersji.  
  
 Aby uniknąć tego problemu, można zmienić rozszerzeń formaty plików stają się niezgodne. Na przykład wersja 1 VSPackage można użyć rozszerzenia .mypkg10 i wersji 2 można użyć rozszerzenia, .mypkg20. Ta różnica identyfikuje pakiet VSPackage, którego kliknięcie spowoduje otwarcie określonego pliku. Jeśli dodasz nowszej VSPackages do listy programów, które są skojarzone z rozszerzeniem stare, użytkownicy mogą kliknij prawym przyciskiem myszy plik i wybierz go otworzyć w nowszej pakiet VSPackage. W tym momencie VSPackage zaoferować uaktualnić go do nowego formatu lub Otwórz plik i zachować zgodność z wcześniejszymi wersjami pakiet VSPackage.  
  
> [!NOTE]
>  Można połączyć tych metod. Można na przykład zapewniają zgodność z poprzednimi wersjami dzięki ładowanie starszych pliku i oferować Uaktualnij format pliku, gdy użytkownik zapisuje go.  
  
## <a name="facing-the-problem"></a>Ten składnik Problem  
 Jeśli ma wiele VSPackages side-by-side, aby użyć tego samego rozszerzenia, należy wybrać wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] skojarzonego z rozszerzeniem. Poniżej przedstawiono dwa alternatyw:  
  
-   Otwórz plik w najnowszej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowany na komputerze użytkownika.  
  
     W takie podejście jest odpowiedzialna za określenie najnowszą wersję Instalatorem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i obejmujący we wpisie rejestru napisane dla skojarzenia pliku. Pakiet Instalatora Windows można dołączyć akcje niestandardowe, aby ustawić właściwość, która wskazuje najnowszą wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  W tym kontekście "najnowszej" oznacza "najnowszą obsługiwaną wersję." Te wpisy Instalator automatycznie nie wykrywa późniejszych wersji produktu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Wpisy w [wykrywanie wymagania systemowe](../extensibility/internals/detecting-system-requirements.md) i w [polecenia czy musi być Uruchom po instalacji](../extensibility/internals/commands-that-must-be-run-after-installation.md) są podobne do tych przedstawionych w tym miejscu i są wymagane do obsługi dodatkowe wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Następujące wiersze w tabeli Akcja niestandardowa ustaw właściwość DEVENV_EXE_LATEST właściwością ustawione przez AppSearch powoduje niepoprawne obcięcie i tabele RegLocator omówione w [polecenia czy musi być Uruchom po instalacji](../extensibility/internals/commands-that-must-be-run-after-installation.md). Wiersze w tabeli InstallExecuteSequence zaplanować akcje niestandardowe na początku sekwencji execute. Wartości w kolumnie warunku upewnij pracy logiki:  
  
    -   Visual Studio .NET 2002 jest najnowsza wersja, jeśli jest tylko bieżącej wersji.  
  
    -   Program Visual Studio .NET 2003 jest najnowsza wersja tylko, jeśli jest obecny i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest obecny.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest najnowsza wersja, jeśli jest tylko bieżącej wersji.  
  
     Wynikiem jest, że DEVENV_EXE_LATEST zawiera ścieżkę najnowszej wersji devenv.exe.  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Akcja niestandardowa wiersze tabeli, które określają najnowszej wersji programu Visual Studio  
  
    |Akcja|Typ|Źródło|docelowy|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>InstallExecuteSequence wiersze tabeli, które określają najnowszej wersji programu Visual Studio  
  
    |Akcja|Warunek|Sekwencja|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 I NIE (DEVENV_EXE_2003 LUB DEVENV_EXE_2005)|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 I NIE DEVENV_EXE_2005|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     Właściwość DEVENV_EXE_LATEST w tabeli w rejestrze pakietu Instalatora Windows służy do zapisywania wpisów z HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand klucza wartość domyślna to "%1" [DEVENV_EXE_LATEST]  
  
-   Uruchamianie programu uruchamiającego udostępnionego, który może zgłaszać najlepszy wybór z dostępnych wersji pakiet VSPackage.  
  
     Deweloperzy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wybrać takie podejście do obsługi złożonych wymagania wiele formatów rozwiązań i projektów, które wynikają z wielu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Takie podejście należy zarejestrować program uruchamiający jako program obsługi rozszerzenia. Uruchom okno sprawdza plik i decyduje o tym, która wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i VSPackage może obsłużyć tego określonego pliku. Na przykład, jeśli użytkownik otwiera plik, który został ostatnio zapisany przy użyciu określonej wersji VSPackage, Uruchom okno można uruchomić ten pakiet VSPackage w tej samej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ponadto użytkownik może skonfigurować uruchamianie można zawsze uruchomić najnowszej wersji. Uruchamianie można również monitowania użytkownika o uaktualnienie format pliku. Jeśli format pliku zawiera numeru wersji, Uruchom okno może informuje użytkownika, jeśli jest w formacie pliku z wersji, która jest nowsza niż zainstalowana VSPackages.  
  
     Uruchom okno powinna mieć składnika Instalator systemu Windows, który jest współużytkowany ze wszystkimi wersjami VSPackage. Ten proces pozwala upewnić się, czy najnowsza wersja jest zawsze instalowany i nie został usunięty, dopóki nie zostaną odinstalowane wszystkie wersje VSPackage. W ten sposób skojarzeń plików i inne wpisy rejestru składnika uruchamiania zostaną zachowane, nawet jeśli jednej wersji pakiet VSPackage zostanie odinstalowana.  
  
## <a name="uninstall-and-file-associations"></a>Odinstaluj i skojarzeń plików  
 Odinstalowanie pakiet VSPackage, który zapisuje wpisy rejestru dotyczące skojarzeń plików powoduje usunięcie skojarzeń plików. W związku z tym rozszerzeniem ma żadnych programów skojarzone. Instalator Windows nie "odzyskać" wpisy rejestru, które zostały dodane podczas VSPackage został zainstalowany. Poniżej przedstawiono kilka sposobów, aby naprawić skojarzeń plików użytkownika:  
  
-   Użyj składnika udostępnionego uruchamiania, jak opisano wcześniej.  
  
-   Poinstruuj użytkowników, aby naprawieniu wersji pakiet VSPackage, który użytkownik chce właścicielem skojarzenia pliku.  
  
-   Podaj oddzielne program wykonywalny, który ponownie zapisuje wpisy rejestru właściwe.  
  
-   Podaj konfigurację Opcje strony lub okna dialogowego okno, które użytkownicy mogą wybrać skojarzeń plików i odzyskać utracone skojarzenia. Poinstruować użytkowników, aby uruchomić go po dezinstalacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)