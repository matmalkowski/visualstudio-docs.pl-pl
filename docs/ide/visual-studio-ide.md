---
title: Omówienie programu Visual Studio 2017 r.
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9e1149803516e0b411bfef1da06fd6e1af9a12f
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282729"
---
# <a name="visual-studio-ide-overview"></a>Visual Studio IDE — omówienie

Środowisko projektowe interaktywne programu Visual Studio (IDE) jest creative konsoli uruchamianie, który służy do wyświetlania i edytowania kodu, następnie Debuguj, kompilacji i publikowanie aplikacji.

Program Visual Studio jest dostępna dla systemów Windows i Mac. [Visual Studio for Mac](/visualstudio/mac/) zawiera te same funkcje co program Visual Studio 2017 i jest zoptymalizowany pod kątem tworzenia aplikacji i platform i przenośnych.

Ten artykuł dotyczy programu Visual Studio 2017 r dla systemu Windows. Go przedstawiono podstawowe funkcje programu IDE. Omówimy niektóre elementy można zrobić za pomocą programu Visual Studio, w tym tworzenie prostego projektu, za pomocą funkcji IntelliSense jako kodowania pomocy i debugowania aplikacji, aby wyświetlić wartość zmiennej podczas wykonywania programu. Firma Microsoft będzie także zapoznaj się z różnych okien narzędzi.

## <a name="install-the-visual-studio-ide"></a>Zainstaluj program Visual Studio IDE

Aby rozpocząć, [pobierania programu Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) i zainstaluj go w tym systemie.

Moduły Instalator umożliwia wybierz i zainstaluj *obciążeń*, które są grup funkcji potrzebnych do programowania języka lub platformy wolisz. Wykonanie czynności dla [tworzenia program](#create-a-program), pamiętaj o wybraniu **aplikacji dla wielu platform .NET Core** obciążenie podczas instalacji. Tematy szybkiego startu, takich jak [wprowadzenie do języka C++ w programie Visual Studio](getting-started-with-cpp-in-visual-studio.md), zawiera instrukcje dotyczące instalowania innych obciążeń.

![Instalator programu Visual Studio](../ide/media/overview-net-core-workload.png)

Po uruchomieniu programu Visual Studio po raz pierwszy, można opcjonalnie Zaloguj się przy użyciu konta Microsoft lub pracy lub konta służbowego.

## <a name="tour-of-the-ide"></a>Samouczek środowiska IDE

Aby dać visual Omówienie programu Visual Studio, na poniższej ilustracji przedstawiono Visual Studio z otwartego projektu oraz kilka okien narzędzi kluczy, które najprawdopodobniej będą używane:

![Visual Studio IDE](../ide/media/visualstudioide.png)

- [Eksplorator rozwiązań](../ide/solutions-and-projects-in-visual-studio.md) umożliwia przeglądanie, przejdź i zarządzanie plikami kodu. Eksplorator rozwiązań może pomóc uporządkowanie kodu przez grupowanie plików do rozwiązania i projekty.

- [Edytor](../ide/writing-code-in-the-code-and-text-editor.md) okna, w którym będzie prawdopodobnie spędzają większość czasu, zawiera kod i umożliwia edytowanie kodu źródłowego i projektu interfejsu użytkownika.

- [Okno danych wyjściowych](../ide/reference/output-window.md) jest, gdzie Visual Studio wysyła jej powiadomień, takie jak debugowanie i komunikaty o błędach, ostrzeżenia kompilatora, publikowania komunikatów o stanie i. Każde źródło komunikatu ma własną kartę.

- [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) umożliwia śledzenie elementów roboczych i udostępnianie kodu z innymi użytkownikami przy użyciu technologii kontroli wersji, takich jak [Git](https://git-scm.com/) i [kontroli wersji typu Team Foundation (TFVC)](/vsts/tfvc/overview).

Poniżej przedstawiono niektóre funkcje popularnych wydajność w programie Visual Studio:

- [Refaktoryzacja](../ide/refactoring-in-visual-studio.md) obejmuje operacje, takie jak inteligentnego zmiana nazwy zmiennych, przenoszenie wybrane wiersze kodu do oddzielnych funkcji przenoszenia kodu do innych lokalizacji, opcję parametrów funkcji i inne.

   ![Refaktoryzacja](../ide/media/VSIDE_refactor.png)

- [IntelliSense](../ide/using-intellisense.md) jest ogólny termin zbiór popularnych funkcji wyświetlania informacji o typie o kodzie bezpośrednio w edytorze i, w niektórych przypadkach można zapisać małe fragmenty kodu. Przypomina o dokumentacji podstawowej wbudowany w edytorze, co pozwala uniknąć konieczności wyszukiwania informacji o typie w oknie Pomoc. Funkcje IntelliSense zależy od języka. Aby uzyskać więcej informacji, zobacz [C#, IntelliSense](../ide/visual-csharp-intellisense.md), [IntelliSense dla programu Visual C++](../ide/visual-cpp-intellisense.md), [IntelliSense dla JavaScript](../ide/javascript-intellisense.md), i [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md). Na poniższej ilustracji przedstawiono niektóre funkcje IntelliSense w miejscu pracy:

   ![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2017_Intellisense.png)

- [Szybkie uruchamianie](../ide/reference/quick-launch-environment-options-dialog-box.md) pole wyszukiwania jest to dobry sposób na szybkie wyszukiwanie informacji w programie Visual Studio. Po prostu zacznij wpisywać ciąg nazwy niezależnie od, którego szukasz, i Visual Studio listy wyników przyjmujących dokładnie której ma nastąpić przejście. **Szybkie uruchamianie** także pokazuje łącza uruchamiane **Instalator programu Visual Studio** obciążenia lub poszczególnych składników.

   ![Pole wyszukiwania w usłudze szybkiego uruchamiania](../ide/media/VSIDE_Tour_QuickLaunch.png)

- **Zygzaki** są faliste podkreślenie, które generują alerty błędów lub potencjalnych problemów w kodzie w czasie rzeczywistym w trakcie pisania. Dzięki temu można rozwiązać je natychmiast bez oczekiwania na błąd mają być wykryte podczas kompilacji lub czasu wykonywania. Jeśli Aktywuj wężyk, pojawi się dodatkowe informacje o tym błędzie. Żarówka może również zostać wyświetlony na lewym marginesie z akcjami, aby naprawić błąd. Aby uzyskać więcej informacji, zobacz [szybkie akcje](../ide/quick-actions.md).

   ![Zygzaki](../ide/media/vs2017_squiggle.png)

- [Hierarchii wywołań](../ide/reference/call-hierarchy.md) można otworzyć okna w menu kontekstowym edytora tekstu do wyświetlenia wywołania, które są wywoływane przez metody metody pod karetką (punktu wstawiania).

   ![Okno hierarchii wywołań](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) umożliwia znalezienie odwołań i zmiany kodu, połączonych usterek, elementy robocze, przeglądy kodu i testów jednostkowych wszystko to bez opuszczania edytora.

   ![CodeLens](../ide/media/codelensoverview.png)

- [Wgląd do definicji](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) okno zawiera wbudowany definicję metody lub typu, bez konieczności opuszczania bieżący kontekst.

   ![Wgląd do definicji](../ide/media/VSIDE_peek_definition.png)

- [Przejdź do definicji](../ide/go-to-and-peek-definition.md) menu kontekstowego przejście bezpośrednio do miejsca, w którym zdefiniowana jest funkcji lub obiektu. Inne polecenia nawigacji dostępne są także klikając prawym przyciskiem myszy w edytorze.

   ![Przejdź do definicji](../ide/media/VSIDE_go_to_definition.png)

## <a name="create-a-program"></a>Utwórz program

Załóżmy zajrzyj dostęp i utworzyć nowe, proste program.

1. Otwórz program Visual Studio. W menu, wybierz **pliku** > **nowy** > **projektu**.

  ![Plik > Nowy projekt na pasku menu](../ide/media/VSIDE_Tour_NewProject1.png)

1. **Nowy projekt** okno dialogowe zawiera kilka projektu *szablony*. Szablon zawiera podstawowe pliki i ustawienia wymagane dla typu danego projektu. Wybierz **.NET Core** kategorię w obszarze **Visual C#**, a następnie wybierz pozycję **aplikacji konsoli (.NET Core)** szablonu. W **nazwa** polu tekstowym **HelloWorld**, a następnie wybierz **OK** przycisku.

  ![Szablon aplikacji .NET core](../ide/media/overview-new-project-dialog.png)

   Program Visual Studio tworzy projekt. Jest prostą aplikację "Hello World", który wywołuje <xref:System.Console.WriteLine?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli.

  > [!NOTE]
  > Jeśli nie widzisz **.NET Core** kategorii, musisz zainstalować **aplikacji dla wielu platform .NET Core** obciążenia. Aby to zrobić, wybierz **Otwórz Instalator programu Visual Studio** łącza w lewym dolnym rogu **nowy projekt** okna dialogowego. Po **Instalator programu Visual Studio** zostanie otwarta, przewiń w dół i wybierz **aplikacji dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

   Wkrótce powinny zostać wyświetlone informacje podobne do następujących:

   ![Visual Studio IDE](../ide/media/overview-ide-console-app.png)

   Kod C# dla aplikacji jest wyświetlany w oknie Edytor zajmuje większość miejsca. Zwróć uwagę, czy tekst jest automatycznie kolorowane w celu wskazania różnych aspektów kodu, na przykład słowa kluczowe i typy. Ponadto małych, pionowych linii kreskowanej w kodzie określają, które nawiasów klamrowych siebie, a później zlokalizować kod pomocy numery wierszy. Można wybrać znaków minus małe, opakowany można zwijać i rozwijać kodu. Ten kod zwijania funkcji umożliwia ukrywanie kodu, który nie jest konieczne, pomagając zminimalizować bałaganu na ekranie.

   Pliki projektu są wyświetlane po prawej stronie w oknie o nazwie **Eksploratora rozwiązań**.

  ![Visual Studio IDE z polami czerwony](../ide/media/overview-ide-console-app-red-boxes.png)

  Brak dostępnych innych menu i okien narzędzi, ale Przyjrzyjmy teraz.

1. Teraz uruchomić aplikację. Można to zrobić, wybierając **uruchomić bez debugowania** z **debugowania** menu na pasku menu. Można również nacisnąć **Ctrl**+**F5**.

  ![Debuguj > Uruchom bez debugowania menu](../ide/media/overview-start-without-debugging.png)

  Visual Studio tworzy aplikację, a komunikat zostanie otwarte okno konsoli **Hello World!**. Masz teraz uruchomionej aplikacji.

  ![Okno konsoli](../ide/media/overview-console-window.png)

1. Aby zamknąć okno konsoli, naciśnij dowolny klawisz na klawiaturze.

1. Dodajmy dodatkowy kod w aplikacji. Dodaj następujący kod C# przed wierszem informacją `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ten kod wyświetla **co to jest nazwa?** w oknie konsoli, a następnie czeka, aż użytkownik wprowadza tekst następuje **Enter** klucza.

1. Zmień wiersz informacją `Console.WriteLine("Hello World!");` poniższy kod:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Ponownie uruchom aplikację wybierając **debugowania** > **uruchomić bez debugowania** lub naciskając klawisz **Ctrl**+**F5**.

   Visual Studio odtwarza aplikacji i otwiera i wyświetla monit o podanie nazwy okna konsoli.

1. Wprowadź nazwę w oknie konsoli i naciśnij klawisz **Enter**.

   ![Dane wejściowe z okna konsoli](media/overview-console-input.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać uruchomiony program.

## <a name="use-refactoring-and-intellisense"></a>Refaktoryzacja i IntelliSense

Przyjrzyjmy się na kilka sposobów który [refaktoryzacji](refactoring-in-visual-studio.md) i [IntelliSense](using-intellisense.md) może pomóc w bardziej wydajne kodem.

Po pierwsze Zmieńmy nazwy `name` zmienną:

1. Kliknij dwukrotnie `name` zmiennej, aby go wybrać.

1. Wpisz nową nazwę zmiennej, `username`.

   Należy zauważyć, że szare pole wokół zmienną i żarówka pojawia się na marginesie.

1. Wybierz ikonę żarówki, aby wyświetlić dostępne [szybkie akcje](quick-actions.md). Wybierz **Zmień nazwę 'name' do 'username'**.

   ![Zmień nazwę akcji w programie Visual Studio](media/rename-quick-action.png)

   Zmienna jest zmieniana na projekt, który w tym przypadku jest tylko dwóch miejscach.

   ![Animowany plik gif przedstawiający Refaktoryzacja zmiany nazwy w programie Visual Studio](media/rename-refactoring.gif)

1. Teraz Spójrzmy na IntelliSense. Poniżej wiersza z informacją, `Console.WriteLine($"\nHello {username}!");`, typ **DateTime teraz = DateTime.**.

   W polu są wyświetlane z członkami <xref:System.DateTime> klasy. Ponadto opis aktualnie wybrany element członkowski wyświetla w osobnym oknie.

   ![Elementy członkowskie listy IntelliSense w Visual Studio](media/intellisense-list-members.png)

1. Wybierz element członkowski o nazwie **teraz**, właściwość klasy, która jest dwukrotne kliknięcie go lub naciskając klawisz **kartę**. Zakończenie wiersza kodu, dodając średnikiem **;**.

1. Poniżej wpisz lub skopiuj następujące wiersze kodu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> różni się nieco do <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , nie powoduje dodania terminator wiersza, po wydrukowaniu. Oznacza to, że dalej fragment tekstu, który jest wysyłany do danych wyjściowych będzie drukować na tej samej linii. W kodzie, aby wyświetlić ich opis można umieść kursor nad każdą z tych metod.

1. Następnie użyjemy refaktoryzacji ponownie nawiązać nieco bardziej zwięzły kod. Polecenie Zmienna `now` w wierszu `DateTime now = DateTime.Now;`.

   Zauważ, że małego ikona śrubokręt wyświetlony na marginesie, w tym wierszu.

1. Kliknij ikonę śrubokręt, aby zobaczyć, jakie sugestie dotyczące programu Visual Studio jest dostępny. W takim przypadku jest widoczny [wbudowanej zmiennej tymczasowej](reference/inline-temporary-variable.md) refaktoryzacji do usunięcia wiersza kodu bez zmiany zachowania ogólną:

   ![Wbudowany tymczasowej zmiennej Refaktoryzacja w programie Visual Studio](media/inline-temporary-variable-refactoring.png)

1. Kliknij przycisk **wbudowanej zmiennej tymczasowej** do zrefaktoryzuj kod.

1. Uruchom program ponownie, naciskając klawisz **Ctrl**+**F5**. Dane wyjściowe wygląda następująco:

   ![Okno konsoli z danych wyjściowych programu](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>Debugowanie kodu

Podczas pisania kodu, należy ją uruchomić i przetestować go dla usterki. System debugowania programu Visual Studio umożliwia kroków opisanych w jedną instrukcję kodu w czasie i sprawdzić zmiennych w trakcie pracy. Można ustawić punktów przerwania, które są osiągane tylko, gdy określony warunek jest spełniony. Można monitorować wartości zmiennych jako uruchamia kod i inne.

Teraz Ustaw punkt przerwania, aby wyświetlić wartość `username` zmiennej, gdy program jest "w locie".

1. Znajdź wiersz kodu, który wskazuje, że wskazuje `Console.WriteLine($"\nHello {username}!");`. Aby ustawić punkt przerwania w tym wierszu kodu, oznacza to, aby zatrzymać wykonywanie w tym wierszu program kliknij na lewym marginesie edytora. Można również kliknij w dowolnym miejscu w wierszu kodu, a następnie naciśnij klawisz **F9**.

   Na lewym marginesie pojawi się czerwone kółko i kod jest wyróżnione kolorem czerwonym.

   ![Punkt przerwania w wierszu kodu w programie Visual Studio](media/breakpoint.png)

1. Rozpocznij debugowanie, wybierając **debugowania** > **Rozpocznij debugowanie** lub naciskając klawisz **F5**.

1. Gdy w oknie konsoli zostanie wyświetlony i prosi o nazwę, wpisz ją w i naciśnij klawisz **Enter**.

   Należy zauważyć, że nastąpi powrót do edytora kodu programu Visual Studio i wiersz kodu z punkt przerwania jest wyróżnione kolorem żółtym. Oznacza to, jest następnym wierszu kodu, który program zostanie wykonany.

1. Umieść kursor myszy nad `username` zmiennej, aby wyświetlić jego wartość. Alternatywnie możesz kliknąć prawym przyciskiem myszy na `username` i wybierz **Dodaj wyrażenie kontrolne** można dodać zmienną **czujki** okna, umożliwia również wyświetlenie jej wartość.

   ![Wartość zmiennej podczas debugowania w programie Visual Studio](media/debugging-variable-value.png)

1. Aby umożliwić program monitów, naciśnij klawisz **F5** ponownie.

Aby uzyskać więcej informacji na temat debugowania w programie Visual Studio, zobacz [debugera samouczek funkcji](../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Dostosowywanie programu Visual Studio

Można spersonalizować IDE, łącznie ze zmianą domyślny motyw kolorów. Aby zmienić **ciemny** motywu:

1. Na pasku menu wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego.

1. Na **środowiska** > **ogólne** Strona opcji, zmień **motywu kolorów** zaznaczenie, aby **ciemny**, a następnie wybierz pozycję **OK**.

   Motyw kolorów dla całego zmiany IDE **ciemny**.

   ![VS ciemnego motywu](media/quickstart-personalize-dark-theme.png)

Aby dowiedzieć się więcej o innych metodach można spersonalizować IDE, zobacz [spersonalizować Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="learn-more"></a>Dowiedz się więcej

Czy chcesz utworzyć aplikację dla systemu Android lub iOS telefonu? Jak gry 3D, lub włączoną obsługę chmury aplikacji? Aby dowiedzieć się więcej na temat tych i innych funkcji programu Visual Studio, zobacz [funkcje programu Visual Studio 2017](../ide/advanced-feature-overview.md).

Jeśli po prostu chcesz rozpocząć teraz kodowania, wybierz jeden z szybkiego startu tematów spisu treści, takich jak [tworzenie pierwszej aplikacji sieci web platformy ASP.NET Core](quickstart-aspnet-core.md).

Możesz również sprawdzić limit bezpłatnych kursów Visual Studio na [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033).

## <a name="see-also"></a>Zobacz także

* [Więcej funkcji programu Visual Studio](../ide/advanced-feature-overview.md)
* [VisualStudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
* [Blog programu Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Pobieranie programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)