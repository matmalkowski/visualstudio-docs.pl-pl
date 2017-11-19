---
redirect_url: /visualstudio/ide/optimize-visual-studio-startup-time/
ms.openlocfilehash: 6ba351d5b395caaddd12021b09f8792cd19b2905
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
Tytuł: "Optymalizacja ładowania rozwiązania w programie Visual Studio | Ms.custom Microsoft Docs":" "ms.date: ms.reviewer 08/31/2017:" "ms.suite:" "ms.tgt_pltfrm:" "ms.topic:"artykuł"helpviewer_keywords: 
  - "czas uruchamiania [Visual Studio]"
  - "czas uruchamiania [Visual Studio] Optymalizowanie"
  - "przyspieszenia czas rozpoczęcia [Visual Studio]" ms.assetid: 84989983-84bc-4f81-97a8-2131e3a25138 caps.latest.revision: Autor 4: ms.author "gewarren": "gewarren" Menedżer: ghogen f1_keywords: 
  - ms.technology "vs.performancecenter": 
  - "vs-ide — ogólne"
---
# <a name="optimize-solution-loading-in-visual-studio"></a>Optymalizacja rozwiązania ładowania w programie Visual Studio
W przypadku wielu rozwiązań zawiera wiele projektów, który ma wpływ na czas ładowania tych rozwiązań. Jednak w środowiskach zespołu, deweloperzy zazwyczaj działają w różnych podzbiór tych projektów i nie musisz załadować wszystkich poszczególnych projektów.

Visual Studio 2017 obsługuje **ładowania rozwiązania lekkie**. Po włączeniu trybu obciążenia (LSL) lekkie rozwiązanie Visual Studio 2017 ładuje mały podzbiór projektów zamiast ładuje wszystkie projekty w dużych rozwiązaniach. Większość typowych funkcji IDE pracy w trybie LSL i zapewnia możliwość do tworzenia, wyszukiwanie i debugowania dla całego rozwiązania. (Głównego nieobsługiwanej funkcji w trybie LSL jest Edytuj i Kontynuuj).  

> [!NOTE]
> Ta zawartość dotyczy programu Visual Studio 2017 Update 3

Dla dużych rozwiązaniach z ponad 30 projektów LSL zazwyczaj ładuje rozwiązań dwukrotnie jako szybkiego (średnio). Podczas gdy większość funkcji IDE pracy w trybie LSL, niektóre funkcje IDE mogą wymagać wszystkie projekty do załadowania. W takich przypadkach program Visual Studio automatycznie ładuje całego rozwiązania tak, aby można było używać funkcji. W najgorszym na końcu wszystkie projekty w trybie lekkie ładowania. 

Jeśli używasz funkcji IDE w projekcie, który nie jest aktualnie załadowany, Visual Studio obliczeniowymi odpowiednie projekty. Na przykład jeśli próbujesz utworzyć lub otworzyć diagramu klas nieotwarte projektu programu Visual Studio automatycznie ładuje odpowiednie projekty. Lista funkcji szczegółowe jest przywoływany w sekcjach poniżej.

Poniższe sekcje pokazują, jak włączyć obciążenia lekkie rozwiązanie, a także zdecydować, czy należy włączyć funkcję Pomoc.

## <a name="enable-or-disable-lightweight-solution-load"></a>Włącz lub wyłącz lekkie rozwiązanie obciążenia

Kliknij prawym przyciskiem myszy nazwę rozwiązania w Eksploratorze rozwiązań i wybierz **włączyć ładowania rozwiązania Lightweight**. Po zaznaczeniu opcji, musisz zamknąć i ponownie otwórz rozwiązanie, aby aktywować obciążenia lekkie rozwiązanie.

> [!NOTE]
> Podobne kroki dotyczą wyłączenie LSL. Aby wyłączyć obciążenia lekkie rozwiązanie, wybierz pozycję **wyłączyć lekkie załadować rozwiązanie**, a następnie zamknij i ponownie otwórz rozwiązanie. 

![Eksplorator rozwiązań](../ide/media/VSIDE_LSL_Solution_Setting.png)

## <a name="global_solution_load_settings"></a>Konfigurowanie ustawień globalnych lekkie rozwiązanie obciążenia

Można globalnie wyłączone lub skonfigurować LSL dla wszystkich rozwiązań, wybierając **Narzędzia > Opcje > Projekty i rozwiązania**.

![Okno dialogowe opcji narzędzi](../ide/media/VSIDE_LightweightSolutionLoad.png)

## <a name="how-does-lightweight-solution-load-work-behind-the-scenes"></a>Jak działa lekkie rozwiązanie obciążenia w tle

Podczas ładowania rozwiązania Visual Studio pamięta projekty, do których uprzednio otwarty i ładuje tylko tych projektów. Wszystkie inne projekty są widoczne w Eksploratorze rozwiązań, ale nie załadowano. Jak najszybciej rozwiń projekt, lub kliknij prawym przyciskiem myszy projekt, Visual Studio automatycznie do pobrania tego projektu. Automatyczne ładowanie projektów zazwyczaj zajmuje mniej niż 1 sekunda, ale może trwać dłużej dla niektórych projektów. Jednak Visual Studio umożliwia korzystanie z funkcji IDE jak wyszukiwanie, debugowania, kompilacji i kontroli źródła, które mogą współdziałać całego rozwiązania. Na przykład można wyszukiwać w całym rozwiązaniu nawet, jeśli tylko kilka projekty zostały załadowane w trybie lightweight. 

Podczas rozszerzania więcej projektów programu Visual Studio pamięta listy projektów rozwinięte. Po otwarciu rozwiązania Visual Studio automatycznie do pobrania projektów, które wcześniej powiększone.

## <a name="visual-studio-prompts-developers-likely-to-see-significant-performance-gains"></a>Visual Studio monituje deweloperzy mogą zobaczyć znaczący wzrost wydajności

Z danych telemetrycznych programu Visual Studio dużych rozwiązaniach z ponad 30 projektów znacząco skorzystać z trybu LSL. W rezultacie firma Microsoft Monituj deweloperom dużych rozwiązaniach wypróbowanie LSL tryb. Większość deweloperów, którzy spróbuj LSL dla pierwszego end czasu przy jego użyciu regularnie. 

## <a name="visual-studio-makes-recommendations-to-turn-on-lightweight-solution-load-based-on-heuristics"></a>Zalecenia, aby włączyć funkcję obciążenia lekkie rozwiązanie oparte na algorytmy heurystyczne sprawia, że program Visual Studio

Domyślnie program Visual Studio włącza LSL dla użytkowników, którzy najprawdopodobniej będzie korzystać. Jeśli masz wiele rozwiązań programu Visual Studio oferuje LSL tryb rozwiązań, które są najbardziej prawdopodobne zobaczyć znaczący wzrost wydajności. Jeśli zostanie wybrana opcja Tryb lekkie **zdecydować Let Visual Studio** (opcja domyślna), programu Visual Studio może Otwórz rozwiązanie w trybie lekkie oparte na algorytmy heurystyczne. Pasek komunikatów wskazuje, czy rozwiązanie jest w trybie lightweight. Pokazuje pasek komunikatów, można dowiedzieć się więcej, lub zaktualizuj ustawienia.

![Okna podręcznego](../ide/media/VSIDE_LSL_Popup.png)

## <a name="ide-features-fully-supported-in-lightweight-mode"></a>Funkcje środowiska IDE w pełni obsługiwane w trybie lekkie

|Funkcja|Obsługiwane w trybie lekkie?|
|-|-|-|
|IntelliSense|Tak|
|Wyszukaj|Tak|
|Debugowanie|Tak|
|Kompilacja|Tak|
|Kod nawigacji (Przejdź do definicji i Znajdź wszystkie odwołania)|Tak|
|Obiektyw kodu|Tak|
|Statycznej analizy kodu|Tak|
|Wdrażanie i publikowanie|Tak|
|Dodawanie i usuwanie odwołań|Tak|
|Wielowersyjność kodu|Tak|
|IntelliTrace|Tak|
|Testy jednostkowe na żywo|Tak|
|IntelliTest|Tak|
|Struktury Microsoft Fakes|Tak|
|Edytuj i kontynuuj|Nieobsługiwane|
|Testowanie jednostkowe|Wymaga ładowania projekty testowe, a następnie kompilacji rozwiązania|

## <a name="scenarios-in-which-lightweight-solution-loads-the-appropriate-projects-to-complete-the-operation"></a>Scenariusze, w których lekkie rozwiązanie ładuje odpowiednie projekty do ukończenia tej operacji

Jeśli nie pracujesz nad projektem w rozwiązaniu, projektu nie została załadowana w trybie lightweight. Niektóre funkcje dodatkowe projekty są ładowane automatycznie do obsługi scenariusza funkcji. (Mają zminimalizować tę listę scenariuszy. ) W tych sytuacjach Visual Studio ładuje projekty sam albo monit o załadowanie projekty, zgodnie z potrzebami.

|Kategoria|Problem|
|-|-|-|
|Testu jednostkowego|Projektów, które nie są obecnie ładowane nie widać na liście Projekty testowe dla kreatorów "Tworzenie IntelliTest" i "Tworzenie testu jednostkowego". </br>Należy załadować projektów, dla których chcesz utworzyć testów (można rozwinąć węzeł projektu, aby załadować projekt).|
|Diagramy klas|Jeśli utworzyć lub otworzyć diagramu klas do projektu, Visual Studio automatycznie ładuje projekty, które są zależności bezpośrednich tego projektu. </br>Całe rozwiązanie nie jest załadowane, możemy wyłączyć weryfikacji przestarzałe artefaktów odwołuje się diagram walidacji zależności.|

## <a name="scenarios-in-which-lightweight-solution-loads-the-entire-solution"></a>Scenariusze, w których lekkie rozwiązanie ładuje całego rozwiązania 

Niektóre funkcje programu Visual Studio ładuje automatycznie całego rozwiązania na potrzeby scenariusza. Dzięki temu, zawsze uzyskać pełną funkcjonalność. Na przykład niektóre operacje TFS może wymagać całego rozwiązania do załadowania. Aby uzyskać pełną funkcjonalność, Visual Studio ładuje całego rozwiązania.

|Kategoria|Scenariusz|
|-|-|-|
|Polecenie TFS SCC w węźle rozwiązania|Jeśli polecenie SCC jest wyzwalane w węźle rozwiązania (w Eksploratorze rozwiązań), programu Visual Studio automatycznie ładuje całe rozwiązanie przed wykonaniem polecenia.|
|Ładowania projektu|Jeśli rozwiązanie zawiera .NET Core i udostępnionych projektów, Visual Studio zawsze automatycznie ładuje te projekty podczas ładowania początkowego rozwiązania, samej siebie. Te projekty aktualnie nie obsługują trybu lightweight.|
|Menedżer konfiguracji rozwiązania|Użycie rozwiązania configuration manager lub usługi partia zadań kompilacji programu Visual Studio automatycznie ładuje całego rozwiązania w celu zapewnienia pełnej obsługi.|
|Menedżer pakietów NuGet|Po otwarciu interfejsu użytkownika Menedżera pakietów NuGet lub konsoli Menedżera pakietów NuGet programu Visual Studio automatycznie ładuje całego rozwiązania w celu zapewnienia pełnej obsługi.|

## <a name="known-issues"></a>Znane problemy

Istnieje kilka scenariuszy, które może nie działać w trybie LSL i wymagają ładowania projektów dodatkowe lub całego rozwiązania. Aktywnie pracujemy nad adresowania tych przypadkach. 

|Kategoria|Problem|Obejście|
|-|-|-|-|
|IntelliSense|IntelliSense mogą nie zostać zaktualizowane po zmianie konfiguracji (np. zmiana wersji kompilacji do debugowania i na odwrót). Wpływ zależy od kodu różnice z powodu zmiany konfiguracji.|Załaduj ponownie rozwiązanie po zmianie konfiguracji.|
|Refaktoryzacja ograniczenia dla C# / VB. projektów|Poprawki kodu, które zmieniają pliki projektu może zakończyć się niepowodzeniem dyskretnie po raz pierwszy.|Załadować tych projektów, jeśli zachodzi konieczność wprowadzania poprawki kodu w plikach tych projektów. Tryb Lightweight nie powoduje poprawki do projektów, które nie zostały załadowane.|
|Odnajdywanie testów jednostkowych|Testy odnalezionych w odroczonego projekty nie zostaną uruchomione, gdy projekt zostanie załadowany ręcznie.|Skompiluj ponownie projekt, aby ponowne odnajdywanie testów i ponownie uruchomić wybrane testy.|
|Testowania (LUT) na żywo jednostek|W trybie LSL może zostać wyświetlony LUT nie został aktywowany. Nie został aktywowany, ponieważ LUT wymaga jednego z projektów testów na załadowanie.|Załaduj wszystkie projektu testowego, aby aktywować na żywo testu jednostkowego dla rozwiązania.|
|Wyszukiwanie Eksploratora rozwiązań|1.    Wyszukiwanie Eksploratora rozwiązań w trybie LSL nie wyszukiwanie w plikach i nie są wyniki postępu (oznacza to, że tylko pliki są wyświetlane w obszarze drzewa, ale nie klas, metod wyszukiwania itd.).</br>2.    Wszystkie pliki należące do projektu są wyświetlane jako płaska lista zamiast widoku drzewa. Gdy pliki są przypisane do folderu projektu, zostanie przedstawiony względną ścieżkę pliku, a nie tylko nazwę pliku w widoku wyszukiwania.</br>W widoku wyszukiwania nie ma menu kontekstowych powiązanych z elementami plików.|Ładowanie całego rozwiązania w trybie LSL nie można pobrać tradycyjnych wyszukiwania w Eksploratorze rozwiązań.</br>Umożliwia także wyszukiwania w programie Visual Studio IDE.|
|Przeglądarka obiektów dla projektów C++|Przeglądarka obiektów zawiera odwołania do zestawu/WinMD tylko załadowanych projektów.|Ładowanie projektów, dla których chcesz wyświetlić informacje w przeglądarce obiektów.|

> [!Note]
> Dzięki użyciu naszych partnerów popularnych rozszerzenia Resharper w tym również działają prawidłowo w przypadku obciążenia lekkie rozwiązanie.

Możemy radością o innowacji w celu optymalizacji wydajności w czasie ładowania rozwiązania dla deweloperów. Ponieważ jest to nowa funkcja, firma Microsoft aktywnie spojrzenie na opinie klientów i adresowania znanych problemów. Mamy nadzieję na wysłuchaniu opinii. Wiadomości e-mail zespołu optymalizacji obciążenia rozwiązań programu Visual Studio wlslsupport@microsoft.com

## <a name="see-also"></a>Zobacz także
[Wydajność programu Visual Studio — porady i wskazówki](../ide/visual-studio-performance-tips-and-tricks.md)  