---
title: Debugowanie kodu dla początkujących bezwzględne
description: Jeśli debugujesz po raz pierwszy, zapoznaj się z pomocą techniczną firmy kilka zasad, aby pomóc w debugowaniu aplikacji za pomocą programu Visual Studio
ms.custom: ''
ms.date: 06/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca01699b8dfef3b427579b839359953742a15758
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36304770"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Debugowanie dla początkujących bezwzględne

Dowiedz się bardzo podstawowe sposoby debugowania za pomocą debugera. Jeśli po raz pierwszy, próbujących przeprowadzić debugowania aplikacji są przygotowanie wypróbowanie debugowania narzędzia, takiego jak Visual Studio, następnie jesteś w odpowiednim miejscu. Gdy używasz debugera po raz pierwszy jest normalnym nadzieję (i oczekują) czy niezależnie od narzędzia debugowania używasz magicznie opisano wszystkie błędy w kodzie. Niestety nie jest to łatwe. Debugowanie jest zapamiętane umiejętności i czasochłonne i rozwiązaniem, aby dowiedzieć się, jak skutecznie debugowania. Więc przed możemy pokazuje sposób debugowania, firma Microsoft zapewniają pewne ogólne wskazówki i zasad.

Po pierwsze, może być przydatne do odpowiedzi na podstawowe pytania takie jak "Co to jest debugowanie?" i "Co to jest tryb debugowania?"

* *Debugowanie* jest proces usuwania błędów w kodzie. W kontekście debugowania narzędzia, takiego jak Visual Studio.

* *Tryb debugowania* oznacza z tą aplikacją (wykonywanie kodu) podczas debuger programu Visual Studio jest dołączony do aplikacji. W debugerze widać, czynności kod po uruchomieniu. Na przykład możesz sprawdzić aplikacji stanu (przyjrzeć zmienne), zobacz co funkcji pobierania noszą nazwę i prób znalezienia usterek. W dokumentów gdy chcemy, aby wprowadzić tryb debugowania, wystarczy zwykle powiedzieć "Debuger Start" lub "Uruchamianie aplikacji w debugerze".

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Wyjaśnienie problem pytając samodzielnie odpowiednie pytania

Ułatwia on wyjaśnienie uruchomionego na, przed podjęciem próby go rozwiązać problem. Oczekuje się, że możesz już wystąpił problem w kodzie, w przeciwnym razie nie można w tym miejscu chcesz dowiedzieć się, jak można debugować go! Dlatego przed rozpoczęciem debugowania, spróbuj odpowiedzieć sobie na kilka pytań.

* Oczekiwań swój kod, aby zrobić?

* Co się stało zamiast niego?

    Jeśli podczas uruchamiania aplikacji wystąpił błąd (wyjątku), które może być zdaje! Wyjątkiem jest nieoczekiwane zdarzenie napotkał podczas uruchamiania kodu, zazwyczaj błąd określonego rodzaju. [Pomocnika wyjątków](../debugger/debugger-feature-tour.md#exception) w programie Visual Studio umieszcza aplikacji w tryb debugowania, przejście do dokładnego miejsce w kodzie, gdzie wyjątek wystąpił i pozwala na komunikat o błędzie badać możliwe poprawki. (Ale przed należy zbadać dokończyć odczytu w tym artykule).

    Jeśli czegoś innego się stało, co to jest symptomem problem? Czy już podejrzewasz, którym wystąpił ten problem w kodzie? Na przykład jeśli kod wyświetla część tekstu, ale tekst jest niepoprawny, wiesz, że dane są uszkodzone albo określonego rodzaju błędów ma kod, który ustawić tekst wyświetlany. Aby rozwiązać problem, takich jak ta, najprawdopodobniej należy uruchomić aplikację w debugerze programu Visual Studio i przyjrzyj się zmiennych. (Ale najpierw należy kontynuować odczytu w tym artykule).

## <a name="examine-your-assumptions"></a>Sprawdź założeń

Wziąć pod uwagę przed badania usterki lub wystąpił błąd, założeń, które można spodziewać się pewnych wynik wprowadzone. Może to być długą listę, poniżej przedstawiono kilka przykładów założeń, które są łatwe do udostępniania, ale nie musi to być wartość true.

* Używasz prawo interfejsu API (oznacza to, prawego obiektu, funkcji, metody lub właściwości). Interfejs API, którego używasz może nie działać wydaje się, że istnieje. (Po należy zbadać wywołania interfejsu API w debugerze, naprawienie go może wymagać podróży dokumentacji w celu identyfikowania poprawne interfejsu API.)

* Poprawnie są przy użyciu interfejsu API. Może być używane po prawej interfejsu API, ale nie został użyty w sposób prawo.

* Kod nie ma żadnych błędów.

* Dokonano zmian w kodzie i założono, że jest związana z problem, który został wyświetlony.

* Wystąpił zmiany w środowisku (na przykład aktualizacji narzędzia lub biblioteki) i założono, że jest związana z problem, który został wyświetlony.

* Oczekiwano obiektu lub zmienna określonej wartości (lub typ wartości), ale nie.

* Zrozumienie tego kodu jest wystarczająco również do jego debugowania. Jest często bardziej trudne do debugowania kogoś innego elementu kodu. Jeśli nie jest kodu, jest to możliwe, należy poświęcić czas nauki kod jest przed debugowaniem jej skutecznie.

    > [!TIP]
    > Zacznij od czegoś małego i rozpoczynać się od kodu, który działa! Czasami łatwiej rozwiązać, zaczynając od małego fragmentu kodu, który demonstruje z podstawowym zadaniem próbujesz osiągnąć duży lub zbyt skomplikowany zestaw kodu (oznacza to, skopiuj przykładowy pracy). Następnie można zmodyfikować lub Dodaj kod przyrostowo, testowanie w każdym punkcie błędów.

Znając założeń może skrócić czas potrzebny do znalezienia problem w kodzie. Może również skrócić czas potrzebny do rozwiązania konkretnego problemu.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Krokowo kodu w tryb można znaleźć, gdzie wystąpił problem podczas debugowania

Jeśli nie otrzymasz wyjątek, użyj debugera, aby znaleźć dokładnego miejsce, w którym wystąpił problem (lub objaw usterki). Przed rozpoczęciem starań w celu znalezienia konkretnego regionu kodu, gdzie występuje ten problem, następnie ustaw [punktu przerwania](../debugger/using-breakpoints.md) gdzie zaczyna się kod. Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio należy zawiesić kodu uruchomionej, aby móc przeglądać wartości zmiennych, ani zachowanie pamięci lub czy jest pobieranie uruchamiana gałąź kodu. Można ustawić punktu przerwania, klikając na lewym marginesie obok wiersza kodu.

![Ustaw punkt przerwania](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

Po ustawieniu punkt przerwania, uruchom debuger (naciśnij klawisz **F5** lub **Rozpocznij debugowanie** przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") w Debugowania narzędzi) i wstrzyma aplikacji, gdy wykonuje kodu, w którym można ustawić punktu przerwania (jeśli go nie wstrzymanie, kod nie wykonaj). Następnie użyj [krok polecenia](../debugger/navigating-through-code-with-the-debugger.md) takich jak **F10** i **F11** wyprzedzeniem debugera i uruchomić kod. Podczas debugowania kodu aplikacji wykonuje jak zwykle. Podczas uruchamiania aplikacji w debugerze, Wyszukaj ten problem, który został zidentyfikowany.

> [!NOTE]
> Jeśli jest trudne do zidentyfikowania region kodu, gdzie występuje ten problem, ustaw punkt przerwania w kodzie, który jest uruchamiany przed wystąpieniem problemu, a następnie użyj polecenia krok, aż pojawi się problem manifestu. Można również użyć [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) logowania komunikaty **dane wyjściowe** okna. Dzięki patrzeć komunikaty zarejestrowane (i wiadomości, które nie zostały jeszcze zarejestrowane po raz pierwszy!), często można odizolować region kodu z tym problemem. Może być konieczne Powtórz ten proces kilka razy, aby zawęzić jej. Jeśli ten problem występuje gdzieś w pętli, który powtarza się wielokrotnie (i w związku z tym jest trudna do odtworzenia), [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) może pomóc.

## <a name="when-you-find-the-region-of-code-with-the-problem-use-the-debugger-to-investigate"></a>Po znalezieniu region kodu z tym problemem, należy użyć debugera do sprawdzania, czy

Aby znaleźć przyczynę problemu, sprawdź kod problemu podczas uruchamiania aplikacji w debugerze:

* [Sprawdź zmienne](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) i sprawdź, czy zawierają one typ wartości, które powinny zawierać. Jeśli okaże się zła wartość dowiedzieć się, gdy została ustawiona nieprawidłowa wartość (Aby dowiedzieć się, gdy wartość została ustawiona, konieczne może być albo ponownie uruchom debuger, obejrzyj [stosu wywołań](../debugger/how-to-use-the-call-stack-window.md), lub obie).

* Sprawdź, czy aplikacja jest wykonywanie kodu, który będzie. (Na przykład może być kod używasz wyjątek i nie należy pamiętać, czy wystąpił wyjątek, aż zostanie wyświetlony kod obsługi wyjątków, Pobierz wywoływane dojść (ukrywa).)

## <a name="next-steps"></a>Następne kroki

W tym artykule kiedy znasz już kilka ogólne koncepcje debugowania. Następnie możesz uruchomić poznanie debugowanie przy użyciu programu Visual Studio.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
