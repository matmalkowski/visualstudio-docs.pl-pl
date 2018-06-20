---
title: Edytowanie kodu języka R
description: Program Visual Studio oferuje dostosowane środowisko edytowania dla R przy zachowaniu wszystkie funkcje i możliwości, aby korzystać z rozszerzeń.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 9eef75c505cb3ed41e24f99e08468512e424884a
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238363"
---
# <a name="edit-r-code-in-visual-studio"></a>Edytuj kod języka R w programie Visual Studio

R narzędzi dla programu Visual Studio (RTVS) dostosowanie programu Visual Studio edytowania specjalnie z myślą o R przy zachowaniu wszystkie funkcje i możliwości, aby korzystać z rozszerzeń. (Na przykład, jeśli wolisz powiązań klucza VIM, można zainstalować bezpłatną [rozszerzenia VsVim](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329) z galerii programu Visual Studio.)

Oprócz funkcji w tym artykule, zobacz też [IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [wstawki kodu](code-snippets-for-r.md), i [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>wyróżnianie składni

Oprócz kolorowania różnych części kodu, na przykład ciągi, komentarze i słów kluczowych, RTVS wyróżnia i umożliwia łącza w komentarzach:

![Kolorowania dla kodu języka R](media/editing-syntax-colors.png)

Aby dostosować czcionki i kolory niektórych wyróżnienia, wybierz opcję **narzędzia** > **opcje** polecenia, przejdź do **środowiska**  >  **Czcionki i kolory**, następnie zmiany ustawień dla elementów powiązanych R **wyświetlania elementów** pola:

![Czcionki i kolory dla kodu języka R](media/editing-syntax-colors-options.png)

Visual Studio również podkreśla błędów składni w edytorze:

![Błąd składniowy wyróżnianie w kodzie języka R](media/editing-syntax-error.png)

Aby zmienić to zachowanie, zobacz **zaawansowane** > **sprawdzanie składni** w obszarze [opcji edytora](#editor-options).

## <a name="edit-and-organize-code"></a>Edytuj i organizowanie kodu

Podczas pisania kodu RTVS możliwość automatycznego uzupełniania, zgodnie z opisem na [IntelliSense](r-intellisense.md) strony. Powoduje także, automatycznego formatowania, takie jak uzupełnianie nawiasy i nawiasy: 

![Animacja wbudowanego formatowania](media/editing-inline-formatting.gif)

Podczas wpisywania wywołania funkcji, które mają wiele parametrów, często chcesz wyrównać parametrów, aby ułatwić kod. RTVS pamięta wcięcie zestawu parametrów i automatycznie stosuje ten wcięcie dla kolejnych wierszy:

![Animacja automatyczne wcięcia](media/editing-auto-indentation.gif)

Aby zmienić to zachowanie, zobacz [opcji edytora](#editor-options) dla **karty** grupy.

Regiony zwijanej kodu pozwalają tymczasowo ukryć część kodu w edytorze. Visual Studio utworzy różnych regionach automatycznie, podobnie jak w przypadku instrukcji wiele wierszy, chyba że **zaawansowane** > **Tworzenie konspektu** > **zwijanie kodu**  opcja ma wartość Off.

Można utworzyć obszaru własny, przestrzennego odpowiedni kod z komentarzami, których nazwa kończy `---`. Mały +/-kontrolki do lewej strony kodu pozwala następnie rozwijanie i zwijanie obszarów:

![Tworzenie zwijanej region z komentarzami](media/editing-collapsible-regions.gif)

Domyślnie program Visual Studio Wstawia spacje po naciśnięciu **kartę** klucza. Można ponownie zmienić to zachowanie, zgodnie z opisem na [karty Opcje, Edytor tekstu,](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Nawigacja w kodzie

Nawigacja w kodzie umożliwia szybki dostęp do kodu źródłowego z programem R i jego bibliotek. Te funkcje zachować w przepływie pracy, a nie konieczności ręcznego wyszukiwania kodu.

**Przejdź do definicji** szybko przechodzi do definicji funkcji lub wyskakującej wbudowanego edytora mini odczytać kodu źródłowego funkcji biblioteki. Kliknij prawym przyciskiem myszy właśnie funkcja odsetek i wybierz **przejdź do definicji**, albo umieść kursor w funkcji i naciśnij klawisz **F12**.

To polecenie powoduje otwarcie nowego okna edytora kodu źródłowego dla funkcji. Kursor jest znajdują się na początku definicji funkcji.

**Podgląd definicji**, wywołana w menu kontekstowym lub **Alt**+**F12**, wstawia region tylko do odczytu, którą można przewijać zawierające kod źródłowy funkcji poniżej Wywołanie funkcji:

![Animacja dla definicji wglądu](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Wyślij kod na okno interaktywne

Wielu deweloperów, takich jak do pisania kodu w edytorze, a następnie wyślij kod do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md) natychmiastowego testowania (znanej także jako odczytu oceny-drukowania-pętla lub REPL). Naciśnięcie przycisku **Ctrl**+**Enter** w R Edytor bieżącego wiersza kodu do okna interaktywnego, a następnie umieszcza kursor w następnym wierszu. Z **Ctrl**+**Enter**, następnie, można efektywnie przejrzeć kodu w edytorze.

Możesz też wybrać kod i naciśnij klawisz **Ctrl**+**Enter** do zastosowania tego całego zaznaczenia. Alternatywnie kliknij zaznaczenie prawym przyciskiem myszy i wybierz **Execute w Interactive**.

## <a name="format-code"></a>Formatowanie kodu

Automatyczne formatowanie programu Visual Studio zachowuje kod, który zapisu, a także kod, który możesz wkleić do edytora sformatowane jako zestaw przez swoje preferencje. Należy również wybrać opcję, kliknij prawym przyciskiem myszy, a następnie wybierz **Wybieranie formatu** (**Ctrl**+**K**,**F**) do zastosowania tych Preferencje. Na przykład, jeśli masz definicji funkcji wszystko w jednym wierszu:

```R
f<-function  (a){  return(a + 1) }
```

Formatowania czyści go jako:

```R
f <- function(a) { return(a + 1) }
```

Do ponownego formatowania pliku całego kodu, wybierz **Edytuj** > **zaawansowane** > **dokumentu w formacie** (**Ctrl** + **E**,**D**).

Automatyczne formatowanie jest operacją oddzielne, którą można cofnąć. Na przykład, jeśli kod wkleić do edytora i formatowanie ma to zastosowanie, wybranie opcji **Edytuj** > **Cofnij** lub naciskając klawisz **Ctrl** + **Z** raz odwraca formatowanie; drugi **Cofnij** odwraca Wklej samej siebie.

Opcje formatowania (w tym wyłączenie opcji formatowania) są ustawiane za pomocą **narzędzia** > **opcje** na **Edytor tekstu**  >  **R** > **zaawansowane** kartę. Można przejść bezpośrednio do tej strony za pomocą **narzędzia R** > **opcji edytora** poleceń lub przez kliknięcie prawym przyciskiem myszy w edytorze i wybraniu **Opcjeformatowania**. Zobacz [opcji edytora](#editor-options) sekcji, aby uzyskać szczegółowe informacje.

## <a name="inserting-roxygen-comments"></a>Wstawianie Roxygen komentarzy

RTVS przewiduje generowania skrótu [Roxygen](http://roxygen.org/) komentarzy przy użyciu nazwy parametrów funkcji. Po prostu wpisz `###` na pusty wiersz powyżej definicji funkcji:

![Animacja wstawiania komentarz Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opcje edytora

Opcje edytora są ustawiane za pomocą **narzędzia** > **opcje** polecenia, przechodząc do **Edytor tekstu** > **R**, lub użyj polecenia skrót **narzędzia R** > **opcji edytora**.

Opcje na **ogólne**, **paski przewijania**, i **karty** karty nie są specyficzne dla języka R, ale są raczej ogólne ustawienia programu Visual Studio, dostępne dla wszystkich języków, ale zastosowane na Podstawa dla języka. Aby uzyskać więcej informacji zobacz następujące artykuły:

- [Opcje, Edytor tekstu, wszystkie języki](../ide/reference/options-text-editor-all-languages.md)
- [Śledzenie można kodu dostosowując pasek przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opcje, Edytor tekstu, karty](../ide/reference/options-text-editor-all-languages-tabs.md)

Opcje na **R** > **zaawansowane** są specyficzne dla RTVS:

| Grupa | Opcja | Domyślny | Opis |
| --- | --- | --- | --- |
| Formatowanie | Automatyczne formatowanie | On | Formatuje kodu podczas pisania. Nie wpływa na **Wybieranie formatu** lub **dokumentu w formacie** poleceń. |
| | Rozwinięte nawiasów klamrowych | Off | Umieszcza otwarty {w nowym wierszu. |
| | Format po wklejeniu | On | Stosuje formatowanie podczas wklejania. |
| | Format zakresu na} | On | Formaty zakresu po wpisaniu zamykającego}. |
| | Miejsca po przecinku | On | Umieszcza odstęp po przecinkach. |
| | Ilość miejsca po — słowo kluczowe | On | Umieszcza spację po słów kluczowych, takich jak `if`, `while`, i `repeat`. |
| | Odstęp przed { | On | Umieszcza spacji przed i otwieranie {. |
| | Spacje wokół = | On | Umieszcza spacje wokół znaku równości. |
| IntelliSense | Zatwierdź na klawisz Enter | Off | Zatwierdza wyboru automatycznego uzupełniania po **Enter** zostanie naciśnięty. |
| | Zatwierdź klucza miejsca | Off | Zatwierdza wyboru automatycznego uzupełniania po **miejsca** zostanie naciśnięty.|
| | Listy uzupełniania w pierwszym znakiem | On | Zawiera listę uzupełniania pierwszy typów znaków. Kiedy, zostanie wyświetlona lista uzupełniania z **Edytuj** > **IntelliSense** > **członków listy** (**Ctrl** + **J**). |
| | Listy uzupełniania w **kartę** klucza | Off | Wywołuje listy uzupełniania wpisując co najmniej jeden znak i naciskając klawisz **kartę**. |
| | Niezgodne typy częściowo nazwy argumentów | Off | Podczas wpisywania nazwy argumentów w wywołaniu funkcji, podpisu pomocy zawiera opis argumentu, który najlepiej odpowiada. |
| Okno interaktywne | Sprawdzanie składni w konsoli języka R | Off | Stosuje składni sprawdzanie w oknie interaktywnym. Sprawdzanie składni może nie działać poprawnie w instrukcjach wiele wierszy. | 
| Tworzenie konspektu | Zwijanie kodu | On | Automatycznie tworzy zwijanej regionów obszarów, takich jak wiele wierszy instrukcji. |
| Sprawdzanie składni | Pokaż błędy składniowe | On | Umożliwia automatyczne składni Sprawdzanie kodu. |
