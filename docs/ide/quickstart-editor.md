---
title: Wprowadzenie do edycji w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: b74acd0b7711f7b11965bdde6fd2e152ee340c85
ms.sourcegitcommit: 1aa9282b1f0bc2795df3264cbd1e331cc44c23f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2017
---
# <a name="quickstart-coding-in-the-editor"></a>Szybki Start: kodowania w edytorze

W tym wprowadzenie 10-minutowych do edytora dodamy kod do pliku, aby wyglądały na kilka sposobów, że program Visual Studio sprawia, że pisania, nawigowania i kod ułatwia zrozumienie.

## <a name="create-a-new-code-file"></a>Utwórz nowy plik kodu

Rozpocznij od tworzenia nowego pliku i dodanie do niej kodu. Należy zauważyć, że nie ma do utworzenia projektu do uzyskania niektóre korzyści, które oferuje edytora.

1. Otwórz program Visual Studio i z **pliku** menu na pasku menu wybierz **nowy** > **pliku...** .

1. W **nowy plik** okna dialogowego, w obszarze **ogólne** kategorii, wybierz **Visual C# klasy**, a następnie wybierz pozycję **Otwórz**.

   Nowy plik zostanie otwarty w edytorze z szkieletową klasy C#.

## <a name="using-code-snippets"></a>Korzystania z wstawek kodu

Program Visual Studio udostępnia wstawki kodu przydatne, które umożliwia szybkie i łatwe generowanie najczęściej używane bloki kodu. [Wstawki kodu](../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym C#, Visual Basic i C++. Dodajmy C# `void Main` fragment do naszej pliku.

1. Umieść kursor poniżej zamykającym `Class1` konstruktora, a następnie wprowadź znaki `svm`.

   Zobacz okno dialogowe IntelliSense są wyświetlane informacje o `svm` fragment kodu.

   ![Fragment kodu IntelliSense](media/quickstart-intellisense-snippet.png)

1. Naciśnij klawisz **kartę** dwa razy, aby wstawić fragment kodu.

   Zostanie wyświetlony `static void Main()` podpis metody zostaną dodane do pliku. `Main()` Metoda jest punkt wejścia dla aplikacji C#.

Wstawki kodu dostępne różnią się w różnych językach. Można przyjrzeć się wstawki kodu dostępne dla języka programowania, wybierając **Edytuj**, **IntelliSense**, **fragment Insert...** , a następnie wybierając folderze danego języka. Język C# listy wygląda następująco:

![Lista fragment kodu C#](media/quickstart-code-snippet-list.png)

Lista zawiera wstawki kodu programu do tworzenia klas, konstruktora, `Console.WriteLine()`, `for` pętle, `if` i `switch` instrukcje i inne.

## <a name="commenting-out-code"></a>Dodawanie komentarza do kodu

Pasek narzędzi udostępnia szereg przycisków większej wydajności jako użytkownik kodu. Na przykład można Przełącz tryb uzupełniania IntelliSense, zwiększyć lub zmniejszyć wcięcie, ustaw zakładki lub komentarz kodu. W tej sekcji, firma Microsoft będzie komentarz dotyczący niektórych kodu, który nie chcemy, aby skompilować.

![Edytor paska narzędzi](media/quickstart-editor-toolbar.png)

1. Wklej następujący kod do `Main()` treści metody.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    }

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Firma Microsoft nie używa `morewords` zmiennej, ale może jej użyć później, nie chcemy go usunąć. Zamiast tego teraz komentarz te wiersze. Wybierz całą definicję `morewords` do zamknięcia średnikami, a następnie wybierz pozycję **komentarz wybranych wierszy** przycisku paska narzędzi lub naciśnij klawisz **Ctrl** + **K**, **Ctrl**+**C**.

   ![Komentarz przycisku](media/quickstart-comment-out.png)

   C# znaki `//` zostaną dodane na początku każdego wybranego wiersza, aby przekształcić w komentarz kod.

## <a name="collapsing-code-blocks"></a>Zwijanie bloków kodu

Nie chcemy zobaczyć pustego konstruktora dla `Class1` wygenerowany, tak aby uniknąć przeładowania naszych widoku kodu, umożliwia zwinąć go. Wybierz małe pole szarego znakiem minus wewnątrz na marginesie pierwszego wiersza konstruktora. Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor dowolne miejsce w Konstruktorze kod i naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M** .

![Tworzenie konspektu przycisk Zwiń](media/quickstart-collapse.png)

Zwija blok kodu do tylko pierwszego wiersza, a następnie wielokropkiem (`...`). Aby rozwinąć blok kodu ponownie, kliknij pole szarego tego samego ma teraz znak plus, lub naciśnij przycisk **Ctrl**+**M**, **Ctrl**+**M**  ponownie. Ta funkcja jest nazywana [zwijania](../ide/outlining.md) i jest szczególnie przydatne, gdy jest zwijanie długi metod lub klas całego.

## <a name="viewing-symbol-definitions"></a>Wyświetlanie definicji symbolu

Edytor programu Visual Studio ułatwia Sprawdź definicję typu, metody itd. Jednym ze sposobów jest przejdź do pliku, który zawiera definicję, na przykład, wybierając **przejdź do definicji** dowolnym odwołuje się do symbolu. Nawet szybszy sposób, który nie Przenieś fokus od pliku pracy jest użycie [definicji wglądu](../ide/go-to-and-peek-definition.md#peek-definition). Załóżmy wgląd w definicji `string`.

1. Kliknij prawym przyciskiem myszy na dowolne wystąpienie `string` i wybierz polecenie **definicji wglądu** z menu zawartości&mdash;lub naciśnij klawisz **Alt**+**F12**.

   Zostanie wyświetlone okno podręczne z definicją `String` klasy. Można przewijać w oknie podręcznym lub nawet wglądu w definicji innego typu niż peeked kodu.

   ![Okno definicji wglądu](media/quickstart-peek-definition.png)

1. Zamknij okno przybywającej definicji, wybierając małe pola z symbol "x" u góry po prawej tego okna.

## <a name="using-intellisense-to-complete-words"></a>Korzystanie z IntelliSense do ukończenia słowa

[IntelliSense](../ide/using-intellisense.md) jest nieoceniony zasobów, gdy jest kodowania. Go można wyświetlić informacji o dostępnych elementach członkowskich typu lub Szczegóły parametru dla innego przeciążenia metody. Umożliwia także IntelliSense do ukończenia słowa po wpisaniu wystarczającej liczby znaków celu odróżnienia go. Dodajmy wiersza kodu w celu wydrukowania uporządkowanej ciągów w oknie konsoli.

1. Poniżej `query` zmiennej, wpisz następujący kod:

   ```csharp
   foreach (string str in qu
   ```

   Zobacz IntelliSense opisano **szybka podpowiedź** o `query` symbolu.

   ![Zakończenie word IntelliSense](media/quickstart-intellisense-completion-list.png)

1. Aby wstawić rest Word `query` za pomocą funkcji "Całe słowo" w funkcji IntelliSense, naciśnij klawisz **kartę**.

1. Zakończ poza blok kodu, aby wyglądały jak w poniższym kodzie. Można nawet Ćwiczenie korzystania z wstawek kodu ponownie, wprowadzając `cw` , a następnie naciskając klawisz **kartę** dwa razy, aby wygenerować `Console.WriteLine` kodu.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>Refaktoryzacja nazwę

Nikt nie pobiera prawo kod po raz pierwszy, a drugi czynności, które możesz chcieć zmienić nazwę zmiennej lub metody. Spróbujmy Visual Studio [Refaktoryzacja](../ide/refactoring-code-generation-quick-actions.md#refactoring) funkcji, aby zmienić nazwę `_words` zmienną `words`.

1. Umieść kursor nad definicji `words` zmienną i wybierz polecenie **zmienić...**  z kliknij prawym przyciskiem myszy lub menu kontekstowego lub naciśnij klawisz **Ctrl**+**R**, **Ctrl**+**R**.

   Okno podręczne **zmienić** u góry zostanie wyświetlone okno dialogowe prawo do edytora.

1. Wprowadź odpowiednią nazwę `words`. Należy zauważyć, że odwołanie do `words` automatycznie zostanie zmieniona w zapytaniu. Przed naciśnięciem przycisku **Enter**, wybierz pozycję **uwzględnić komentarze** checkbox w **zmienić** okno podręczne.

   ![Zmień nazwę — Okno dialogowe](media/quickstart-rename.png)

1. Naciśnij klawisz **wprowadź**.

   Oba wystąpienia `words` została zmieniona, a także odwołanie do `words` w komentarz do kodu.

## <a name="next-steps"></a>Następne kroki

Udało Ci się ukończyć tego przewodnika Szybki Start dla edytorze programu Visual Studio! Następnie spróbuj się z innymi poradniki Szybki Start dla programu Visual Studio IDE poszukać na więcej sposobów [nawigowanie po kodzie](../ide/navigating-code.md), lub linków, aby uzyskać więcej informacji o funkcjach, analizujemy. W przeciwnym razie wszystkiego kodowania!

## <a name="see-also"></a>Zobacz także

[Szybki Start: Pierwsze spojrzenie na środowiska IDE programu Visual Studio](../ide/quickstart-ide-orientation.md)  
[Szybki Start: personalizowanie środowiska IDE programu Visual Studio i edytora](../ide/quickstart-personalize-the-ide.md)  
[Wstawki kodu](../ide/code-snippets.md)  
[Obramowanie](../ide/outlining.md)  
[Polecenia Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)  
[Refaktoryzacja](../ide/refactoring-code-generation-quick-actions.md#refactoring)  
[Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)  