---
title: "Określ symboli (.pdb) i plików źródłowych w debugerze | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 04/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84dbee96880d651ab17efd1b19dbb2589f87f9f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Określ symboli (.pdb) i plików źródłowych w debugerze programu Visual Studio
Plik bazy danych (.pdb) programu skrót pliku symboli, mapuje identyfikatorów, które należy utworzyć w kodzie źródłowym dla klas, metod i inny kod, aby identyfikatory, które są używane w skompilowanych plików wykonywalnych projektu. Plik .pdb mapuje również instrukcje zawarte w kodzie źródłowym na instrukcje wykonania w plikach wykonywalnych. Debuger użyje tych informacji do określenia dwóch kluczowych informacji:

* Nazwy plików i wierszy numer źródłowego mają być wyświetlane w programie Visual Studio IDE
* Lokalizacja w pliku wykonywalnego do zatrzyma się w przypadku ustawienia punktu przerwania

Plik symboli zawiera także oryginalną lokalizację plików źródłowych i opcjonalnie lokalizację serwera źródeł, z którego mogą być pobierane pliki źródłowe.
  
> [!TIP]
> Jeśli chcesz debugować kodu spoza projektu kodu źródłowego, takie jak kod systemu Windows lub kod innych firm wywołania projektu, należy określić lokalizację .pdb (i opcjonalnie plików źródłowych kod zewnętrzny), a tych plików muszą być dokładnie odpowiada kompilacji t on plików wykonywalnych.  
 
##  <a name="BKMK_Find_symbol___pdb__files"></a>Gdy debuger wyszukiwania plików symboli? 
  
1.  Lokalizacja określona w pliku DLL lub pliku wykonywalnym.  
  
     (Domyślnie, jeśli skompilowałeś bibliotekę DLL lub plik wykonywalny na swoim komputerze, konsolidator umieszcza pełną ścieżkę i nazwę skojarzonego pliku .pdb wewnątrz pliku DLL lub pliku wykonywalnego. Debuger najpierw sprawdza, czy plik symboli znajduje się w lokalizacji określonej w pliku DLL lub pliku wykonywalnym. Jest to pomocne, ponieważ zawsze masz dostępne symbole dla kodu, który skompilowałeś na swoim komputerze.)  
  
2.  pliki .pdb, które znajdują się w tym samym folderze co plik DLL lub pliku wykonywalnego.

3. Wszystkie lokalizacje [określona w opcjach debugera](#BKMK_Specify_symbol_locations_and_loading_behavior) plików symboli. 
  
    * Wszystkie lokalne foldery pamięci podręcznej symboli.  
  
    * Wszystkie sieci internet, lub symbol lokalnych serwerów i lokalizacje, które są określone, takich jak Microsoft symbol server (jeśli jest włączona). 

> [!NOTE]
> Przed programu Visual Studio 2012 podczas debugowania kodu zarządzanego na urządzeniu zdalnym trzeba umieścić pliki symboli na komputerze zdalnym. Począwszy od programu Visual Studio 2012, wszystkie pliki symboli musi znajdować się na komputerze lokalnym lub w lokalizacji [określona w opcjach debugera](#BKMK_Specify_symbol_locations_and_loading_behavior).  
  
##  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a>Dlaczego pliki symboli są wymagane dokładnie odpowiadać pliki wykonywalne?  
Debuger będzie ładował tylko plik .pdb dla pliku wykonywalnego, który dokładnie pasuje do pliku .pdb, który z kolei został utworzony podczas kompilowania pliku wykonywalnego (czyli .pdb musi być plikiem oryginalnym lub kopią oryginalnego pliku .pdb). Ponieważ kompilator jest zoptymalizowany pod kątem szybkości kompilacji, oprócz swojego głównego zadania utworzenia prawidłowego i efektywnego kodu, można zmienić układ pliku wykonywalnego, nawet jeśli nie zmienił się sam kod. Aby uzyskać więcej informacji, zobacz [Dlaczego Visual Studio wymaga symbol debugera dokładnej zgodności plików pliki binarne, które zostały skompilowane?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)
  
##  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>Konfigurowanie, gdy debuger wyszukuje pliki symboli i zachowania ładowania symboli
 Podczas debugowania projektu w programie Visual Studio IDE debuger ładuje automatycznie pliki symboli, które znajdują się w katalogu projektu. Można określić ścieżki alternatywnej wyszukiwania i symboli z serwerów Microsoft, Windows i składników innych firm w **Narzędzia > Opcje > debugowanie > symbole**. Można również określić określone moduły, które mają debugera automatyczne ładowanie symboli dla elementu. Można też następnie zmienić te ustawienia ręcznie podczas aktywnego debugowania.  
  
1.  W programie Visual Studio Otwórz **Narzędzia > Opcje > debugowanie > symbole** strony.  
  
     ![Narzędzia &#45; Opcje &#45; Debugowanie &#45; Strona symbole](../debugger/media/dbg_tools_options_symbols.gif "DBG_Tools_Options_Symbols")  
  
2.  Wybierz folder ![narzędzia &#47; Opcje &#47; Debugowanie &#47; Ikona folderu symbole](../debugger/media/dbg_tools_options_foldersicon.png "DBG_Tools_Options_FoldersIcon") ikony. Można edytować tekst jest wyświetlany w **symboli (.pdb) lokalizacje** pole.  
  
3.  Wpisz adres URL lub ścieżkę katalogu serwera symboli lub lokalizację symboli. Uzupełnianie instrukcji pomaga w znalezieniu właściwego formatu.

    Można użyć **Ctrl + Up** i **Ctrl + Down** Aby zmienić kolejność ładowania dla lokalizacji symboli. Naciśnij klawisz **F2** Aby edytować adres URL lub ścieżkę katalogu.
  
4.  Zwiększające symbol ładowania wydajności wpisz ścieżkę do katalogu lokalnego, w której symbole mogą zostać skopiowane przez serwery symboli w **pamięci podręcznej symboli w tym katalogu** polu katalog lokalny, który może zostać skopiowana symboli.  
  
    > [!NOTE]
    >  Pamięci podręcznej symboli nie należy umieszczać w folderze chronionym (na przykład C:\Windows lub jednym z jego podfolderów). Zamiast tego użyj folderu przeznaczonego do odczytu i zapisu.  
  
### <a name="specify-symbol-loading-behavior"></a>Określ zachowanie ładowania symboli 
  
Można określić pliki, które mają zostać załadowane automatycznie z **symboli (.pdb) lokalizacje** pole lokalizacji po rozpoczęciu debugowania. Pliki symboli w katalogu projektu są zawsze załadowane.  
  
1.  Wybierz **wszystkich modułów, chyba że wykluczone** załadować wszystkie symbole dla wszystkich modułów oprócz tych, które określisz po wybraniu **Określ wykluczonych modułów** łącza.  
  
2.  Wybierz **tylko określonych modułów** opcji, a następnie wybierz pozycję **Określ modułów** do listy modułów, że symboli plików, które chcesz załadować automatycznie. Pliki symboli dla innych modułów są ignorowane.  
  
### <a name="specify-additional-symbol-options"></a>Określ opcje dodatkowe symboli 
  
Następujące opcje można również ustawić na **Narzędzia > Opcje > debugowanie > Ogólne** strony:  
  
**Załaduj elementy eksportu bibliotek DLL (tylko kod natywny)**  
  
Po wybraniu ładuje tabele eksportu bibliotek DLL. Informacje symboliczne z tabel eksportu bibliotek DLL mogą być przydatne, jeśli pracujesz z komunikatami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM, kierowaniem lub dowolną biblioteką DLL, dla której nie masz symboli. Odczytywanie informacji o eksportowaniu biblioteki DLL są związane z pewnym dodatkowym obciążeniem. Dlatego ta funkcja jest domyślnie wyłączona.  
  
Aby zobaczyć, jakie symboli są dostępne w tabeli eksportu biblioteki dll, użyj `dumpbin /exports`. Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Przeczytaj `dumpbin /exports` danych wyjściowych widać nazwy funkcji dokładne, w tym znaków innych niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji tabel eksportu biblioteki DLL mogą być pojawić się obcięte gdzie indziej w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>Serwery symboli użycia można znaleźć plików symboli nie na komputerze lokalnym  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]serwery symboli, które implementują protokół symsrv mogą pobrać pliki symboli debugowania. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/Library/bd6977ca-e30a-491a-a153-671d81222ce6) i [narzędzia do debugowania dla systemu Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) są dwa narzędzia, które można wdrożyć serwery symboli. Określ serwery symbol do użycia w VS **opcje** okno dialogowe.  
  
 Serwery symboli, z których możesz korzystać, obejmują:  
  
 **Serwery symboli publicznych firmy Microsoft**  
  
 Aby debugować awarię, która występuje podczas wywoływania biblioteki DLL systemu lub innej biblioteki, często potrzebować będziesz systemowych plików .pdb, które zawierają symbole dla Windows DLL, EXE i sterowników urządzeń. Możesz uzyskać te symbole z serwerów publicznych firmy Microsoft. Serwery symboli publicznych firmy Microsoft Podaj symbole dla systemów operacyjnych Windows, oprócz MDAC, usługi IIS, ISA i [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Aby korzystać z serwerów symboli firmy Microsoft, wybierz **opcji i ustawień** na **debugowania** menu, a następnie wybierz **symbole**. Wybierz **serwerów symboli firmy Microsoft**.  
  
 **Serwery symboli w sieci wewnętrznej lub na komputerze lokalnym**  
  
 Zespół lub firma mogą tworzyć serwery symboli dla własnych produktów i w roli pamięci podręcznej dla symboli ze źródeł zewnętrznych. Możesz mieć serwer symboli na własnym komputerze. Możesz wprowadzić lokalizacji serwerów symboli jako adres URL lub ścieżkę **debugowanie**/**symbole** strony VS **okno dialogowe opcji**.  
  
 **Serwery symboli innych firm**  
  
 Inni dostawcy aplikacji systemu Windows i bibliotek mogą zapewnić dostęp do serwera symboli w Internecie. Także wprowadzić adres URL z tych serwerów symboli **debugowanie**/**symbole** strony,  
  
> [!NOTE]
>  Jeśli używasz serwera symboli innego niż publiczne serwery symboli Microsoft, upewnij się, że serwer symboli i jego ścieżka są godne zaufania. Pliki symboli mogą zawierać dowolny kod wykonywalny, dlatego możesz być narażony na zagrożenia bezpieczeństwa.  
  
###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a>Znajdź i załaduj symbole podczas debugowania  
 W dowolnym momencie, gdy debuger jest w trybie przerwania, można załadować symbole dla modułu, który wcześniej został wykluczony przez opcje debugera lub których kompilator nie mógł odnaleźć. Możesz załadować symbole z menu skrótów okien Stos wywołań, Moduły, Elementy lokalne, Automatyczne i wszystkich okien Czujka. Jeśli debuger przerwie działanie na kodzie, który nie zawiera dostępnych plików symboli lub źródłowych, pojawi się okno dokumentu. Tutaj można znaleźć informacje o brakujących plikach i podjąć działania w celu odszukania i załadowania ich.
  
 **Znajdowanie symboli ze stronami dokumentu nie załadowano symboli**  
  
 Istnieje szereg sposobów na to, aby debuger wszedł do kodu, który nie zawiera dostępnych symboli:  
  
1.  Przechodzenie do kodu.  
  
2.  Wejście do kodu z punktu przerwania lub wyjątku.  
  
3.  Przełączenie do innego wątku.  
  
4.  Zmiana ramek stosu przez dwukrotne kliknięcie ramki w oknie wywołania stosu.  
  
 Gdy wystąpi jedno z tych zdarzeń, debuger wyświetla **nie załadowano symboli** strony, aby odnaleźć i załadować symbole niezbędne.  
  
 ![Strona nie załadowano symboli](../debugger/media/dbg_nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
-   Aby zmienić ścieżki wyszukiwania, wybierz ścieżkę niezaznaczone lub **nowy** i wprowadź nową ścieżkę. Wybierz **załadować** ponowić wyszukiwanie ścieżki i załadować pliku symboli, jeśli został znaleziony.  
  
-   Wybierz **przeglądania i Znajdź***nazwę pliku wykonywalnego***...**  zastąpienia żadnych opcji symbolu i ponów próbę ścieżki wyszukiwania. Plik symboli jest ładowany, jeśli zostanie odnaleziony, lub wyświetlany jest Eksplorator plików, aby użytkownik mógł ręczne wybrać plik symboli.  
  
-   Wybierz **zmiany ustawień symboli...**  do wyświetlenia **debugowanie** > **symbole** strony okna dialogowego Opcje programu VS.  
  
-   Wybierz **wyświetlić dezasemblacji** można wyświetlić dezasemblacji w nowym oknie jeden raz.  
  
-   Aby zawsze pokazuj dezasemblację, gdy nie znajdują się pliki źródła lub symbol, wybierz **okno dialogowe Opcje** połączyć, a następnie wybierz oba **włączyć debugowanie poziomu adres** i **Pokaż dezasemblację, jeśli źródło nie jest dostępny**.  
  
     ![Opcje &#47; Debugowanie &#47; Opcje ogólne dezasemblacji](../debugger/media/dbg_options_general_disassembly_checkbox.png "DBG_Options_General_disassembly_checkbox")  
  
 **Zmień symbol opcje z menu skrótów**  
  
 Gdy jesteś w trybie przerwania możesz znaleźć i załadować symbole dla elementów, które są wyświetlane w oknach Stos wywołań, Moduły, Lokalne, Automatyczne i wszystkich oknach Czujka Zaznacz element w oknie, otwórz menu podręczne i wybierz jedną z następujących opcji:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Załaduj symbole**|Próbuje załadować symboli z lokalizacji określonej w **debugowanie**/**symbole** strony **opcje** okno dialogowe. Jeśli nie można znaleźć pliku symboli, uruchamiany jest Eksplorator plików, tak aby można było określić nową lokalizację do wyszukiwania.|  
|**Informacje dotyczące ładowania symboli**|Przedstawia informacje wskazujące lokalizację załadowanego pliku symboli lub lokalizacje, które były przeszukiwane, jeśli debuger nie może znaleźć pliku.|  
|**Ustawienia symboli...**|Otwiera **debugowanie**/**symbole** strony VS **opcje** okno dialogowe.|  
|**Zawsze ładuj automatycznie**|Dodaje plik symboli do listy plików, które są ładowane automatycznie przez debuger.|  
  
###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a>Ustawianie opcji kompilatora pliki symboli  
 Podczas kompilacji projektu z VS IDE i użyć standardowego **debugowania** konfigurację kompilacji, C++ i zarządzanych kompilatory utworzyć pliki symboli w odpowiednich dla kodu. Możesz również ustawić opcje kompilatora w wierszu polecenia, aby tworzyć pliki symboli.  
  
 **Opcje języka C++**  
  
 Plik bazy danych programu (.pdb) przechowuje informacje od debugowaniu i stanie projektu, co pozwala na łączenie przyrostowe konfiguracji debugowania programu. Plik PDB jest tworzony podczas kompilowania z [/zi lub/zi](/cpp/build/reference/z7-zi-zi-debug-information-format) (dla C/C++).  
  
 W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], [/Fd](/cpp/build/reference/fd-program-database-file-name) opcji nazwy pliku .pdb utworzony przez kompilator. Podczas tworzenia projektu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] za pomocą kreatorów, **/Fd** opcja jest ustawiona na tworzenie pliku PDB o nazwie *projektu*.pdb.  
  
 Tworzenie aplikacji C/C++ za pomocą pliku reguł programu make i określenia **/zi** lub **/zi** bez **/Fd**, na końcu dwa pliki .pdb:  
  
-   VC*x*.pdb, gdzie *x* reprezentuje wersji programu Visual C++, na przykład VC11.pdb. Ten plik przechowuje wszystkie informacje o debugowaniu dla poszczególnych plików OBJ i znajduje się w tym samym katalogu, co plik makefile projektu.  
  
-   Project.pdb tego pliku przechowywane są wszystkie informacje debugowania dla pliku the.exe. Dla języka C/C++ znajduje się w podkatalogu \debug.  
  
 Zawsze tworzy plik OBJ, kompilator C/C++ scala informacji o debugowaniu VC*x*.pdb. Informacje wstawione zawierają informacje o typie, ale nie zawierają informacji o symbolach, takich jak definicje funkcji. Tak, nawet jeśli każdy plik źródłowy zawiera wspólne pliki nagłówkowe, takich jak \<windows.h >, definicje typów z tych nagłówków są przechowywane tylko raz, a nie w każdym pliku OBJ.  
  
 Konsolidator tworzy plik project.pdb, który zawiera informacje debugowania do pliku EXE projektu. Plik project.pdb zawiera informacje debugowania pełne, w tym prototypy funkcji, nie tylko informacje o typie znaleziono w VC*x*.pdb. Oba pliki .pdb zezwalają na aktualizacje przyrostowe. Konsolidator osadza także ścieżkę do pliku .pdb w pliku .exe lub .dll, który tworzy.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debuger używa ścieżka do pliku PDB w pliku EXE lub DLL można znaleźć pliku project.pdb. Debuger nie może znaleźć pliku PDB w tej lokalizacji lub jeśli ścieżka jest nieprawidłowa (np. projekt został przeniesiony na inny komputer), debuger wyszukuje ścieżkę zawierającą plik EXE, ścieżki symboli określone w **opcje** okno dialogowe (**debugowanie** folderu, **symbole** węzła). Debuger nie załaduje pliku .pdb, który nie pasuje do debugowanego pliku wykonywalnego. Jeśli debuger nie może znaleźć pliku PDB **znajdowanie symboli** zostanie wyświetlone okno dialogowe, które umożliwia wyszukiwania symboli lub dodać dodatkowych lokalizacji do ścieżki wyszukiwania.  
  
 **Opcje środowiska .NET framework**  
  
 Plik bazy danych programu (.pdb) przechowuje informacje o debugowaniu i stanie projektu, co pozwala na łączenie przyrostowe konfiguracji debugowania programu. Plik PDB jest tworzony podczas kompilowania z **/debug**. Można tworzyć aplikacje z **/debug:full** lub **/debug:pdbonly**. Kompilowanie z użyciem **/debug:full** generuje kod z możliwością debugowania. Kompilowanie z użyciem **/debug:pdbonly** generuje .pdb, pliki, ale nie generuje `DebuggableAttribute` który informuje kompilator JIT czy informacje debugowania są dostępne. Użyj **/debug:pdbonly** Jeśli chcesz wygenerować .pdb, pliki do kompilacji wydania, którego chcesz debugować. Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) lub [/Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debuger używa ścieżka do pliku PDB w pliku EXE lub DLL można znaleźć pliku project.pdb. Jeśli debuger nie może znaleźć pliku PDB w tej lokalizacji lub ścieżka jest nieprawidłowa, debuger wyszukuje ścieżkę zawierającą plik EXE i następnie określone ścieżki symboli w **opcje** okno dialogowe. Ta ścieżka jest zazwyczaj **debugowanie** folderu w **symbole** węzła. Debuger nie załaduje pliku .pdb, który nie pasuje do debugowanego pliku wykonywalnego. Jeśli debuger nie może znaleźć pliku PDB **znajdowanie symboli** zostanie wyświetlone okno dialogowe, które umożliwia wyszukiwania symboli lub dodać dodatkowych lokalizacji do ścieżki wyszukiwania.  
  
 **Aplikacje sieci Web**  
  
 Plik konfiguracyjny aplikacji (Web.config) musi być ustawiony w tryb debugowania. Tryb debugowania powoduje, że ASP.NET generuje symbole dla dynamicznie generowanych plików i umożliwia debugerowi dołączenie do aplikacji ASP.NET. Visual Studio to automatycznie ustawia podczas uruchamiania debugowania, jeśli projekt został utworzony z szablonu projektów sieci Web.  
  
##  <a name="BKMK_Find_source_files"></a>Znajdź pliki źródłowe  
  
###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a>Gdy debuger wyszukuje pliki źródłowe  
 Debuger szuka plików źródłowych w następujących lokalizacjach:  
  
1.  Pliki otwarte w środowisku IDE wystąpienia programu Visual Studio, które uruchomiło debugera.  
  
2.  Pliki w rozwiązaniu, która jest otwarta w wystąpieniu programu Visual Studio.  
  
3.  Katalogi, które są określone w **wspólne właściwości**/**debugowania plików źródłowych** strony właściwości rozwiązania. (W **Eksploratora rozwiązań**, wybierz węzeł rozwiązania, kliknij prawym przyciskiem myszy i wybierz **właściwości**. )  
  
4.  Informacje źródłowe z .pdb modułu. Może to być lokalizacja pliku źródłowego, gdy moduł został skompilowany, lub może to być polecenie do serwera źródłowego.  
  
###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a>Znajdź i załadować plików źródłowych przy użyciu stron załadowano symbole Source/No nr  
 Gdy debuger dzieli wykonywania w lokalizacji, w którym plik źródłowy nie jest dostępne, zostaną wyświetlone **załadować źródła nie** lub **nie załadowano symboli** stron, które mogą pomóc Ci znaleźć pliku źródłowego. **Nie załadowano symboli** jest wyświetlany, gdy debuger nie może odnaleźć pliku symboli (.pdb) dla pliku wykonywalnego ukończyć jej wyszukiwania. Strona Brak symboli zawiera opcje wyszukiwania pliku. Jeśli plik .pdb zostanie znaleziony po wykonaniu jednej z opcji i debuger może pobrać plik źródłowy przy użyciu informacji w pliku symboli, źródło jest wyświetlane. W przeciwnym razie **załadować źródła nie** zostanie wyświetlona strona zawierający opis problemu. Na stronie są wyświetlane łącza do opcji mogących wykonywać akcje, które mogą rozwiązać problem.  
  
###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a>Dodawanie ścieżki wyszukiwania plików źródła do rozwiązania  
 Możesz określić sieć lub katalogi lokalne, aby w nich wyszukiwać pliki źródłowe.  
  
1.  Wybierz rozwiązanie w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości** z menu skrótów.  
  
2.  W obszarze **wspólne właściwości** węzła, wybierz **debugowania plików źródłowych**.  
  
3.  Kliknij folder ![narzędzia &#47; Opcje &#47; Debugowanie &#47; Ikona folderu symbole](../debugger/media/dbg_tools_options_foldersicon.png "DBG_Tools_Options_FoldersIcon") ikony. Można edytować tekst jest wyświetlany w **katalogi zawierające kod źródłowy** listy.  
  
4.  Dodaj ścieżkę, którą chcesz przeszukać.  
  
 Należy zauważyć, że przeszukiwany jest tylko określony katalog. Musisz dodać wpisy do wszystkich podkatalogów, które chcesz przeszukać.  
  
###  <a name="BKMK_Use_source_servers"></a>Użyj serwerów źródłowych  
 Gdy na komputerze lokalnym nie ma kodu źródłowego lub plik .pdb nie pasuje do kodu źródłowego, możesz użyć Serwera źródłowego, aby pomóc w debugowaniu aplikacji. Serwer źródłowy przyjmuje żądania dotyczące plików i zwraca rzeczywiste pliki. Serwer źródłowy jest uruchamiany za pomocą pliku DLL, o nazwie srcsrv.dll. Serwer źródłowy odczytuje plik .pdb aplikacji, który zawiera wskazówki do repozytorium kodu źródłowego, a także polecenia używane do pobierania kodu źródłowego z repozytorium. Możesz ograniczyć, jakie polecenia mogą być wykonywane z pliku .pdb aplikacji, poprzez wymienienie dozwolonych poleceń wewnątrz pliku o nazwie srcsrv.ini, który musi być umieszczony w tym samym katalogu, co srcsrv.dll i devenv.exe.  
  
> [!IMPORTANT]
>  Dowolne polecenia mogą być osadzone w pliku .pdb aplikacji, więc upewnij się, że można umieścić tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: debuger musi wykonać niezaufaną komendę](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.  
  
 **Aby włączyć korzystanie z serwera źródłowego**  
  
1.  Upewnij się, że postępujesz zgodnie ze środkami bezpieczeństwa opisanymi w poprzedniej sekcji.  
  
2.  Na **narzędzia** menu, wybierz **opcje**.  
  
     **Opcje** zostanie wyświetlone okno dialogowe.  
  
3.  W **debugowanie** węzła, wybierz **ogólne**.  
  
4.  Wybierz **Włącz obsługę serwera źródłowego** pole wyboru.  
  
     ![Włącz opcje serwera źródłowego](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  
  
5.  (Opcjonalnie) Wybierz żądane opcje podrzędne.  
  
     Należy pamiętać, że oba **Zezwalaj serwera źródłowego na częściowo zaufane zestawy (tylko kod zarządzany)** i **awsze Uruchamiaj polecenia niezaufanego serwera źródłowego bez monitowania** wzrasta zagrożenie bezpieczeństwa opisanych wyżej.  
  
## <a name="see-also"></a>Zobacz też  
[Opis plików Symbol i ustawienia programu Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)

[Symbol zdalnego .NET ładowania zmiany w programie Visual Studio 2012 i 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)