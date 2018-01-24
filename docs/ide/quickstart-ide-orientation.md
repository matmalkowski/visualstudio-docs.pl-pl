---
title: "Samouczek środowiska IDE programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a74d123d8cb0055f01619bae25b9a1bda54b35f4
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Szybki Start: Pierwsze spojrzenie na środowiska IDE programu Visual Studio

W to 5 – 10 min wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) firma Microsoft będzie przewodnik niektóre z okien, menu i inne funkcje interfejsu użytkownika.

## <a name="start-page"></a>Strona początkowa

W pierwszej kolejności zostanie wyświetlony po uruchomieniu programu Visual Studio jest najprawdopodobniej strony początkowej. Strona początkowa został zaprojektowany jako "koncentrator" w celu znalezienia polecenia i szybciej niepotrzebne pliki projektu. **Ostatnie** sekcja wyświetla projektów i foldery pracuje ostatnio. W obszarze **nowy projekt**, można kliknąć łącze, aby wyświetlić okno dialogowe nowego projektu lub w obszarze **Otwórz**, możesz otworzyć istniejącego projektu lub katalogu z kodem. Po prawej stronie jest źródło danych najnowsze developer.

![Strona początkowa VS](media/quickstart-IDE-start-page.png)

Jeśli zamkniesz — strona początkowa i chcesz ponownie wyświetlony, możesz uruchomić go z **pliku** menu.

![menu Plik](media/quickstart-IDE-file-menu-large.png)

Aby kontynuować zapoznawanie IDE, Utwórzmy nowy projekt.

1. Na **— strona początkowa**, w polu wyszukiwania w obszarze **nowy projekt**, wprowadź `console` Aby filtrować listę typów projektów. Wybierz opcję C# lub VB. **konsoli aplikacji (.NET Framework)**. (Można również jeśli C++, Javascript lub innych deweloperów języka, możesz zająć się tworzenie projektu na jednym z tych języków. Interfejs użytkownika, które firma Microsoft będzie sprawdzane jest podobnych dla wszystkich języków).

1. W **nowy projekt** okno dialogowe pola, zaakceptuj domyślną nazwę projektu i wybierz **OK**.

   Projekt zostanie utworzony i plik o nazwie **Program.cs** lub **Program.vb** otworzy się w **edytor** okna. Edytor zawiera zawartość plików i jest, gdzie należy wykonać większość pracy kodowania w programie Visual Studio.

## <a name="solution-explorer"></a>Eksplorator rozwiązań

Eksplorator rozwiązań zawiera graficzną reprezentację hierarchii plików i folderów w projekcie, rozwiązania lub katalogu z kodem. Można wybrać hierarchię i przejdź do pliku w Eksploratorze rozwiązań.

![Eksplorator rozwiązań](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

Na pasku menu u góry IDE grupy poleceń w kategorie. Na przykład **projektu** menu zawiera polecenia związanych z projektem pracy. Na **narzędzia** menu IDE można dostosować, wybierając **opcje**, lub Dodaj funkcje do instalacji, wybierając **Pobierz narzędzia i funkcje...** .

![Pasek menu](media/quickstart-IDE-menu-bar.png)

Teraz Otwórz okno Lista błędów, wybierając **widoku** menu, a następnie **listy błędów**.

## <a name="error-list"></a>Lista błędów

Na liście błędów wyświetlana błędy, ostrzeżenia i komunikaty dotyczące bieżącego stanu kodu. Jeśli wystąpiły błędy (na przykład Literówka składni) w pliku, lub w dowolnym miejscu w projekcie, będą wyświetlane w tym miejscu.

![Lista błędów](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Okno wyniku

Pokazuje okno danych wyjściowych output wiadomości z kompilacji i kontroli źródła.

Utworzymy projekt, aby wyświetlić niektóre rejestrowania danych wyjściowych. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**. W oknie danych wyjściowych automatycznie uzyskuje fokus i wyświetli komunikat pomyślnego utworzenia kompilacji.

![Okno wyniku](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>Szybkie uruchamianie

Pole Szybkie uruchamianie jest szybki i łatwy sposób pretty dużo niczego w środowisku IDE. Można wprowadzić tekst powiązany co chcesz zrobić, a jego opisano listę opcji, które odnoszą się do tekstu. Załóżmy na przykład, że chcemy zwiększyć poziom szczegółowości danych wyjściowych kompilacji do wyświetlenia rejestrowania informacje dodatkowe o tym, co dokładnie tworzenie zadań:

1. Wprowadź `verbosity` do **Szybkie uruchamianie** polu, a następnie wybierz pozycję **projektów i rozwiązań -> Kompilowanie i uruchamianie** w obszarze **opcje** kategorii.

   ![Pole szybkiego uruchamiania](media/quickstart-IDE-quick-launch.png)

   **Opcje** zostanie otwarte okno dialogowe do **skompilować i uruchomić** strona Opcje.

1. W obszarze **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild**, wybierz **normalny**, a następnie kliknij przycisk **OK**.

1. Obecnie firma Microsoft będzie ponownie skompilować projekt prawym przyciskiem myszy na **ConsoleApp1** projektu w **Eksploratora rozwiązań**i wybierając polecenie **odbudować** z menu kontekstowego.

   Teraz w oknie danych wyjściowych zawiera pełniejsze rejestrowanie w procesie kompilacji w tym pliki, które zostały skopiowane where.

## <a name="send-feedback-menu"></a>Wyślij opinię menu

Należy napotykasz problemy podczas korzystania z programu Visual Studio, lub jeśli masz sugestie dotyczące ulepszenia produktu, możesz użyć **Prześlij opinię** menu w górnej części środowiska IDE obok pola Szybkie uruchamianie.

![Wyślij opinię menu](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Następne kroki

Analizujemy zostały tylko niektóre funkcje programu Visual Studio IDE, aby korzystały z interfejsem użytkownika. Do dalszego zbadania:

- Przejdź do sekcji Ogólne elementy interfejsu użytkownika w dokumentacji wersji programu VS, przejdzie bardziej szczegółowo omówiono systemu windows, takich jak [listy błędów](../ide/reference/error-list-window.md), [okno danych wyjściowych](../ide/reference/output-window.md), [okna właściwości](../ide/reference/properties-window.md), i [opcje — Okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md)

- Więcej informacji na temat Przewodnik IDE, a nawet dabble debugowania, w [Omówienie środowiska IDE programu Visual Studio](../ide/visual-studio-ide.md)

## <a name="see-also"></a>Zobacz także

[Szybki Start: Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)  
[Szybki Start: Kodowania w edytorze](../ide/quickstart-editor.md)  
[Szybki Start: Projekty i rozwiązania](../ide/quickstart-projects-solutions.md)