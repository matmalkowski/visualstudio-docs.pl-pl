---
title: Przy użyciu plików zrzutu | Dokumentacja firmy Microsoft
ms.custom: H1HackMay2017
ms.date: 03/08/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b06f88433f8b744a9bea7dfcce95b0a095cf7890
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481830"
---
# <a name="use-dump-files-with-visual-studio"></a>Program Visual Studio przy użyciu plików zrzutu
Pliki zrzutu z lub bez stosów; Utwórz plik zrzutu; Otwórz plik zrzutu; Znajdowanie danych binarnych, w pliku pdb i pliku źródłowego dla pliku zrzutu.
  
##  <a name="BKMK_What_is_a_dump_file_"></a> Co to jest plik zrzutu?  
 A *plik zrzutu* jest migawką aplikacji w punkcie w czasie zrzutu jest zajęta. To pokazuje, jaki proces był wykonywany i które moduły zostały załadowane. Jeśli zrzut został zapisany z informacjami o stercie, plik zrzutu zawiera migawkę tego, co było w pamięci aplikacji w tamtym momencie. Otwieranie pliku zrzutu ze stertą w Visual Studio przypomina zatrzymywanie w punkcie przerwania sesji debugowania. Chociaż nie możesz kontynuować wykonywania, możesz przeanalizować stosy, wątki i wartości zmiennych aplikacji dla momentu zrzutu.  
  
 Zrzuty są używane przede wszystkim do debugowania problemów występujących na maszynach, które projektanta nie ma dostępu do. Na przykład można użyć pliku zrzutu z komputera klienta, gdy nie można odtworzyć awarię klienta, lub Rozłącz na tym komputerze. Zrzuty są również tworzone przez testerów w celu zapisania danych o awarii lub zawieszeniu, tak aby maszyna testowa mogła służyć do dalszego testowania. Debuger programu Visual Studio może zapisywać pliki zrzutu dla kodu zarządzanego lub natywnego. Debuger może ładować pliki zrzutu, które zostały utworzone przez program Visual Studio lub przez inne programy, które zapisują pliki w *minizrzutu* format.  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Pliki zrzutu, lub bez stert  
 Można tworzyć pliki zrzutu z informacjami o stercie lub bez nich.  
  
-   **Zrzuć pliki z stosów** zawierającego migawkę pamięci aplikacji. Obejmuje to wartości zmiennych utworzonych w momencie zrzutu. Jeśli załadujesz plik zrzutu, który został zapisany ze stertą, program Visual Studio można załadować symbole, nawet jeśli nie można odnaleźć pliku binarnego aplikacji. Program Visual Studio zapisuje także pliki binarne załadowanych modułów macierzystych w pliku zrzutu, co znacznie ułatwia debugowanie.  
  
-   **Zrzuć pliki bez stosów** są znacznie mniejszy niż zrzuty stosu informacje. Jednak debuger musi załadować pliki binarne aplikacji, aby znaleźć informacje o symbolach. Pliki binarne muszą dokładnie odpowiadać plikom binarnym, które były używane podczas tworzenia zrzutu. Tylko wartości zmiennych stosu są zapisywane w plikach zrzutu bez danych sterty.  
  
##  <a name="BKMK_Requirements_and_limitations"></a> Wymagania i ograniczenia  
  
-   Debugowanie plików zrzutu zoptymalizowanego kodu może być mylące. Na przykład wbudowywanie funkcji przez kompilator może spowodować nieoczekiwane stosy wywołań, a inne optymalizacje mogą zmienić okres istnienia zmiennych.  
  
-   Pliki zrzutu z komputerów 64-bitowych muszą być debugowane na wystąpieniu programu Visual Studio, który jest uruchomiony na komputerze 64-bitowym.  
  
-   W wersjach Visual Studio starszych niż VS 2013, zrzutów aplikacji 32-bitowych uruchamianych na komputerach 64-bitowych, które zostały zebrane przez kilka narzędzi (takich jak Menedżer zadań i WinDbg 64-bitowe), nie można otworzyć w programie Visual Studio. Ograniczenie to zostało usunięte w VS 2013.  
  
-   Program Visual Studio umożliwia debugowanie plików zrzutu macierzystych aplikacji z urządzeń ARM. Program Visual Studio umożliwia również debugowanie plików zrzutu zarządzanych aplikacji z urządzeń ARM, ale tylko w macierzystym debugerze.  
  
-   Aby debugować [trybu jądra](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) Zrzuć pliki, Pobierz narzędzia debugowania dla systemu Windows, który jest częścią [zestaw sterowników systemu Windows (WDK)](/windows/hardware/windows-driver-kit). 
  
-   Program Visual Studio nie może debugować pliki zrzutu zapisane w formacie zrzutu starsze znany jako [zrzut pełnego trybu użytkownika](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Należy zauważyć, że pełny zrzut trybu użytkownika to nie to samo, co zrzut ze stertą.  
  
-   Aby debugować z [SOS.dll (rozszerzenie debugowania SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension) w programie Visual Studio należy zainstalować narzędzia debugowania dla systemu Windows, który jest częścią [zestaw sterowników systemu Windows (WDK)](/windows/hardware/windows-driver-kit) 
  
##  <a name="BKMK_Create_a_dump_file"></a> Utwórz plik zrzutu  
 Aby utworzyć plik zrzutu z programu Visual Studio:  
  
-   Podczas debugowania procesu w Visual Studio, można zapisać plik zrzutu po zatrzymaniu debugera w sytuacji wyjątku lub w punkcie przerwania. Wybierz **debugowania**, następnie **zapisać zrzutu jako**, następnie **debugowania**. W **zapisać zrzutu jako** okna dialogowego, **Zapisz jako typ** listy, możesz wybrać **minizrzutu** lub **minizrzutu ze stertą** (ustawienie domyślne).  
  
-   Z [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) włączone, można uruchomić debugera awaria procesu, który działa poza debugerem i następnie zapisz plik zrzutu. Zobacz [dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 Można również tworzyć pliki zrzutu za pomocą dowolnego programu, który obsługuje format minizrzutu systemu Windows. Na przykład **Procdump** narzędzia wiersza polecenia z [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) można utworzyć pliki zrzutu awaryjnego procesu na podstawie wyzwalaczy lub na żądanie. Zobacz [wymagania i ograniczenia](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) w tym temacie, aby uzyskać dodatkowe informacje przy użyciu innych narzędzi do tworzenia plików zrzutu. 
  
##  <a name="BKMK_Open_a_dump_file"></a> Otwórz plik zrzutu  
  
1.  W programie Visual Studio, wybierz **pliku**, **Otwórz**, **pliku**.  
  
2.  W **Otwórz plik** okno Znajdź i wybierz plik zrzutu. Będzie zazwyczaj miał rozszerzenie .dmp. Następnie wybierz pozycję **OK**.  
  
3.  **Podsumowanie pliku zrzutu** zostanie wyświetlone okno. W tym oknie można wyświetlać informacje podsumowujące debugowanie dla pliku zrzutu, ustawić ścieżkę symboli, rozpocząć debugowanie i skopiować informacje podsumowujące do Schowka.  
  
     ![Strona podsumowania minizrzutu](../debugger/media/dbg_dump_summarypage.png "DBG_DUMP_SummaryPage")  
  
4.  Aby rozpocząć debugowanie, przejdź do **akcje** sekcji, a następnie wybrać opcję **debugowania zarządzanego tylko**, **debugowania wyłącznie natywnego** lub **debugowanie przy użyciu Mixed**.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Znajdź pliki binarne, pliki symboli (.pdb) i pliki źródłowe  
 Aby użyć wszystkich funkcji programu Visual Studio do debugowania pliku zrzutu, potrzebny jest dostęp do następujących elementów:  
  
-   Plik .exe, dla którego zrobiono zrzut, i inne pliki binarne (biblioteki DLL itd.), które były używane w procesie zrzutu.  
  
     Jeśli debugujesz zrzut z danymi sterty, Visual Studio może poradzić sobie z brakującymi plikami binarnymi dla niektórych modułów, ale musi mieć pliki binarne dla wystarczającej liczby modułów, aby generować prawidłowe stosy wywołań. Program Visual Studio zawiera moduły macierzyste w pliku zrzutu ze stertą.  
  
-   Pliki symboli (.pdb) dla pliku .exe i innych plików binarnych.  
  
-   Pliki źródłowe dla modułów, które cię interesują.  
  
     Plik wykonywalny i pliki .pdb muszą dokładnie odpowiadać wersji i kompilacji plików używanych podczas tworzenia zrzutu.  
  
     Można debugować przy użyciu dezasemblacji modułów, jeśli nie można znaleźć plików źródłowych  
  
 **Domyślne ścieżki wyszukiwania plików wykonywalnych**  
  
 Visual Studio automatycznie wyszukuje te lokalizacje plików wykonywalnych, które nie są uwzględnione w pliku zrzutu:  
  
1.  Katalog zawierający plik zrzutu.  
  
2.  Ścieżka modułu, który jest określony w pliku zrzutu. Jest to ścieżka modułu na komputerze, na który pobrano zrzut.  
  
3.  Ścieżki symboli określone w **debugowanie**, **opcje**, **symbole** strony programu Visual Studio **narzędzia**, **opcje**  okno dialogowe. Do wyszukiwania na tej stronie można dodać więcej lokalizacji.  
  
 **Za pomocą binarnego nr > Symbol > Źródło strony**  
  
 Jeśli program Visual Studio nie może znaleźć plików potrzebnych do modułu w zrzutu debugowania, wyświetla odpowiedniej strony (**nie znaleziono binarne**, **znaleziono symboli nie**, lub **nie znaleziono źródła**). Strony te zawierają szczegółowe informacje o przyczynie problemu i zawierają łącza do czynności, które mogą pomóc w określeniu poprawnej lokalizacji plików. Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)