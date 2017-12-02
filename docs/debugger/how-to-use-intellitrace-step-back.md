---
title: "Wyświetl migawkę przy użyciu funkcji IntelliTrace krok zwrotnego — Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e8da202cf8ae5680bede1ec4b2f2c8984624e4e
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2017
---
# <a name="view-snapshots-using-intellitrace-step-back"></a>Migawki widoku przy użyciu zwrotnego krok IntelliTrace
Krok zwrotnego IntelliTrace automatycznie tworzy migawkę aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawki umożliwiają wróć na poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, ponieważ był w przeszłości. IntelliTrace krok wstecz może zaoszczędzić czas podczas chcesz zobacz poprzedni stan aplikacji, ale nie chcesz uruchomić ponownie debugowania lub Utwórz ponownie stan żądanej aplikacji.

Krok IntelliTrace zwrotnego jest dostępna, począwszy od programu Visual Studio Enterprise 2017 wersji 15.5 lub nowszej, a wymaga systemu Windows 10 Anniversary aktualizacji lub nowszej. Funkcja jest obecnie obsługiwane dla debugowania ASP.NET, WinForms WPF, konsoli zarządzanych aplikacji i bibliotek klas zarządzanych. Debugowanie aplikacji platformy ASP.NET Core .NET Core i platformy uniwersalnej systemu Windows nie jest obecnie obsługiwane. 
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Włącz tryb migawki i zdarzenia funkcji IntelliTrace 
Aby włączyć tę funkcję, przejdź do **Narzędzia > Opcje > IntelliTrace** ustawienia, a następnie wybierz opcję **IntelliTrace zdarzenia i migawek**. 

![Włącz tryb zdarzeń funkcji IntelliTrace i migawki](../debugger/media/intellitrace-enable-snapshots.png "tryb migawki i włączyć zdarzeń funkcji IntelliTrace")

IntelliTrace tworzy migawkę proces aplikacji w debugerze każdego zdarzenia krok i punktu przerwania. Te zdarzenia są rejestrowane w **zdarzenia** karcie **narzędzia diagnostyczne** okna, oraz inne zdarzenia funkcji IntelliTrace. Aby otworzyć to okno, wybierz polecenie **Debug / Windows / Pokaż narzędzia diagnostyczne**.

Ikona aparatu obok zdarzeń, dla których są dostępne migawki. 

![Karta zdarzeń z migawkami](../debugger/media/intellitrace-events-tab-with-snapshots.png "kartę zdarzenia z migawkami punktów przerwania i kroki")

Ze względu na wydajność migawki nie są brane podczas wykonywania kroków bardzo szybko. Jeśli brak aparatu ikony obok kroku, spróbuj krokowe wykonywanie wolniej.

## <a name="navigate-and-view-snapshots"></a>Nawigacja i wyświetlanie migawek

Można przechodzić między zdarzeniami przy użyciu **krok z poprzednimi wersjami (Alt + [)** i **krok do przodu (Alt +])** przycisków na pasku narzędzi debugowania. Tych przycisków nawigacji zdarzenia, które są widoczne w **zdarzenia** karcie **okno narzędzia diagnostyczne**. Wykonywanie krok po kroku do przodu lub do tyłu na zdarzenie automatycznie aktywuje debugowania historycznego wybranego zdarzenia.

![Krok wstecz i przekazywać je przycisków](../debugger/media/intellitrace-step-back-icons-description.png "krok do tyłu i do przodu krok przycisków")

Gdy krok wstecz lub krok do przodu, Visual Studio wprowadza tryb debugowania historycznego. W tym trybie kontekstu debugera przełączników do momentu, gdy zarejestrowano wybranego zdarzenia. Visual Studio również przesunie wskaźnik do odpowiedniego wiersza kodu w oknie źródła. 

W tym widoku możesz sprawdzić wartości w **stos wywołań**, **zmiennych lokalnych**, **automatycznych**, i **czujki** systemu windows. Można również ustawić kursor nad zmienne do wyświetlania etykietek danych i wykonywania wyrażenia w **Immediate** okna. Dane, które pojawi się z migawki procesu aplikacji, w tym punkcie w czasie.

Tak, na przykład, jeżeli został trafiony punkt przerwania i podjąć krok (**F10**), **krok do tyłu** przycisk umieszcza Visual Studio w trybie historycznych w wierszu kodu odpowiadający punktu przerwania. 

![Tryb historycznych uaktywnianie na zdarzenie z migawki](../debugger/media/intellitrace-historical-mode-with-snapshot.png "tryb historycznych uaktywnianie na zdarzenie z migawki")

Aby powrócić do wykonania na żywo, wybierz **Kontynuuj (F5)** lub kliknij przycisk **wrócić do debugowania na żywo** łącze w pasku informacyjnym. 

Można również wyświetlić migawka **zdarzenia** kartę. Wybierz zdarzenie z migawki, a następnie kliknij przycisk **Uaktywnij debugowanie historyczne**. Możesz również kliknąć ikonę aparatu, aby aktywować debugowania historycznego.

![Aktywuj debugowania historycznego na zdarzenie](../debugger/media/intellitrace-activate-historical-debugging.png "Uaktywnij debugowanie historyczne na zdarzenia")

W odróżnieniu od **ustawienia następnej instrukcji** polecenia Wyświetlanie migawki nie ponownie kodu; daje widok statyczny stan aplikacji w punkcie w czasie, który wystąpił w przeszłości.

![Omówienie zwrotnego krok IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Omówienie programu IntelliTrace krok zwrotnego")

## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak sprawdzić zmienne w Visual Studio, zobacz [debugera samouczek funkcji](../debugger/debugger-feature-tour.md)  
 Omówienie debugowania historycznego, zobacz [debugowania historycznego](../debugger/historical-debugging.md).  

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

* Podczas zapisywania pliku z **Debuguj > IntelliTrace > Zapisz IntelliTrace sesji** w trybie zdarzeń i migawki, dodatkowe dane przechwycone z migawek nie jest dostępny w pliku .itrace. Punkt przerwania i krok zdarzeń Zobacz tych samych informacji tak, jakby plik zapisaną w trybie tylko do zdarzeń funkcji IntelliTrace. 
