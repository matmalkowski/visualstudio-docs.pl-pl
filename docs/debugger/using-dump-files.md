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
ms.openlocfilehash: d072dcf839f31df2dba14a3293ed962cd3a68fce
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281029"
---
# <a name="use-dump-files-with-visual-studio"></a>Za pomocą programu Visual Studio przy użyciu plików zrzutu
Pliki zrzutu ze stertami lub bez nich; Tworzenie pliku zrzutu; Otwieranie pliku zrzutu; Znajdowanie plików binarnych, w pliku pdb i pliku źródłowego dla pliku zrzutu.

##  <a name="BKMK_What_is_a_dump_file_"></a> Co to jest plik zrzutu?
 A *plik zrzutu* jest migawką z aplikacji w punkcie w momencie dokonywana zrzutu. To pokazuje, jaki proces był wykonywany i które moduły zostały załadowane. Jeśli zrzut został zapisany z informacjami o stercie, plik zrzutu zawiera migawkę tego, co było w pamięci aplikacji w tamtym momencie. Otwieranie pliku zrzutu ze stertą w Visual Studio przypomina zatrzymywanie w punkcie przerwania sesji debugowania. Chociaż nie możesz kontynuować wykonywania, możesz przeanalizować stosy, wątki i wartości zmiennych aplikacji dla momentu zrzutu.

 Zrzuty są wykorzystywane głównie do debugowania problemów występujących na komputerach, które deweloper nie ma dostępu. Na przykład można użyć pliku zrzutu z komputera klienta, gdy nie można odtworzyć awarii przez klienta lub odłożyć na swojej maszynie. Zrzuty są również tworzone przez testerów w celu zapisania danych o awarii lub zawieszeniu, tak aby maszyna testowa mogła służyć do dalszego testowania. Debuger programu Visual Studio może zapisywać pliki zrzutu dla kodu zarządzanego lub natywnego. Debuger może załadować pliki zrzutu utworzone przez program Visual Studio lub przez inne programy, które zapisują pliki w *minizrzutu* formatu.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Naciśnięcie i przytrzymanie pliki zrzutu ze stertami lub bez
 Można tworzyć pliki zrzutu z informacjami o stercie lub bez nich.

-   **Pliki zrzutu ze stertami** zawierają migawkę pamięci aplikacji. Obejmuje to wartości zmiennych utworzonych w momencie zrzutu. Jeśli załadujesz plik zrzutu, który został zapisany ze stertą, program Visual Studio można załadować symbole, nawet jeśli nie można odnaleźć pliku binarnego aplikacji. Program Visual Studio zapisuje także pliki binarne załadowanych modułów macierzystych w pliku zrzutu, co znacznie ułatwia debugowanie.

-   **Zrzuć pliki bez stert** są znacznie mniejsze niż informacjami o stertach. Jednak debuger musi załadować pliki binarne aplikacji, aby znaleźć informacje o symbolach. Pliki binarne muszą dokładnie odpowiadać plikom binarnym, które były używane podczas tworzenia zrzutu. Tylko wartości zmiennych stosu są zapisywane w plikach zrzutu bez danych sterty.

##  <a name="BKMK_Requirements_and_limitations"></a> Wymagania i ograniczenia

-   Debugowanie plików zrzutu zoptymalizowanego kodu może być mylące. Na przykład wbudowywanie funkcji przez kompilator może spowodować nieoczekiwane stosy wywołań, a inne optymalizacje mogą zmienić okres istnienia zmiennych.

-   Pliki zrzutu z komputerów 64-bitowych muszą być debugowane na wystąpieniu programu Visual Studio, który jest uruchomiony na komputerze 64-bitowym.

-   W wersjach Visual Studio starszych niż VS 2013, zrzutów aplikacji 32-bitowych uruchamianych na komputerach 64-bitowych, które zostały zebrane przez kilka narzędzi (takich jak Menedżer zadań i WinDbg 64-bitowe), nie można otworzyć w programie Visual Studio. Ograniczenie to zostało usunięte w VS 2013.

-   Program Visual Studio umożliwia debugowanie plików zrzutu macierzystych aplikacji z urządzeń ARM. Program Visual Studio umożliwia również debugowanie plików zrzutu zarządzanych aplikacji z urządzeń ARM, ale tylko w macierzystym debugerze.

-   Aby debugować [trybu jądra](/windows-hardware/drivers/debugger/kernel-mode-dump-files) pliki zrzutu, Pobierz narzędzia do debugowania dla Windows, który jest częścią [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio nie umożliwia debugowania plików zrzutu zapisanych w starszym formacie zrzutu znanym jako [zrzut trybu użytkownika pełnego](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Należy zauważyć, że pełny zrzut trybu użytkownika to nie to samo, co zrzut ze stertą.

-   Aby debugować z [SOS.dll (SOS Debugging Extension)](/dotnet/framework/tools/sos-dll-sos-debugging-extension) w programie Visual Studio, należy zainstalować narzędzia debugowania dla Windows, który jest częścią [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk)

##  <a name="BKMK_Create_a_dump_file"></a> Tworzenie pliku zrzutu
 Aby utworzyć plik zrzutu z programu Visual Studio:

-   Podczas debugowania procesu w Visual Studio, można zapisać plik zrzutu po zatrzymaniu debugera w sytuacji wyjątku lub w punkcie przerwania. Wybierz **debugowania**, następnie **Zapisz zrzut jako**, następnie **debugowania**. W **Zapisz zrzut jako** dialogowym **Zapisz jako typ** listy, możesz wybrać **minizrzutu** lub **minizrzutu ze stertą** (ustawienie domyślne).

-   Za pomocą [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) włączone, można dołączyć debugera do awarii procesu, który działa poza debugera i następnie zapisać plik zrzutu. Zobacz [dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

 Można również tworzyć pliki zrzutu za pomocą dowolnego programu, który obsługuje format minizrzutu systemu Windows. Na przykład **Procdump** narzędzie wiersza polecenia z [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) można tworzyć pliki zrzutu awaryjnego procesów na podstawie wyzwalaczy lub na żądanie. Zobacz [wymagania i ograniczenia](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) w tym temacie, aby uzyskać dodatkowe informacje na temat korzystania z innych narzędzi do tworzenia plików zrzutu.

##  <a name="BKMK_Open_a_dump_file"></a> Otwieranie pliku zrzutu

1.  W programie Visual Studio, wybierz **pliku**, **Otwórz**, **pliku**.

2.  W **Otwórz plik** okno dialogowe Znajdź i zaznacz plik zrzutu. Będzie zazwyczaj miał rozszerzenie .dmp. Następnie wybierz **OK**.

3.  **Podsumowanie pliku zrzutu** zostanie wyświetlone okno. W tym oknie można wyświetlać informacje podsumowujące debugowanie dla pliku zrzutu, ustawić ścieżkę symboli, rozpocząć debugowanie i skopiować informacje podsumowujące do Schowka.

     ![Strona podsumowania minizrzutu](../debugger/media/dbg_dump_summarypage.png "DBG_DUMP_SummaryPage")

4.  Aby rozpocząć debugowanie, przejdź do **akcje** sekcji, a następnie wybierz opcję **debugowanie zarządzane tylko za pomocą**, **Debuguj tylko kod natywny** lub **debugowanie za pomocą mieszanego**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Znajdowanie plików binarnych, plików symboli (.pdb) i plików źródłowych
 Aby użyć wszystkich funkcji programu Visual Studio do debugowania pliku zrzutu, potrzebny jest dostęp do następujących elementów:

-   Plik .exe, dla którego zrobiono zrzut, i inne pliki binarne (biblioteki DLL itd.), które były używane w procesie zrzutu.

     Jeśli debugujesz zrzut z danymi sterty, Visual Studio może poradzić sobie z brakującymi plikami binarnymi dla niektórych modułów, ale musi mieć pliki binarne dla wystarczającej liczby modułów, aby generować prawidłowe stosy wywołań. Program Visual Studio zawiera moduły macierzyste w pliku zrzutu ze stertą.

-   Pliki symboli (.pdb) dla pliku .exe i innych plików binarnych.

-   Pliki źródłowe dla modułów, które cię interesują.

     Plik wykonywalny i pliki .pdb muszą dokładnie odpowiadać wersji i kompilacji plików używanych podczas tworzenia zrzutu.

     Można debugować z użyciem deasemblacji modułów, jeśli nie możesz znaleźć plików źródłowych

 **Domyślne ścieżki wyszukiwania dla plików wykonywalnych**

 Program Visual Studio automatycznie przeszukuje następujące lokalizacje plików wykonywalnych, które nie są uwzględnione w pliku zrzutu:

1.  Katalog zawierający plik zrzutu.

2.  Ścieżka modułu, który jest określony w pliku zrzutu. Jest to ścieżka modułu na komputerze, na który pobrano zrzut.

3.  Ścieżki symboli określone w **debugowanie**, **opcje**, **symbole** stronie programu Visual Studio **narzędzia**, **opcje**  okno dialogowe. Do wyszukiwania na tej stronie można dodać więcej lokalizacji.

 **Przy użyciu nie znaleziono pliku binarnego > Symbol > Źródło strony**

 Jeśli program Visual Studio nie może znaleźć plików potrzebnych do debugowania modułu w zrzucie, wyświetlana jest odpowiednia strona (**nie znaleziono pliku binarnego**, **nie znaleziono symboli**, lub **nie znaleziono źródła**). Strony te zawierają szczegółowe informacje o przyczynie problemu i zawierają łącza do czynności, które mogą pomóc w określeniu poprawnej lokalizacji plików. Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Zobacz także

- [Debugowanie just in time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)