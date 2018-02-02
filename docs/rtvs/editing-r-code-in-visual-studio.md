---
title: "Edycja kodu za pomocą narzędzia R dla programu Visual Studio | Dokumentacja firmy Microsoft"
description: "Program Visual Studio oferuje dostosowane środowisko edytowania dla R przy zachowaniu wszystkie funkcje i możliwości, aby korzystać z rozszerzeń."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 2650d366cd174b9964142b76048cda6e4b3c3497
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="editing-r-code-in-visual-studio"></a>Edytowanie kodu języka R w programie Visual Studio

R narzędzi dla programu Visual Studio (RTVS) dostosowanie programu Visual Studio edytowania specjalnie z myślą o R przy zachowaniu wszystkie funkcje i możliwości, aby korzystać z rozszerzeń. (Na przykład, jeśli wolisz powiązań klucza VIM, można zainstalować bezpłatną [rozszerzenia VsVim](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329) z galerii programu Visual Studio.)

Oprócz funkcji w tym artykule, zobacz też [IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [wstawki kodu](code-snippets-for-r.md), i [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>wyróżnianie składni

Oprócz kolorowania różnych części kodu, na przykład ciągi, komentarze i słów kluczowych, RTVS wyróżnia i umożliwia łącza w komentarzach:

![Kolorowania dla kodu języka R](media/editing-syntax-colors.png)

Aby dostosować czcionki i kolory niektórych wyróżnienia, wybierz opcję **Narzędzia > Opcje** polecenia, przejdź do **środowiska > czcionki i kolory**, następnie zmiany ustawień dla elementów powiązanych R  **Wyświetl elementy:** pola:

![Czcionki i kolory dla kodu języka R](media/editing-syntax-colors-options.png)

Visual Studio również podkreśla błędów składni w edytorze:

![Błąd składniowy wyróżnianie w kodzie języka R](media/editing-syntax-error.png)

Aby zmienić to zachowanie, zobacz **Zaawansowane > Sprawdzanie składni** w obszarze [opcji edytora](#editor-options).

## <a name="editing-and-organizing-code"></a>Edytowanie i organizowanie kodu

Podczas pisania kodu RTVS możliwość automatycznego uzupełniania, zgodnie z opisem na [IntelliSense](r-intellisense.md) strony. Powoduje także, automatycznego formatowania, takie jak uzupełnianie nawiasy i nawiasy: 

![Animacja wbudowanego formatowania](media/editing-inline-formatting.gif)

Podczas wpisywania wywołania funkcji, które mają wiele parametrów, często chcesz wyrównać parametrów, aby ułatwić kod. RTVS pamięta wcięcie zestawu parametrów i automatycznie stosuje ten wcięcie dla kolejnych wierszy:

![Animacja automatyczne wcięcia](media/editing-auto-indentation.gif)

Aby zmienić to zachowanie, zobacz [opcji edytora](#editor-options) dla **karty** grupy.

Regiony zwijanej kodu pozwalają tymczasowo ukryć część kodu w edytorze. Visual Studio utworzy różnych regionach automatycznie, podobnie jak w przypadku instrukcji wiele wierszy, chyba że **Zaawansowane > Tworzenie konspektu > zwijania kodu** opcja ma wartość Off.

Można utworzyć obszaru własny, przestrzennego odpowiedni kod z komentarzami, których nazwa kończy `---`. Mały +/-kontrolki do lewej strony kodu pozwala następnie rozwijanie i zwijanie obszarów:

![Tworzenie zwijanej region z komentarzami](media/editing-collapsible-regions.gif)

Domyślnie program Visual Studio Wstawia spacje po naciśnięciu klawisza Tab. Można ponownie zmienić to zachowanie, zgodnie z opisem na [karty Opcje, Edytor tekstu,](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Nawigacja w kodzie

Nawigacja w kodzie umożliwia szybki dostęp do kodu źródłowego z programem R i jego bibliotek. Te funkcje zachować w przepływie pracy, a nie konieczności ręcznego wyszukiwania kodu.

**Przejdź do definicji** szybko przechodzi do definicji funkcji lub wyskakującej wbudowanego edytora mini odczytać kodu źródłowego funkcji biblioteki. Kliknij prawym przyciskiem myszy właśnie funkcja odsetek i wybierz **przejdź do definicji**, umieść kursor w funkcji i naciśnij klawisz F12.

To polecenie powoduje otwarcie nowego okna edytora kodu źródłowego dla funkcji. Kursor jest znajdują się na początku definicji funkcji.

**Wybieranie definicji**, wywoływane z menu kliknij prawym przyciskiem myszy lub Alt + F12, wstawia region tylko do odczytu, którą można przewijać zawierające kod źródłowy funkcji poniżej wywołania funkcji:

![Animacja dla definicji wglądu](media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>Wysyłanie do okna interaktywnego kodu

Wielu deweloperów, takich jak do pisania kodu w edytorze, a następnie wyślij kod do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md) natychmiastowego testowania (znanej także jako odczytu oceny-drukowania-pętla lub REPL). Naciśnięcie klawiszy Ctrl + Enter w edytorze R bieżącego wiersza kodu do okna interaktywnego, a następnie umieszcza kursor w następnym wierszu. Z klawiszy Ctrl + Enter następnie, można efektywnie przejrzeć kodu w edytorze.

Można również wybrać kodu i naciśnij klawisz Ctrl + Enter, aby zastosować całego wybieranie. Alternatywnie kliknij zaznaczenie prawym przyciskiem myszy i wybierz **Execute w Interactive**.

## <a name="formatting-code"></a>Formatowanie kodu

Automatyczne formatowanie programu Visual Studio zachowuje kod, który zapisu, a także kod, który możesz wkleić do edytora sformatowane jako zestaw przez swoje preferencje. Należy również wybrać opcję, kliknij prawym przyciskiem myszy, a następnie wybierz **Wybieranie formatu** (Ctrl + K, F), aby zastosować tych preferencji. Na przykład, jeśli masz definicji funkcji wszystko w jednym wierszu:

```R
f<-function  (a){  return(a + 1) }
```

Formatowania czyści go jako:

```R
f <- function(a) { return(a + 1) }
```

Do ponownego formatowania pliku całego kodu, wybierz **Edytuj > Zaawansowane > dokumentu w formacie** (Ctrl + E, D).

Automatyczne formatowanie jest operacją oddzielne, którą można cofnąć. Na przykład, jeśli kod wkleić do edytora i formatowanie ma to zastosowanie, wybranie opcji **Edytuj > cofnąć** lub naciskając klawisz Ctrl + Z raz odwraca formatowanie; drugi cofania odwraca Wklej sam.

Opcje formatowania (w tym wyłączenie opcji formatowania) są ustawiane za pomocą **Narzędzia > Opcje** na **Edytor tekstu > R > Zaawansowane** kartę. Można przejść bezpośrednio do tej strony za pomocą **R Narzędzia > Opcje edytora...**  poleceń lub przez kliknięcie prawym przyciskiem myszy w edytorze i wybraniu **opcje formatowania...** . Zobacz [opcji edytora](#editor-options) sekcji, aby uzyskać szczegółowe informacje.

## <a name="inserting-roxygen-comments"></a>Wstawianie Roxygen komentarzy

RTVS przewiduje generowania skrótu [Roxygen](http://roxygen.org/) komentarzy przy użyciu nazwy parametrów funkcji. Po prostu wpisz `###` na pusty wiersz powyżej definicji funkcji:

![Animacja wstawiania komentarz Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opcje edytora

Do ustawiania opcji edytora specyficznych **Narzędzia > Opcje** polecenia, przechodząc do **Edytor tekstu > R**, lub użyj polecenia skrót **R Narzędzia > Opcje edytora...** .

Opcje na **ogólne**, **paski przewijania**, i **karty** karty nie są specyficzne dla języka R, ale są raczej ogólne ustawienia programu Visual Studio, dostępne dla wszystkich języków, ale zastosowane na Podstawa dla języka. Aby uzyskać więcej informacji zobacz następujące artykuły:

- [Opcje, Edytor tekstu, wszystkie języki](../ide/reference/options-text-editor-all-languages.md)
- [Śledzenie można kodu dostosowując pasek przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opcje, Edytor tekstu, karty](../ide/reference/options-text-editor-all-languages-tabs.md)

Opcje na **R > Zaawansowane** są specyficzne dla RTVS:

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
| IntelliSense | Zatwierdź na klawisz Enter | Off | Zatwierdza wyboru automatycznego uzupełniania po naciśnięciu klawisza Enter. |
| | Zatwierdź klucza miejsca | Off | Zatwierdza wyboru automatycznego uzupełniania po naciśnięciu miejsca.|
| | Listy uzupełniania w pierwszym znakiem | On | Zawiera listę uzupełniania pierwszy typów znaków. Kiedy, zostanie wyświetlona lista uzupełniania z **Edytuj > IntelliSense > członków listy** (Ctrl + J). |
| | Listy uzupełniania w klawisza Tab | Off | Wywołuje listy uzupełniania wpisywanie co najmniej jeden znak i naciskając klawisz Tab. |
| | Niezgodne typy częściowo nazwy argumentów | Off | Podczas wpisywania nazwy argumentów w wywołaniu funkcji, podpisu pomocy zawiera opis argumentu, który najlepiej odpowiada. |
| Okno interaktywne | Sprawdzanie składni w konsoli języka R | Off | Stosuje składni sprawdzanie w oknie interaktywnym. Sprawdzanie składni może nie działać poprawnie w instrukcjach wiele wierszy. | 
| Tworzenie konspektu | Zwijanie kodu | On | Automatycznie tworzy zwijanej regionów obszarów, takich jak wiele wierszy instrukcji. |
| Sprawdzanie składni | Pokaż błędy składniowe | On | Umożliwia automatyczne składni Sprawdzanie kodu. |
