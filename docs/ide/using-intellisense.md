---
title: IntelliSense programu Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48aa6cea8deec13bdf5dd43f83528daf5492e3d0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="using-intellisense-in-visual-studio"></a>Korzystanie z IntelliSense w Visual Studio

Technologia IntelliSense jest ogólnym terminem dla wielu funkcji: elementów członkowskich listy, informacji o parametrach, szybkich informacji i uzupełniania słów. Te funkcje pozwalają dowiedzieć się więcej o kodzie, którego używasz, śledzić wpisywane parametry i dodawać wywołania do właściwości i metod za pomocą zaledwie kilku naciśnięć klawiszy.

Wiele aspektów IntelliSense jest specyficzne dla języków. Aby uzyskać więcej informacji o funkcji IntelliSense dla różnych języków, zobacz tematy wymienione w [Zobacz też](#see-also) sekcji.

## <a name="list-members"></a>Lista składników

Zostanie wyświetlona lista elementów prawidłową z typu (lub przestrzeni nazw), po wpisaniu znaku wyzwalacza (na przykład okres (`.`) w kodzie zarządzanym lub `::` w języku C++). Jeśli będziesz kontynuować, wpisując znaków, lista jest filtrowana do uwzględnienia tylko do elementów członkowskich, które zaczynają się od tych znaków lub których na początku *żadnych* programu word w nazwa rozpoczyna się od tych znaków. IntelliSense wykonuje także "camelcase" dopasowania, więc można po prostu wpisz pierwszą literę każdego wyrazu formatu — z uwzględnieniem wielkości liter w nazwie elementu członkowskiego, aby zobaczyć dopasowań.

Po wybraniu elementu, będzie mogło do kodu, naciskając klawisz **kartę** lub wpisując spacją. Jeśli wybierzesz element i wpiszesz kropkę, element pojawia się, a po nim kropka, co wywołuje kolejną listę elementów członkowskich. Po wybraniu elementu, ale przed jego wstawieniem, otrzymasz szybkie informacje na jego temat.

Na liście składowych ikona po lewej stronie reprezentuje typ składowej, taki jak przestrzeń nazw, klasa, funkcja lub zmienna. Listę ikony, zobacz [Widok klas i przeglądarka obiektów ― ikony](../ide/class-view-and-object-browser-icons.md). Listy może być dość długo, więc możesz nacisnąć przycisk **PgUp** i **PgDn** do Przenieś w górę lub w dół na liście.

![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015_intellisense.png "vs2015_Intellisense")

Można wywołać **członków listy** funkcji, ręcznie wpisując **CTRL** + **J**, wybierając pozycję **Edytuj**  >  **IntelliSense** > **członków listy**, lub wybierając **członków listy** przycisk na pasku narzędzi edytora. Gdy jest wywoływana w pustym wierszu lub poza rozpoznawalnym zasięgiem, na liście wyświetlane są symbole w globalnej przestrzeni nazw.

Aby wyłączyć członków listy domyślnie (tak aby nie jest wyświetlana, jeśli wywołania), przejdź do **narzędzia** > **opcje** > **wszystkie języki**i usuń zaznaczenie **automatyczna lista członków**. Jeśli chcesz wyłączyć członków listy tylko dla określonego języka, przejdź do **ogólne** ustawień dla tego języka.

Można również przejść do trybu sugestii, w którym tylko wpisany tekst jest umieszczony w kodzie. Na przykład możesz wprowadzić identyfikator, który nie jest na liście i naciśnij klawisz **kartę**, zakończenia działania trybu zapis spowodowałoby zastąpienie identyfikatora typu. Aby przełączyć tryb uzupełniania i tryb sugestii, naciśnij klawisz **Ctrl** + **Alt** + **spacja**, lub wybierz **Edytuj**  >  **IntelliSense** > **Przełącz tryb uzupełniania**.

## <a name="parameter-info"></a>Informacje o parametrach

Informacje o parametrach zawierają informacje na temat liczby, nazw i typów parametrów wymaganych przez metodę, parametr typu ogólnego atrybutu (w języku C#) lub szablon (w języku C++).

Parametr pogrubiony wskazuje następny parametr, który jest wymagany podczas wprowadzania funkcji. Dla przeciążonych funkcji klawisze strzałek w górę i w dół umożliwiają wyświetlenie informacji o alternatywnych parametrach przeciążeń funkcji.

![Informacje o parametrach](../ide/media/vs2015_param_info.png "VS2015_param_Info")

Gdy opisujesz funkcje i parametry za pomocą komentarzy dokumentacji XML, komentarze będą wyświetlane jako informacje o parametrach. Aby uzyskać więcej informacji, zobacz [dostarczanie komentarze w kodzie XML](../ide/supplying-xml-code-comments.md).

Informacje o parametrach można wywołać ręcznie, wybierając **Edytuj** > **IntelliSense** > **informacje o parametrach**, naciskając **Ctrl**   +  **Shift** + **miejsca**, lub wybierając **informacje o parametrach** przycisk na pasku narzędzi edytora.

## <a name="quick-info"></a>Szybkie informacje

Szybkie informacje wyświetlają pełną deklarację dla każdego identyfikatora w kodzie.

![Visual Studio Quick Info](../ide/media/vs2015_quick_info.png "VS2015_Quick_info")

Po wybraniu elementu członkowskiego **członków listy** polu Szybkie informacje jest także wyświetlany.

![Informacje o parametrach w C&#35; pliku kodu](../ide/media/vs2015_paraminfo.png "VS2015_ParamInfo")

Szybkie informacje można wywołać ręcznie, wybierając **Edytuj** > **IntelliSense** > **szybka podpowiedź**, naciskając **Ctrl**  +  **I**, lub wybierając **szybka podpowiedź** przycisk na pasku narzędzi edytora.

Jeżeli funkcja jest przeciążona, mechanizm IntelliSense może nie wyświetlać informacji dla wszystkich postaci przeciążenia.

Można wyłączyć szybka podpowiedź dla kodu C++ przechodząc do **narzędzia** > **opcje** > **Edytor tekstu** > **C / C++** > **zaawansowane**, a ustawienie **automatyczna szybka podpowiedź** do `false`.

## <a name="complete-word"></a>Dokończ wyraz

Całe słowo kończy reszty zmiennej, polecenia lub nazwę funkcji po wprowadzeniu wystarczającej liczby znaków, aby usunąć niejednoznaczność terminu. Można wywołać całe słowo, wybierając **Edytuj** > **IntelliSense** > **całe słowo**, naciskając **Ctrl** + **Miejsca**, lub wybierając **całe słowo** przycisk na pasku narzędzi edytora.

## <a name="intellisense-options"></a>Opcje IntelliSense

Opcje IntelliSense są domyślnie włączone. Aby je wyłączyć, należy wybrać **narzędzia** > **opcje** > **Edytor tekstu** i usuń zaznaczenie **informacje o parametrach**lub **automatyczna lista członków** Jeśli nie chcesz, aby funkcja listy członków.

## <a name="troubleshooting-intellisense"></a>Rozwiązywanie problemów z technologią IntelliSense

W niektórych przypadkach opcje IntelliSense mogą nie działać zgodnie z oczekiwaniami.

**Gdy kursor znajduje się poniżej błąd kodu.** Nie można używać funkcji IntelliSense, jeśli funkcja niekompletne lub inny błąd nie istnieje w kodzie powyżej kursora, ponieważ nie można zanalizować elementy kodu IntelliSense. Można naprawić ten problem, zakomentowując odpowiedni kod.

**Kursor znajduje się w komentarz do kodu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w komentarzu w pliku źródłowym.

**Kursor jest literałem ciągu.** Nie można użyć funkcji IntelliSense, gdy kursor znajduje się w cudzysłowie literału ciągu, jak w poniższym przykładzie:

```cpp
MessageBox( hWnd, "String literal|")
```

**Opcje automatycznego są wyłączone.** Domyślnie IntelliSense działa automatycznie, ale można ją wyłączyć. Nawet jeśli automatyczne uzupełnianie instrukcji jest wyłączone, można wywołać funkcję mechanizmu IntelliSense.

## <a name="see-also"></a>Zobacz także

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [Funkcja IntelliSense dla języka JavaScript](../ide/javascript-intellisense.md)
- [Pisanie i refaktoryzacja kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Stosowanie komentarzy kodu XML](../ide/supplying-xml-code-comments.md)