---
title: Wyświetl migawkę przy użyciu zwrotnego krok IntelliTrace
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 05/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68fec4e10d172f79908e57828c542a444d081b50
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="view-snapshots-using-intellitrace-step-back-in-visual-studio"></a>Zwroty kroku migawki widoku przy użyciu funkcji IntelliTrace w programie Visual Studio

Krok zwrotnego IntelliTrace automatycznie tworzy migawkę aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawki umożliwiają wróć na poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, ponieważ był w przeszłości. IntelliTrace krok wstecz może zaoszczędzić czas podczas chcesz zobacz poprzedni stan aplikacji, ale nie chcesz uruchomić ponownie debugowania lub Utwórz ponownie stan żądanej aplikacji.

Krok IntelliTrace zwrotnego jest dostępna, począwszy od programu Visual Studio Enterprise 2017 wersji 15.5 lub nowszej, a wymaga systemu Windows 10 Anniversary aktualizacji lub nowszej. Funkcja jest obecnie obsługiwane dla debugowania ASP.NET, WinForms WPF, konsoli zarządzanych aplikacji i bibliotek klas zarządzanych. Począwszy od programu Visual Studio Enterprise 2017 wersji 15.7 preview 1, funkcja również jest obsługiwana dla platformy .NET Core i ASP.NET Core. Debugowanie aplikacji platformy uniwersalnej systemu Windows nie jest obecnie obsługiwane.

W tym samouczku obejmują:

> [!div class="checklist"]
> * Włącz migawki i zdarzenia funkcji Intellitrace
> * Przejdź zdarzenia przy użyciu polecenia krok wstecz i następny krok
> * Wyświetl zdarzenia migawki
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Włącz tryb migawki i zdarzenia funkcji IntelliTrace 

1. Otwórz projekt w programie Visual Studio Enterprise.

1. Otwórz **narzędzia** > **opcje** > **IntelliTrace** ustawienia, a następnie wybierz opcję **IntelliTrace zdarzeń i migawki** . 

    ![Włącz tryb zdarzeń funkcji IntelliTrace i migawki](../debugger/media/intellitrace-enable-snapshots.png "tryb migawki i włączyć zdarzeń funkcji IntelliTrace")

1. Jeśli chcesz skonfigurować opcje wyświetlania migawek na wyjątki, wybierz **IntelliTrace** > **zaawansowane** z **opcje** okno dialogowe.

    Te opcje są dostępne w programie Visual Studio Enterprise 2017 wersji 15.7.

    ![Skonfiguruj zachowanie dla migawki na wyjątki](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Po włączeniu zdarzeń i migawki, tworzenie migawek na wyjątki jest również domyślnie włączone. Możesz wyłączyć migawek na wyjątki przez wyłączenie **zbierane migawki na zdarzeń wyjątków**. Gdy ta funkcja jest włączona, migawek są wykonywane dla nieobsługiwanych wyjątków. Dla wyjątków obsłużonych migawki są wykonywane tylko wtedy, gdy wyjątku i jeśli nie jest ponownie zgłosić wyjątek zgłoszony wcześniej. Maksymalna liczba migawek na wyjątki można ustawić, wybierając wartość z listy rozwijanej. Maksymalna stosuje za każdym razem przez aplikację przejdzie w tryb przerwania (na przykład jeśli aplikacja trafienia punktu przerwania).

    > [!NOTE]
    > Migawki są wykonywane tylko dla zdarzeń dotyczących wyjątków tego rekordów funkcji IntelliTrace. Jakie zdarzenia funkcji IntelliTrace rekordy można określić, wybierając **narzędzia** > **opcje** > **zdarzeń funkcji IntelliTrace**.

1. W projekcie, ustawić co najmniej jednego punktu przerwania i Rozpocznij debugowanie (naciśnij klawisz **F5**), lub uruchomić debugowanie przy przechodzeniu przez kod (**F10** lub **F11**).

    IntelliTrace tworzy migawkę proces aplikacji na każdym kroku debugera, zdarzenie punktu przerwania i zdarzeń nieobsługiwany wyjątek. Te zdarzenia są rejestrowane w **zdarzenia** karcie **narzędzia diagnostyczne** okna, oraz inne zdarzenia funkcji IntelliTrace. Aby otworzyć to okno, wybierz polecenie **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

    Ikona aparatu obok zdarzeń, dla których są dostępne migawki. 

    ![Karta zdarzeń z migawkami](../debugger/media/intellitrace-events-tab-with-snapshots.png "kartę zdarzenia z migawkami punktów przerwania i kroki")

    Ze względu na wydajność migawki nie są brane podczas wykonywania kroków bardzo szybko. Jeśli brak aparatu ikony obok kroku, spróbuj krokowe wykonywanie wolniej.

## <a name="navigate-and-view-snapshots"></a>Nawigacja i wyświetlanie migawek

1. Przechodzenie między zdarzeniami przy użyciu **krok z poprzednimi wersjami (Alt + [)** i **krok do przodu (Alt +])** przycisków na pasku narzędzi debugowania.

    Tych przycisków nawigacji zdarzenia, które są widoczne w **zdarzenia** karcie **okno narzędzia diagnostyczne**. Wykonywanie krok po kroku do przodu lub do tyłu na zdarzenie automatycznie aktywuje [debugowania historycznego](../debugger/historical-debugging.md) na wybranego zdarzenia.

    ![Krok wstecz i przekazywać je przycisków](../debugger/media/intellitrace-step-back-icons-description.png "krok do tyłu i do przodu krok przycisków")

    Gdy krok wstecz lub krok do przodu, Visual Studio wprowadza tryb debugowania historycznego. W tym trybie kontekstu debugera przełączników do momentu, gdy zarejestrowano wybranego zdarzenia. Visual Studio również przesunie wskaźnik do odpowiedniego wiersza kodu w oknie źródła. 

    W tym widoku możesz sprawdzić wartości w **stos wywołań**, **zmiennych lokalnych**, **automatycznych**, i **czujki** systemu windows. Można również ustawić kursor nad zmienne do wyświetlania etykietek danych i wykonywania wyrażenia w **Immediate** okna. Dane, które pojawi się z migawki procesu aplikacji, w tym punkcie w czasie.

    Tak, na przykład, jeżeli został trafiony punkt przerwania i podjąć krok (**F10**), **krok do tyłu** przycisk umieszcza Visual Studio w trybie historycznych w wierszu kodu odpowiadający punktu przerwania. 

    ![Tryb historycznych uaktywnianie na zdarzenie z migawki](../debugger/media/intellitrace-historical-mode-with-snapshot.png "tryb historycznych uaktywnianie na zdarzenie z migawki")

2. Aby powrócić do wykonania na żywo, wybierz **Kontynuuj (F5)** lub kliknij przycisk **wrócić do debugowania na żywo** łącze w pasku informacyjnym. 

3. Można również wyświetlić migawka **zdarzenia** kartę. Aby to zrobić, wybierz zdarzenie z migawki, a następnie kliknij przycisk **Uaktywnij debugowanie historyczne**.

    ![Aktywuj debugowania historycznego na zdarzenie](../debugger/media/intellitrace-activate-historical-debugging.png "Uaktywnij debugowanie historyczne na zdarzenia")

    W odróżnieniu od **ustawienia następnej instrukcji** polecenia Wyświetlanie migawki nie ponownie kodu; daje widok statyczny stan aplikacji w punkcie w czasie, który wystąpił w przeszłości.

    ![Omówienie zwrotnego krok IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Omówienie programu IntelliTrace krok zwrotnego")

    Aby dowiedzieć się więcej na temat inspekcji zmienne w Visual Studio, zobacz [debugera samouczek funkcji](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Często zadawane pytania

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Jak krok zwrotnego IntelliTrace jest inny niż tryb tylko zdarzenia funkcji IntelliTrace?

IntelliTrace w trybie tylko do zdarzeń umożliwiają aktywowania debugowania historycznego kroki debugera i punktów przerwania. Jednak IntelliTrace przechwytuje tylko dane w **zmiennych lokalnych** i **automatycznych** systemu windows, jeśli systemu windows są otwarte, a następnie przechwytuje tylko dane, które jest rozwinięty i w widoku. W trybie tylko do zdarzeń często nie masz pełny widok zmiennych i obiektów złożonych. Ponadto wyrażenia obliczania i wyświetlania danych w **czujki** okno nie jest obsługiwane. 

W trybie zdarzeń i migawek IntelliTrace przechwytuje migawkę całego procesu aplikacji, w tym złożone obiekty. W wierszu kodu można zobaczyć te same informacje tak, jakby były zatrzymany w punkcie przerwania (i nie ma znaczenia, czy wcześniej powiększone informacje). Szacowanie wyrażeń jest również obsługiwany w przypadku wyświetlania migawki.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Co to jest jego wpływ na wydajność tej funkcji? 

Wpływ na ogólną wydajność wykonywania krokowego zależy od aplikacji. Obciążenie związane z migawki jest około 30 ms. Gdy migawki, proces aplikacji jest rozwidlone i rozwidlonych kopiowania jest wstrzymana. Po wyświetleniu migawkę programu Visual Studio jest dołączenie do rozwidlonych kopię procesu. Dla każdej migawki Visual Studio kopiuje tabeli strony i ustawia stron kopii przy zapisie. Zmiana obiektów na stercie między krokami debugera z skojarzone migawki tabeli odpowiednich strony jest następnie skopiowana, co pamięci minimalne kosztów. Jeśli program Visual Studio wykryje, że nie ma wystarczającej ilości pamięci do tworzenia migawki, go nie przyjmuje jeden.
 
## <a name="known-issues"></a>Znane problemy  
* Jeśli używasz trybu migawki i zdarzenia funkcji IntelliTrace w wersjach systemu Windows starszych niż Windows 10 spadek twórców aktualizacji (RS3) i platforma cel debugowania aplikacji ma ustawioną wartość x86, IntelliTrace nie migawek.

    Obejście problemu:
    * Instalacji lub uaktualnienia do systemu Windows 10 spadek twórców aktualizacji (RS3). 
    * Można również: 
        1. Zainstaluj zestaw narzędzi VC++ 2015.3 v140 dla składnika komputera stacjonarnego (x86, x64) przy użyciu Instalatora programu Visual Studio.
        2. Skompiluj aplikację docelową.
        3. Z poziomu wiersza polecenia, użyj narzędzia polecenia editbin, aby ustawić `Largeaddressaware` flagi dla elementu docelowego pliku wykonywalnego. Na przykład można użyć tego polecenia (po zaktualizowaniu ścieżki): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" / largeaddressaware "C:\Path\To\Application\app.exe".
        4. Aby rozpocząć debugowanie, naciśnij klawisz **F5**. Teraz migawki są wykonywane na kroki debugera i punkty przerwania.

        > [!Note]
        > `Largeaddressaware` Musi zostać ustawiona flaga za każdym razem pliku wykonywalnego, który zostanie skompilowany ponownie za zmiany.

* Podczas procesu aplikacji migawki w aplikacji korzystającej z utrwalonego pliku mapowane w pamięci, proces z migawką utrzymuje wyłącznej blokady plików mapowanych na pamięć (nawet po proces nadrzędny wydała jego blokady). Inne procesy mogą nadal odczytywać, ale nie zapisywać do pliku mapowanych na pamięć.

    Obejście problemu:
    * Usuń wszystkie migawki poprzez zakończenie sesji debugowania. 

* Podczas debugowania aplikacji, których proces ma dużą liczbę regiony pamięci unikatowy, takie jak aplikacja, która ładuje wiele bibliotek DLL, wzmocnienie wydajności z migawkami włączone może mieć wpływ na. Ten problem zostanie rozwiązany w przyszłej wersji systemu Windows. Jeśli występuje ten problem, dotrzeć do nas na stepback@microsoft.com. 

* Podczas zapisywania pliku z **Debuguj > IntelliTrace > Zapisz IntelliTrace sesji** w trybie zdarzeń i migawki, dodatkowe dane przechwycone z migawek nie jest dostępny w pliku .itrace. Punkt przerwania i krok zdarzeń Zobacz tych samych informacji tak, jakby plik zapisaną w trybie tylko do zdarzeń funkcji IntelliTrace. 

## <a name="next-steps"></a>Następne kroki

W tym samouczku kiedy znasz już sposób użycia zwrotnego krok IntelliTrace. Możesz dowiedzieć się więcej na temat innych funkcji IntelliTrace.

> [!div class="nextstepaction"]
> [Funkcje IntelliTrace](../debugger/intellitrace-features.md)
