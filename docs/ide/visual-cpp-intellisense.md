---
title: Visual C++ IntelliSense | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: bfebee340a880cdef1b8721bd5f57e3be5db8e47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-intellisense"></a>IntelliSense dla programu Visual C++

IntelliSense dla języka C++ jest dostępna dla autonomicznych pliki także jak w przypadku plików, które są częścią projektu C++. W projektach między platformami niektóre funkcje IntelliSense są dostępne w .cpp i .c pliki w projekcie udostępnionym kodu, nawet jeśli znajdują się w kontekście systemu Android lub iOS.

## <a name="intellisense-features-in-c"></a>Funkcje IntelliSense w języku C++

IntelliSense jest nazwa nadana zestaw funkcji, które kodowania wygodniejsze. Ponieważ różne osoby mają różne poznać co to jest wygodne, można niemal wszystkie funkcje IntelliSense włączone lub wyłączone w **opcje** okna dialogowego, w obszarze **Edytor tekstu**  >  **C/C++** > **zaawansowane**. **Opcje** okno dialogowe jest dostępne z **narzędzia** menu na pasku menu.

![Okno dialogowe opcji narzędzi](../ide/media/sintellisensecpptoolsoptions.PNG)

Elementy menu i skróty klawiaturowe pokazano na poniższej ilustracji umożliwia dostęp do funkcji IntelliSense.

![IntelliSense menu](../ide/media/vs2015_cpp_intellisense_menu.png)

### <a name="statement-completion-and-member-list"></a>Listy uzupełniania i element członkowski — instrukcja

Po ponownym uruchomieniu, wpisując słowa kluczowego, typu, funkcji, nazwa zmiennej lub innego elementu programu rozpoznającego przez kompilator, edytor oferuje dokończyć słowo.

Listę ikon i ich znaczenie, zobacz [Widok klas i przeglądarka obiektów ― ikony](../ide/class-view-and-object-browser-icons.md).

![Visual C&#43; &#43; okna całe słowo](../ide/media/vs2015_cpp_complete_word.png "vs2015_cpp_complete_word")

Lista elementów członkowskich jest wywoływana po raz pierwszy pokazywane są tylko elementy członkowskie, które są dostępne dla bieżącego kontekstu. Jeśli naciśniesz **Ctrl**+**J** po, który zawiera wszystkie elementy członkowskie niezależnie od dostępności. Jeśli wywołanie raz trzeci go jeszcze większą listę elementów programu jest wyświetlany. Można wyłączyć listy członków w **opcje** okna dialogowego, w obszarze **Edytor tekstu** > **C/C++** > **ogólne**  >  **Automatyczna lista członków**.

![Visual C&#43;&#43; Member List](../ide/media/vs2015_cpp_list_members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Parametr pomocy

Po wpisaniu nawiasu otwierającego wywołanie funkcji lub nawias w deklaracji zmiennej szablonu klasy Edytor pokazuje małe okno z typami parametrów dla każdego przeciążenia funkcji lub konstruktora. Parametr "bieżący"&mdash;na podstawie lokalizacji kursora&mdash;jest pogrubiony. Można wyłączyć informacje o parametrach w **opcje** okna dialogowego, w obszarze **Edytor tekstu** > **C/C++** > **Ogólne**  >  **Informacje o parametrach**.

![Visual C&#43;&#43; Parameter Help](../ide/media/vs_2015_cpp_param_help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Szybkie informacje

Po umieszczeniu kursora myszy na zmienną małych okno jest wyświetlane w tekście, który zawiera informacje o typie i nagłówek, w którym jest zdefiniowany typ. Aktywuj wywołanie funkcji, aby wyświetlić podpisu funkcji. Można wyłączyć szybkie informacje w **opcje** okna dialogowego, w obszarze **Edytor tekstu** > **C/C++** > **zaawansowane**  >  **Automatyczna szybka podpowiedź**.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

### <a name="error-squiggles"></a>Zygzaki sygnalizujące błędy

Zygzaki pod elementem programu (zmiennej, słowo kluczowe, nawias klamrowy, wpisz nazwę i tak dalej) wywołać uwagę błąd lub potencjalnych błędów w kodzie. Zielony wężyk pojawia się podczas pisania deklaracja przekazująca dalej w celu odnotowania, konieczność zapisania implementacji. Purpurowa wężyk w projekcie udostępnionym jest wyświetlany błąd w kodzie, który nie jest obecnie aktywny, na przykład podczas pracy w kontekście systemu Windows, ale coś wprowadź, która byłaby błędu w kontekście systemu Android. Czerwona falista wskazuje błąd kompilatora lub ostrzeżenie w aktywnej kod, który należy rozwiązać.

![Visual C&#43; &#43; zygzaki sygnalizujące błędy](../ide/media/vs2015_cpp_error_quiggles.png "vs2015_cpp_error_quiggles")

### <a name="code-colorization-and-fonts"></a>Kolorowanie kodu i czcionek

Można zmienić domyślny kolorów i czcionek w **opcje** okna dialogowego, w obszarze **środowiska** > **czcionki i kolory**. Można zmienić czcionki dla wielu interfejsu użytkownika systemu windows w tym miejscu nie tylko edytora. Ustawienia, które są specyficzne dla języka C++ rozpoczynać się od "C++"; inne ustawienia są dla wszystkich języków.

### <a name="cross-platform-intellisense"></a>IntelliSense i platform

W projekcie udostępnionym kodu niektóre funkcje IntelliSense, takie jak zygzaki są dostępne, nawet wtedy, gdy użytkownik pracuje w kontekście systemu Android. Jeśli piszesz niektórych kod, który może spowodować błąd w projekcie jest nieaktywny, pozostanie zygzaki funkcji IntelliSense, ale znajdują się w innym kolorze niż zygzaki błędów w bieżącym kontekście.

Oto OpenGLES aplikacji, która jest skonfigurowana dla kompilacji dla systemów Android i iOS. Na ilustracji przedstawiono udostępnionego kodu edytowany. W pierwszym obrazu systemu Android jest aktywnym projektem:

![Projekt systemu Android jest aktywnym projektem. ] (../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")

Należy zauważyć, że:

- #Else gałęzi w wierszu 8 będzie szary, aby wskazać regionu nieaktywnych, ponieważ __ANDROID\_ \_ jest zdefiniowany dla systemu android.

- Zmienna pozdrowienia w wierszu 11 został zainicjowany z identyfikatorem HELLO, mającej wężyk purpurowy. Jest tak, ponieważ nie identyfikatora HELLO nie została zdefiniowana w projekcie aktualnie nieaktywne w systemie iOS. Gdy w systemie Android czy skompilować projekt wiersza 11, nie będzie w systemie iOS. Ponieważ jest to udostępniony kod, który nie jest należy zmienić nawet kompiluje w aktualnie aktywnej konfiguracji.

- W wierszu 12 znajduje się czerwona falista na podstawie identyfikatora BYE; Ten identyfikator nie jest zdefiniowany w obecnie zaznaczonej aktywnego projektu.

Teraz Zmień aktywnego projektu iOS.StaticLibrary i zwróć uwagę, jak zmienić zygzaki.

![iOS został wybrany jako aktywnego projektu. ] (../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

Należy zauważyć, że:

- Gałęzi #ifdef w wierszu 6 będzie szary, aby wskazać regionu nieaktywnych, ponieważ __ANDROID\_ \_ nie jest zdefiniowany dla projektu iOS.

- Zmienna pozdrowienia w wierszu 11 został zainicjowany z identyfikatorem HELLO, który ma teraz czerwona falista. Jest tak, ponieważ nie identyfikatora HELLO nie została zdefiniowana w projekcie iOS aktualnie aktywny.

- Wiersz 12 ma purpurowa wężyk na podstawie identyfikatora BYE; Ten identyfikator nie jest zdefiniowany w aktualnie nieaktywne Android.NativeActivity projektu.

### <a name="intellisense-for-stand-alone-files"></a>IntelliSense dla plików autonomicznych

Po otwarciu pojedynczego pliku poza żadnego projektu nadal otrzymywać IntelliSense. Można włączyć lub wyłączyć określonej funkcji IntelliSense w **opcje** okna dialogowego, w obszarze **Edytor tekstu** > **C/C++**  >  **Zaawansowane**. Aby skonfigurować IntelliSense dla pojedynczych plików, które nie są częścią projektu, należy wyszukać **IntelliSense i przeglądanie dla plików poza projektami** sekcji.

![Visual C&#43; &#43; intellisense pojedynczy plik](../ide/media/vs2015_cpp_single_file_intellisense.png "vs2015_cpp_single_file_intellisense")

Domyślnie IntelliSense używane tylko standardowe obejmują pojedynczy plik katalogów można znaleźć plików nagłówka. Aby dodać dodatkowe katalogi, otwórz menu skrótów w węźle rozwiązania i Dodaj katalog na **debugowania kodu źródłowego** listy, jak przedstawiono na poniższej ilustracji:

![Dodawanie ścieżki do pliku nagłówka. ] (../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")

## <a name="see-also"></a>Zobacz także

[Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)