---
title: Pisanie kodu w edytorze kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 09/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4f26fcfb6b12266dd980fb8c38075e1937fcc022
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="write-code-in-the-code-editor"></a>Pisanie kodu w edytorze kodu
Edytor programu Visual Studio udostępnia wiele funkcji, które ułatwiają zapisu i zarządzanie kodu i tekstu. Można zwijać i rozwijać różnych bloków kodu za pomocą obramowanie. Użytkownik może dowiedzieć się więcej o kod za pomocą funkcji IntelliSense, **przeglądarki obiektów**i hierarchii wywołań. Możesz znaleźć kodu za pomocą funkcji, takich jak **przejdź do**, **przejdź do definicji**, i **Znajdź wszystkie odwołania**. Możesz wstawić bloków kodu z fragmentów kodu i istnieje możliwość wygenerowania kodu za pomocą funkcji, takich jak **Generowanie z użycia**. Jeśli nie znasz edytorze programu Visual Studio przed, zobacz [edycji kodu](https://www.visualstudio.com/features/ide-vs) szybki przegląd.  

 Kodu można wyświetlić na kilka różnych sposobów. Domyślnie **Eksploratora rozwiązań** zawiera kod uporządkowane według plików. Możesz kliknąć **widoku klasy** u dołu okna, aby wyświetlić kod uporządkowane według klasy.

 Można wyszukiwania i zamieniania tekstu w jednej lub wielu plików. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md). Wyrażenia regularne służy do znajdowania i zamieniania tekstu. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 Języki Visual Studio oferują różne zestawy funkcji, a w niektórych przypadkach funkcje działają inaczej w różnych językach. Wiele z tych różnic są określone w opisach funkcji, ale uzyskać więcej informacji można wyświetlić sekcje na określonych języków Visual Studio.  

> [!IMPORTANT]
>  Program Visual Studio i ustawienia, którego używasz może mieć wpływ na funkcje w środowisku IDE. Mogą różnić się od opisanych w tym temacie.  

## <a name="editor-features"></a>Funkcje edycji  

|||  
|-|-|  
|Kolorowanie składni|Niektóre elementy składni plików kodu i znaczników mają kolor inaczej, aby odróżnić je. Na przykład słowa kluczowe (takich jak `using` w języku C# i `Imports` w języku Visual Basic) są jednego koloru, ale typy (takich jak `Console` i `Uri`) są w innym kolorze. Inne elementy składni są również pokolorowane, takie jak literały ciągów i komentarze. C++ używa koloru do rozróżnienia typów, wyliczenia i makra, między innymi tokenów.<br /><br /> Widać domyślny kolor dla każdego typu i można zmienić kolor elementów składni w [czcionki i kolory, środowisko, opcje — Okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), który można otworzyć z **narzędzia** menu.|  
|Błąd i ostrzeżenie znaków|Dodaj kod i Skompiluj rozwiązanie, mogą pojawić się faliste podkreślenie () innym kolorze (nazywane zygzaki) i (b) żarówki znajdujących się w kodzie. Czerwony zygzaki oznaczenia błędy składni, niebieski oznacza błędy kompilatora zielony oznacza ostrzeżenia i purpurowy oznacza inne typy błędów. [Żarówki](../ide/perform-quick-actions-with-light-bulbs.md) Sugeruj poprawki dotyczące problemów i ułatwić poprawki.<br /><br /> Widać domyślny kolor dla każdego błędu i ostrzeżenia wężyk w **narzędzia/Opcje/środowiska/czcionki i kolory** okno dialogowe. Wyszukaj **błąd składniowy**, **błąd kompilatora**, **ostrzeżenie**, i **inny błąd**.|  
|Parowanie nawiasów klamrowych|Gdy punkt wstawiania znajduje się na otwierający nawias klamrowy w pliku kodu, są wyróżnione go i zamykający nawias klamrowy. Ta funkcja zapewnia natychmiast uzyskuje opinie zagubione lub brak nawiasów klamrowych. Można włączyć parowanie nawiasów klamrowych lub Wyłącz z **automatyczne wyróżnianie ogranicznika** ustawienie (**narzędzia/Opcje/tekstu edytor**). Można zmienić kolor wyróżnienia w **czcionki i kolory** ustawienie (**narzędzia/Opcje/środowiska**). Wyszukaj **nawias klamrowy dopasowywania (Wyróżnij)** lub **nawias klamrowy dopasowywania (prostokąt)**.|  
|Struktura wizualizatora|Przerywana łączone pasujących nawiasów klamrowych w plikach kodu, ułatwiając Zobacz otwierający i zamykający nawias klamrowy pary. To może pomóc w znalezieniu kodu w Twojej codebase szybciej. Można włączyć te wiersze lub wyłączyć z **Pokaż wytyczne struktury** w **wyświetlania** sekcji **narzędzia/Opcje/tekstu Edytor/ogólne** strony.|
|Numery wiersza|Numery wiersza mogą być wyświetlane na lewym marginesie okna kodu. Nie są wyświetlane domyślnie. Można włączyć tę opcję **edytora tekstów wszystkie języki** ustawień (**narzędzia/Opcje/Editor/All w językach**). Można wyświetlić numery wierszy dla poszczególnych języków programowania, zmieniając ustawienia w tych językach (**narzędzia / Opcje / Edytor tekstu /\<języka >**). W przypadku numerów wierszy do drukowania, musisz wybrać **zawierają numery wierszy** w **drukowanie** okno dialogowe.|  
|Śledzenie zmian|Kolor lewy margines umożliwia śledzenie zmian wprowadzonych w pliku. Zmiany wprowadzone przez użytkownika, ponieważ plik został otwarty, ale nie zapisano są wskazywane przez żółty pasek na lewym marginesie (nazywane margines zaznaczania). Po zapisaniu zmian (ale przed zamknięciem pliku), pasku włącza zielony. Jeśli po zapisaniu pliku możesz cofnąć zmianę, pasku włącza pomarańczowy. Aby wyłączyć i Włącz tę funkcję, zmień **śledzenia zmian** opcji **Edytor tekstu** ustawienia (**narzędzia/Opcje/tekstu edytor**).|  
|Wybieranie kodu i tekstu|Można zaznaczyć tekst w trybie Standardowy strumień ciągłej lub w trybie pole, wybierz prostokątny część tekstu, zamiast zestawu wierszy. Aby dokonać wyboru w trybie pole, trzymając naciśnięty klawisz ALT przeciągnij mysz nad wyborem (lub naciśnij klawisze ALT + SHIFT + \<Strzałka >). Zaznaczenie zawiera wszystkie znaki w prostokącie zdefiniowane przez znak pierwszy i ostatni znak w zaznaczeniu. Dodaje się niczego wpisana lub wklejane obszaru, w tym samym punkcie w każdym wierszu.|  
|Powiększenie|W dowolnym oknie kodu można powiększanie lub pomniejszanie naciskając klawisz CTRL i przenoszenie kółko przewijania myszy (lub CTRL + SHIFT +. Aby zwiększyć i CTRL + SHIFT +, aby zmniejszyć). Można ustawić wartość procentową powiększenia określonych umożliwia także pole powiększenia w lewym dolnym rogu okna kodu. Funkcja powiększenia nie działa w systemie windows narzędzia.|  
|Wirtualna spacja|Domyślnie wierszy w Visual Studio edytory zakończona po ostatnim znaku, aby strzałka w prawo na końcu wiersza przenosi kursor na początek następnego wiersza. W niektórych innych edytory wiersza nie kończy się po ostatnim znaku i umieść kursor dowolne miejsce w wierszu. Można włączyć wirtualną przestrzeń w edytorze w **narzędzia/Opcje/Editor/All w językach** ustawienia. Należy pamiętać, że można włączyć jedną **wirtualną przestrzeń** lub **zawijanie**, ale nie oba.|  
|Drukowanie|Można użyć opcji w **drukowanie** okno dialogowe, aby uwzględnić numery wierszy lub ukrywanie zwinięte regionów kodu podczas drukowania pliku. W **ustawienia strony** okno dialogowe, również można wydrukować pełną ścieżkę i nazwę pliku, wybierając **nagłówek strony**.<br /><br /> Opcje drukowania w kolorze można ustawić w **narzędzia/Opcje/środowiska/czcionki i kolory** okno dialogowe. Wybierz **drukarki** w **Pokaż ustawienia dla** listy, aby dostosować drukowanie kolorów. Można określić różne kolory do drukowania pliku niż do edycji plik.|  
|Globalne cofanie i powtórz|**Cofnij ostatnią akcję globalną** i **wykonaj ponownie ostatnią akcję globalną** polecenia w **Edytuj** menu cofnąć ani ponowić Akcje globalne, które mają wpływ na wiele plików. Globalne akcje obejmują, zmiana nazwy klasy lub przestrzeni nazw, wykonywanie operacji Znajdź i Zamień rozwiązanie refaktoryzacji bazy danych lub innych działań, które zmieniają wiele plików. Można zastosować globalnego cofania i ponawiania poleceń do akcji w bieżącej sesji programu Visual Studio, nawet po zamknięciu rozwiązania, w którym akcja została zastosowana.|  

## <a name="advanced-editing-features"></a>Zaawansowane funkcje edytowania  
 Liczba zaawansowanych funkcji można znaleźć w **edycji/zaawansowane** podmenu. Nie wszystkie te funkcje są dostępne dla wszystkich typów plików kodu.  

|||  
|-|-|  
|Format dokumentu|Ustawia odpowiednie wcięcia wierszy kodu i przenosi nawiasy klamrowe do osobnych wierszy w dokumencie.|  
|Wybieranie formatu|Ustawia odpowiednie wcięcia wierszy kodu i przenosi nawiasy klamrowe do osobnych wierszy w zaznaczeniu.|  
|Tabify — formatowanie wybranych wierszy|Spacje wiodące na znaki tabulacji, gdzie jest to odpowiednie zmiany.|  
|Untabify wybranych wierszy|Zmiany wiodące tabulatory na spacje. Jeśli chcesz przekonwertować wszystkie spacje w pliku na kartach (lub wszystkie tabulatory na spacje), możesz użyć `Edit.ConvertSpacesToTabs` i `Edit.ConvertTabsToSpaces` poleceń. Te polecenia nie są wyświetlane w menu programu Visual Studio, ale może być wywoływany ze okna Szybki dostęp lub okna poleceń.|  
|Upewnij się wielkie litery|Zmienia wszystkie znaki w zaznaczeniu na wielkie litery, lub jeśli nie ma żadnego zaznaczenia, zmieni się znak punkt wstawiania na wielkie litery.|  
|Zmień litery na małe|Zmienia wszystkie znaki w zaznaczeniu na małe litery, lub jeśli nie ma żadnego zaznaczenia, zmienia znak punkt wstawiania na małe litery.|  
|Przesuń wybrane wiersze w górę|Przenosi wybrany wiersz w górę o jeden wiersz. Skrótu: Klawisze ALT + Strzałka w górę.|
|Przesuń wybrane wiersze w dół|Przenosi wybrany wiersz w dół o jeden wiersz. Skrótu: Klawisze ALT + Strzałka w dół.|
|Sprawdź poprawność dokumentu|Weryfikuje plików kodu w języku JScript.|  
|Usuń biały znak w poziomie|Usuwa tabulatory lub spacje na koniec bieżącego wiersza.|  
|Widok biały znak|Wyświetla spacje jako zgłoszono kropek i karty jako strzałki. Koniec pliku jest wyświetlana jako prostokątne symbolu. Jeśli **narzędzia/Opcje/tekstu Editor/All języków/Word zawijania/Pokaż symbole widoczne dla zawijania** jest zaznaczone, tego symbolu jest również wyświetlany.|  
|Zawijanie tekstu|Powoduje, że wszystkie wiersze w dokumencie mają być wyświetlane w oknie kodu. Można włączyć zawijanie i Włącz ustawienia edytora tekstu wszystkie języki (**narzędzia/Opcje/językach Editor/All**).|  
|Zaznaczanie komentarzy|Dodaje komentarz znaków do zaznaczenia lub bieżącego wiersza.|  
|Usuń znaczniki komentarza zaznaczenia|Usuwa znaki komentarza z zaznaczenie lub bieżącego wiersza.|  
|Zwiększ wcięcie wiersza|Dodaje kartę (lub równoważne spacji) do wybranych wierszy lub bieżącego wiersza.|  
|Zmniejsza wcięcie linii|Usuwa kartę (lub równoważne spacji) z wybranych wierszy lub bieżącego wiersza.|  
|Wybierz Tag|W dokumencie, który zawiera tagów (na przykład, XML lub HTML) wybiera tagu.|  
|Wybierz zawartość tagów|W dokumencie, który zawiera tagów (na przykład, XML lub HTML) wybiera zawartości.|  

## <a name="navigate-and-find-code"></a>Nawigację i znalezienie kodu  
Można przenosić w edytorze kodu kilka różnych sposobów, łącznie z nawigowania wstecz i przekazuje do poprzednich punktów wstawiania, wyświetlanie definicji typu lub elementu członkowskiego i przejście do określonej metody za pomocą paska nawigacji. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie](navigating-code.md).  

## <a name="finding-references-in-your-code-base"></a>Trwa znajdowanie odwołań w kodzie  
Aby dowiedzieć się, gdy elementy określonego kodu są przywoływane w całym baza kodu, można użyć **Znajdź wszystkie odwołania** polecenia. Ponadto po kliknięciu typu lub elementu członkowskiego, **podświetlanie odwołań** funkcji automatycznie prezentuje wszystkie odwołania do tego typu lub elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).  

## <a name="customize-the-editor"></a>Dostosowywanie edytora  
Można udostępnić ustawienia programu Visual Studio z innego projektanta, mieć ustawienia są zgodne z normą, lub przywrócić ustawienia domyślne programu Visual Studio za pomocą **Kreator importowania i eksportowania ustawień** na  **Narzędzia** menu. W **Kreator importowania i eksportowania ustawień**, możesz zmienić wybrane ustawienia ogólne lub język i ustawienia specyficzne dla projektu.

Aby zdefiniowane klawisze dostępu nowe lub zmienione istniejących klawisze dostępu, przejdź do **narzędzia**, **opcje**, **środowiska**, **klawiatury**. Aby uzyskać więcej informacji na temat klawisze dostępu, zobacz [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

Aby uzyskać więcej informacji dotyczących dostosowywania edytora, zobacz [dopasowywanie edytora](../ide/customizing-the-editor.md). Aby informacji na temat opcji edytora specyficznych dla języka, zobacz [przy użyciu środowiska programowania Visual Studio w języku C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) i [opcje, Edytor tekstu, JavaScript, formatowanie](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
