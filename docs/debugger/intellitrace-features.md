---
title: Funkcje IntelliTrace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18e3058416e6ce14dd8a481eb5dd8f8200217895
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="intellitrace-features"></a>Funkcje IntelliTrace

Można użyć funkcji IntelliTrace, rejestrowanie zdarzeń i aplikacji, dzięki czemu można zbadać stanu (stosu wywołań i wartości zmiennych lokalnych) w różnych punktach podczas wykonywania wywołania metod. Po prostu zacznij debugowania w zwykły sposób — IntelliTrace jest domyślnie włączona i wyświetlane są informacje funkcji IntelliTrace jest rejestrowanie w nowym **narzędzia diagnostyczne** w obszarze **zdarzenia** kartę. Zaznacz zdarzenie i kliknij przycisk **Uaktywnij debugowanie historyczne** aby zobaczyć stos wywołań i zmiennych lokalnych zarejestrowane dla tego zdarzenia.

Aby uzyskać opis krok po kroku, zobacz [wskazówki: przy użyciu funkcji IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

Funkcja IntelliTrace jest dostępna w Visual Studio Enterprise edition, ale nie w wersji Visual Studio Professional lub społeczności.

Aby upewnić się, że funkcja IntelliTrace jest włączona, otwórz **Narzędzia > Opcje > IntelliTrace** strona Opcje. **Włącz IntelliTrace** powinny być domyślnie zaznaczone.

> [!NOTE]
> Zakres wszystkich ustawień na **IntelliTrace** strona Opcje jest Visual Studio jako całość, nie pojedynczych projektów lub rozwiązania. Zmiana tych ustawień ma zastosowanie do wszystkich wystąpień programu Visual Studio, wszystkie debugowania sesji i wszystkie projekty lub rozwiązania.

## <a name="ChooseEvents"></a> Wybierz zdarzenia tego rekordów funkcji IntelliTrace

Możesz włączyć lub wyłączyć rejestrowanie dla określonych zdarzeń funkcji IntelliTrace.

Jeśli debugujesz, Zatrzymaj debugowanie. Przejdź do **Narzędzia > Opcje > IntelliTrace > zdarzeń funkcji IntelliTrace**. Wybierz zdarzeń funkcji IntelliTrace do rejestrowania.

## <a name="Snapshots"></a> Zbieranie zdarzeń i migawki

To nie jest włączone domyślnie, ale IntelliTrace można przechwytywać migawki aplikacji w każdym zdarzeniu krok punktu przerwania i debuger i migawki te można wyświetlić w sesji debugowania historycznego. Migawka umożliwia widok z pełnym stanem aplikacji. Aby włączyć przechwytywania migawek, przejdź do **Narzędzia > Opcje > IntelliTrace > Ogólne**i wybierz **IntelliTrace zdarzenia i migawek**. Aby uzyskać więcej informacji, zobacz [wyświetlić migawki za pomocą kroku zwrotnego IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md)

Migawki są dostępne w Visual Studio Enterprise 2017 wersji 15.5 lub nowszej, a wymaga systemu Windows 10 Anniversary aktualizacji lub nowszej.  W przypadku aplikacji .NET Core i ASP.NET Core Visual Studio Enterprise 2017 wersji 15.7 preview 1 jest wymagana.

## <a name="GoingFurther"></a> Informacji o wywołaniach i zbierania zdarzeń funkcji IntelliTrace

Ta opcja nie jest domyślnie włączona, ale IntelliTrace można rejestrować wywołania metody oraz zdarzenia. Aby włączyć zbieranie metody wywołania przejdź do **Narzędzia > Opcje > IntelliTrace > Ogólne**i wybierz **zdarzeń funkcji IntelliTrace i informacji o wywołaniach**.

Informacje o wywołaniu nie jest obecnie dostępna w przypadku aplikacji .NET Core i ASP.NET Core. 

Dzięki temu można zobaczyć historię stosu wywołań i krok wstecz i przekazywać je do wywołań w kodzie. IntelliTrace rejestruje dane, takie jak nazwy metod, punkty wejścia i wyjścia — metoda i niektórych wartości parametrów i zwracanych wartości.

> [!TIP]
> Ta opcja nie jest włączona domyślnie, ponieważ powoduje ona dodanie znaczne obciążenie. Nie tylko ma IntelliTrace przechwycenia każdego wywołania metody, który sprawia, że aplikacja, ale również musi uwzględniać znacznie większy zestaw danych, jeśli chodzi o wyświetlaniu ją na ekranie lub utrwalanie go na dysku.
>
> Można zmniejszyć obciążenie ograniczając listę zdarzeń tego rekordów funkcji IntelliTrace i przechowując liczba modułów są zbierane do minimum. Aby uzyskać więcej informacji, zobacz [kontroli ilości informacji o wywołaniach IntelliTrace rekordów](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Użyj trasę nawigacji

Można użyć trasę nawigacji, który pojawia się z lewej strony okna kodu. Jeśli nie widzisz trasę nawigacji, przejdź do **Narzędzia > Opcje > IntelliTrace > Zaawansowane**i wybierz **wyświetlić trasę nawigacji w trybie debugowania**.

Trasę nawigacji umożliwia jej przeniesienie do przodu i do tyłu za pośrednictwem wywołania metod i zdarzeń w trybie debugowania historycznego. Aby uzyskać więcej informacji dotyczących debugowania historycznego, zobacz [debugowania historycznego](../debugger/historical-debugging.md). Ma wiele poleceń:

|||
|-|-|
|**Ustaw tutaj kontekst debugera**|Ustaw kontekst debugowania przedział czasu wywołania gdzie jest dostępny.<br /><br /> Ta ikona jest wyświetlana tylko dla bieżącego stosu wywołań.|
|**Wróć do miejsca wywołania**|Przesuń wskaźnik i kontekst debugowania do której wywołano bieżącej funkcji.<br /><br /> Jeśli jesteś w trybie debugowania na żywo, to polecenie włącza debugowanie historyczne. Jeśli przejdziesz do oryginalnego podziału wykonywania debugowania historycznego jest wyłączona i debugowania na żywo jest włączona.|
|**Przejdź do poprzedniego wywołania lub zdarzenia funkcji IntelliTrace**|Przenieś wskaźnik i debugowania kontekst z powrotem do poprzedniego wywołania lub zdarzenia.<br /><br /> Jeśli jesteś w trybie debugowania na żywo, to polecenie powoduje włączenie debugowania historycznego.|
|**Krok**|Krok do aktualnie wybranych funkcji.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy są w trybie debugowania historycznego.|
|**Przejdź do następnego wywołania lub zdarzenia funkcji IntelliTrace**|Przesuń wskaźnik i kontekst debugowania do następnego wywołania lub zdarzenia, dla których IntelliTrace danych istnieje.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy są w trybie debugowania historycznego.|
|**Przejdź do trybu na żywo**|Wróć do trybu debugowania na żywo.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Wyszukaj wiersz lub metodę w funkcji IntelliTrace

Metody można przeszukiwać tylko wtedy, gdy włączono informacje dotyczące wywołania metody. Można wyszukiwać historię funkcji IntelliTrace dla określonego wiersza lub metody. Podczas wykonywania debugera jest zatrzymywane, kliknij prawym przyciskiem myszy wewnątrz treści funkcji, aby wyświetlić menu kontekstowe i kliknij opcję **wyszukiwania dla tego wiersza w funkcji IntelliTrace** lub **wyszukiwania dla tej metody w funkcji IntelliTrace**.

### <a name="ControlCallData"></a> Kontroli ilości informacji o wywołaniach IntelliTrace rekordów

Domyślnie IntelliTrace rejestruje informacje dla wszystkich modułów, które są używane w tym rozwiązaniu. Można ustawić IntelliTrace wywołania rekordów tylko informacje dotyczące modułów, które są potrzebne. W **Narzędzia > Opcje > IntelliTrace > Moduły**, można określić moduły, aby dołączyć lub moduły do wykluczenia z funkcji IntelliTrace. IntelliTrace będzie zbierać zdarzenia, które pochodzą z modułów, które określono i wywołania metody, które wystąpiły w modułach myślisz.

Aby dodać wiele modułów, użyj symbolu wieloznacznego * na początku lub końcu ciągu. W przypadku nazwy modułów użyj nazw plików, nie nazw zestawów. Ścieżki plików nie są akceptowane.

Spróbuj zachować liczba modułów do minimum. Osiągnąć wyższą wydajność, ponieważ jest mniejsza ilość danych, które mają być zbierane. Mniej szumu umożliwia również wyświetlenie w interfejsie użytkownika, ponieważ istnieje podąża mniejszej ilości danych.

## <a name="SaveSession"></a> Zapisz dane funkcji IntelliTrace do pliku

Można zapisać dane, które zostały zebrane IntelliTrace do **debugowania > IntelliTrace > zapisać sesji funkcji IntelliTrace** podczas debugowania i aplikacja jest w stanie przerwania. Element menu jest wyłączone i nie można zapisać dane, które zebrał IntelliTrace, jeśli aplikacja jest nadal uruchomiona lub zatrzymaniu debugowania.

Można skonfigurować IntelliTrace automatycznie zapisać do pliku, przechodząc do **Narzędzia > Opcje > IntelliTrace > Zaawansowane** i wybierając **nagrań magazynu IntelliTrace w tym katalogu**. Można również skonfigurować Ustaw rozmiar dla wygenerowanego pliku, co powoduje, że IntelliTrace nadpisywać starszych danych, gdy zabraknie mu miejsca. Visual Studio tworzy dwa pliki dla każdej sesji funkcji IntelliTrace, kiedy są automatycznie zapisywane i Visual Studio proces hostingu (vshost.exe) jest włączona.

> [!TIP]
> Aby zaoszczędzić miejsce na dysku, wyłączyć zapisywanie plików automatycznie, gdy użytkownik nie są już potrzebne. Wszystkie istniejące pliki nie zostaną usunięte. Można zapisać do pliku na żądanie z menu kontekstowego.

Podczas zapisywania danych funkcji IntelliTrace do pliku, otrzymasz jednego pliku .itrace dla każdego procesu, który IntelliTrace zbierane z. Następnie możesz otworzyć pliku .itrace w programie Visual Studio, przechodząc do **Plik > Otwórz > pliku** i wybraniu pliku .itrace z okna dialogowego Otwieranie pliku. Aby uzyskać więcej informacji, zobacz [Using zapisywane są dane funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogi

[IntelliTrace w Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)

[Wskazówki dla debugowania na żywo przy użyciu funkcji IntelliTrace w programie Visual Studio 2015 (Edytor tekstu)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)

[Wskazówki dla debugowania na żywo przy użyciu funkcji IntelliTrace w programie Visual Studio 2015 (społecznościowych klub)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)

[IntelliTrace w Visual Studio Enterprise 2015 teraz obsługuje dołączyć!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)

[Zbierz dane z usługi systemu windows przy użyciu autonomiczny moduł zbierający IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)

[Edytowanie planu kolekcji funkcji IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)

[Niestandardowe TraceSource i debugowanie przy użyciu funkcji IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)

[Uruchomiony autonomiczny moduł zbierający IntelliTrace i pule aplikacji w obszarze kont usługi Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)

## <a name="forums"></a>Fora

[Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)

## <a name="videos"></a>Wideo

[Środowisko IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Debugowanie historyczne przy użyciu funkcji IntelliTrace w programie Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
