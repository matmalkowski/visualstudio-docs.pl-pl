---
title: "Porady: diagnozowanie rozszerzenia wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: "1"
author: BertanAygun
ms.author: bertaygu
manager: ghogen
ms.workload: bertaygu
ms.openlocfilehash: 1d1034cce8b2fced5af48a0a4bfa8620b56994e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="measuring-extension-impact-in-startup"></a>Pomiaru wpływu rozszerzenia przy uruchamianiu

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Skupić się na wydajności rozszerzenia w Visual Studio 2017 r.

Na podstawie opinii klientów, została jedną obszarach zainteresowań dla wersji programu Visual Studio 2017 uruchamiania i rozwiązanie wydajność obciążenia. Podczas zespole platformy Visual Studio, możemy odbywała się wcześniej Praca poprawia wydajność obciążenia uruchamiania i rozwiązanie ogólnie rzecz biorąc, nasze dane telemetryczne sugeruje zainstalowanych rozszerzeń również może mieć znaczący wpływ na temat tych scenariuszy.

Aby ułatwić użytkownikom poznania zakresu przedstawionego wypływu, dodaliśmy nową funkcją w programie Visual Studio, aby powiadomić użytkowników powolne rozszerzeń. Visual Studio wykrycie nowe rozszerzenie spowolnieniem uruchamiania lub ładowania rozwiązania, użytkownicy będą widzieć powiadomień w IDE wskazaniem nowego okna dialogowego "Zarządzanie wydajnością programu Visual Studio". To okno dialogowe uzyskiwał zawsze menu Pomoc do przeglądania wykrytych wcześniej rozszerzenia.

![Zarządzanie działanie programu Visual Studio](media/manage-performance.png)

Ten dokument ma na celu pomóc deweloperom rozszerzenia przez opisujący sposób obliczania wpływ rozszerzenia i jak można ją analizować lokalnie Aby sprawdzić, czy rozszerzenie mogą być wyświetlane jako wydajności wpływające na rozszerzenia.

## <a name="how-extensions-can-impact-startup"></a>Wpływ uruchamiania rozszerzenia

Najbardziej typowe sposoby dla rozszerzenia, które mają wpływ na wydajność uruchamiania jest wybrać opcję automatycznego obciążenia w jednej uruchamiania znanych kontekstów interfejsu użytkownika takich jak NoSolutionExists lub ShellInitialized. Te konteksty interfejsu użytkownika uzyskać aktywowana podczas uruchamiania i wszelkie pakiety, które obejmują atrybut "ProvideAutoLoad" w ich definicji z tych kontekstach zostanie załadowana i zainicjowane w tej chwili.

Gdy firma Microsoft mierzymy jego wpływ na rozszerzenia, możemy głównie skupić się na czasu poświęcanego przez te rozszerzenia, które wybrać opcję automatycznego obciążenia w kontekstach powyżej. Mierzy czas będzie zawierać, ale nie jest ograniczona do:

* Podczas ładowania zestawów rozszerzenia synchroniczne pakietów
* Czas spędzony w konstruktorze klasy pakietu dla pakietów synchroniczne
* Czas spędzony w metodzie inicjowania (lub SetSite) pakietu synchroniczne pakietów
* Asynchroniczne pakietów wyżej czynności uruchomienie wątku w tle i w związku z tym są wykluczone z monitorowania
* Czas działania zaplanowane podczas inicjowania pakietu w głównym wątku asynchronicznego pracę
* Czas działania obsługi zdarzeń, w szczególności powłoki zainicjować kontekstu aktywacji lub zmiana stanu zombie powłoki
* Począwszy od programu Visual Studio 2017 Update 3, zostanie również rozpocznie się monitorowanie czas wykonywania na bezczynności połączenia przed zainicjowaniem powłoki. Dużo operacji w obsłudze bezczynności także spowodować odpowiadać IDE i przyczyniają się do czasu uruchomienia postrzegana przez użytkownika.

Dodano wiele funkcji, począwszy od programu Visual Studio 2015 w celu usunięcie potrzebę pakietów do automatycznego obciążenia, Odłóż ich obciążenia do bardziej szczegółowych przypadków, w których użytkownicy będą bardziej niektórych rozszerzenie lub zmniejszyć wpływ rozszerzenia podczas ładowania automatycznie.

Więcej informacji o tych funkcjach można znaleźć w następujących dokumentach:

[Konteksty interfejsu użytkownika na podstawie reguł](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): bogatsze aparat oparty na regułach opracowane w kontekstach interfejsu użytkownika pozwalają tworzyć niestandardowe kontekstów na podstawie typów projektów, odmian i możliwości. Te niestandardowe kontekstów można załadować pakietu podczas bardziej konkretnych scenariuszy, takich jak obecności projektu z konkretną funkcją zamiast uruchamiania; lub zezwolić [polecenia widoczność ograniczeni do niestandardowych kontekstu](visibilityconstraints-element.md) na podstawie możliwości projektu lub inne dostępne postanowienia, eliminując konieczność załadowania pakietu można zarejestrować obsługi zapytania stan polecenia.

[Obsługa asynchroniczne pakietu](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Nowa klasa podstawowa AsyncPackage w programie Visual Studio 2015 umożliwia pakietów programu Visual Studio do załadowania w tle asynchronicznie Jeśli pakiet obciążenia żądał atrybut obciążenia auto lub zapytania asynchronicznego usługi . Podczas ładowania tego tła umożliwia IDE pozostać odpowiadać podczas rozszerzenia został zainicjowany w tle i scenariuszy o kluczowym znaczeniu jak obciążenia uruchamiania i rozwiązanie nie będzie w pełni funkcjonalne.

[Asynchroniczne usług](how-to-provide-an-asynchronous-visual-studio-service.md): Z obsługą asynchroniczne pakietu dodaliśmy również obsługę asynchronicznie kwerenda usług i możliwość zarejestrowania asynchronicznych usług. Ważniejsze pracujemy nad konwertowanie podstawowe usługi Visual Studio obsługuje zapytania asynchronicznego, dzięki czemu większość pracy w zapytaniu async występuje w wątki w tle. SComponentModel (Visual Studio MEF host) jest jednym z głównych usług, które obsługuje teraz zapytania asynchronicznego, aby zezwalać na rozszerzenia obsługi asynchroniczne ładowanie całkowicie.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Zmniejszenie wpływu automatycznie załadować rozszerzeń

Jeśli pakiet nadal musi być automatycznie załadowany podczas uruchamiania, należy zminimalizować pracy podczas inicjowania pakietu, aby ograniczyć możliwość rozszerzenia wpływające na uruchamiania.

Przykłady powodujących inicjowania pakietu są kosztowne to:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Użyj pakietu synchroniczne obciążenia zamiast obciążenia asynchroniczne pakietu

Ponieważ synchroniczne pakiety są ładowane w głównym wątku domyślnie, firma Microsoft zachęca rozszerzenia właścicieli, których ładowane automatycznie pakietów, użyj zamiast tego, jak wspomniano wcześniej klasy podstawowej asynchroniczne pakietu. Zmiana pakiet załadowany automatycznie w celu obsługi asynchroniczne ładowanie będzie również ułatwić rozwiązać poniższe problemy.

### <a name="synchronous-filenetwork-io-requests"></a>Żądania We/Wy pliku synchroniczne i sieci

W idealnym przypadku żadnych synchroniczne żądania We/Wy pliku lub sieci należy unikać w głównym wątku ich wpływ będzie zależeć od stanu komputera i zablokować przez dłuższy czas, w niektórych przypadkach.

Przy użyciu pakietu asynchroniczne ładowanie i asynchroniczne We/Wy interfejsów API powinien zapewnić inicjowania pakietu nie blokuje wątku głównego w takich przypadkach i użytkownicy nadal mogą współdziałać z programem Visual Studio podczas żądań We/Wy występować w tle.

### <a name="early-initialization-of-services-components"></a>Inicjowanie wcześniejszego usług i składników

Jednym z typowych wzorców podczas inicjowania pakietu jest zainicjować usług używanych przez lub udostępniane przez ten pakiet w metodzie konstruktora lub zainicjować pakietu. Gdy gwarantuje to, że usługi są gotowe do użycia, można również dodać niepotrzebnych kosztów do pakietu podczas ładowania, jeśli te usługi nie są używane natychmiast. Zamiast tego takie usługi muszą zostać zainicjowane na żądanie, aby zminimalizować pracy podczas inicjowania pakietu.

Dostarczona przez pakiet usług globalnych można użyć metody AddService, które przyjmuje funkcja opóźnieniem zainicjować usługi tylko wtedy, gdy jest on wymagany przez składnik. W przypadku usług używanych w pakiecie, możesz użyć Lazy<T> lub AsyncLazy<T> do zapewnienia usług zainicjować/zbadać przy pierwszym użyciu.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Pomiaru wpływu automatycznie załadować rozszerzeń przy użyciu dziennika aktywności

Począwszy od programu Visual Studio 2017 Update 3 Dziennik aktywności programu Visual Studio będzie teraz zawierać wpisy dla pakietów wpływ na wydajność podczas uruchamiania i rozwiązanie obciążenia. Aby zobaczyć pomiarów, masz do uruchamiania programu Visual Studio z przełącznikiem/log i Otwórz plik ActivityLog.xml.

W dzienniku aktywności wpisy znajdują się w źródłowym "Zarządzanie wydajnością programu Visual Studio" i będą wyglądać jak poniżej:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Oznacza to tego pakietu z GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" poświęconego 2008 ms przy uruchamianiu programu Visual Studio. Należy pamiętać, że Visual Studio uwzględnia najwyższego poziomu koszt jako podstawowy numer, podczas obliczania wpływ pakietu jako wyniesie użytkownika savigs Zobacz podczas ich wyłączyć rozszerzenie dla tego pakietu.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Pomiaru wpływu automatycznie załadować rozszerzeń przy użyciu narzędzia PerfView

Podczas analizy kodu może ułatwić identyfikację ścieżki kodu, które może to spowolnić inicjowania pakietu, może również korzystać śledzenia przy użyciu aplikacji, takich jak narzędzia PerfView zrozumienie wpływu obciążenia pakietu przy uruchamianiu programu Visual Studio.

Narzędzia PerfView jest narzędziem do śledzenia szeroki system, który pomoże poznać gorących ścieżek w aplikacji, albo z powodu użycia procesora CPU lub blokuje wywołań systemowych. Poniżej przedstawiono prosty przykład na analizowanie Przykładowe rozszerzenie przy użyciu narzędzia PerfView dostępne pod adresem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Przykład kodu:**

Ten przykład jest oparty na przykład niektóre typowe przyczyny opóźnienia przypadek poniższego kodu, który jest przeznaczony do wyświetlenia:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Rejestrowanie śledzenia z narzędzia PerfView:**

Po skonfigurowaniu środowiska Visual Studio z rozszerzeniem zainstalowany można rejestrować śledzenia uruchamiania, należy otworzyć narzędzia PerfView i otwarcie okna dialogowego zbieranie z menu "Zbieranie".

![zbieranie menu Narzędzia perfview](media/perfview-collect-menu.png)

Domyślne opcje zapewni stosy wywołań wykorzystania Procesora, ale ponieważ interesuje NAS również czas blokowania, należy również włączyć stosów "Czas wątku". Po zatwierdzeniu gotowe ustawienia można polecenie "Rozpocznij zbieranie" i uruchom program Visual Studio po uruchomieniu rejestrowania.

Przed zatrzymaniem zbierania chcesz upewnij się, że Visual Studio jest w pełni zainicjowany, okno główne jest całkowicie widoczna i jeśli rozszerzenie zawiera wszystkie elementy interfejsu użytkownika, które są automatycznie wyświetlane, również są widoczne. Po Visual Studio jest całkowicie załadowany i rozszerzenie został zainicjowany, można zatrzymać rejestrowanie do analizowania śledzenia.

**Analizowanie danych śledzenia z narzędzia PerfView:**

Po zakończeniu rejestrowania narzędzia PerfView automatycznie otworzyć śledzenia i opcje.

Na potrzeby tego przykładu Dbamy głównie w widoku "Wątku czasu stosy", która znajduje się w grupie"Advanced". Ten widok wyświetli całkowity czas spędzony na wątek przy użyciu metody, w tym zarówno czas procesora CPU i czas blokowania, takich jak We/Wy dysku lub Oczekiwanie na dojściach.

 ![stosy wątków czasu](media/perfview-thread-time-stacks.png)

 Podczas otwierania "Wątku czasu stosy" widok, należy wybrać proces "devenv" można rozpocząć analizy.

Narzędzia PerfView przedstawiono szczegółowe instrukcje dotyczące odczytu wątku stosy czasu w obszarze własną menu Pomoc, aby uzyskać bardziej szczegółowe analizy. Do celów tego przykładu chcemy filtrowania tego widoku dalsze tylko włączając stosy z wątkiem naszych pakietów w module nazwy i uruchamiania.

1. Wartość "GroupPats" pusty tekst, aby usunąć wszelkie grupowania domyślnie dodawane.
2. Zestaw "IncPats", aby uwzględnić część nazwy zestawu i uruchomienia wątku oprócz istniejący filtr procesu. W takim przypadku należy go "devenv; Uruchamianie wątku; MakeVsSlowExtension".

Obecnie tylko pokazywanych jest koszt związany z zestawami związane z rozszerzenia. W tym widoku kiedykolwiek wymienione w kolumnie "Inc" (całkowity koszt) uruchomienia wątku jest powiązany z naszych filtrowane rozszerzenia i będzie mieć wpływ na uruchamiania.

Na przykład powyżej niektóre ciekawe wywołanie będzie stosy:

1. We/Wy przy użyciu klasy System.IO: całkowity koszt tych ramek nie może być bardzo kosztowna w śledzeniu, są potencjalną przyczyną problemu, ponieważ plik szybkości operacji We/Wy zależy od komputera.

  ![system We/Wy ramki](media/perfview-system-io-frames.png)

2. Blokowanie oczekiwanie na inne zadanie asynchroniczne wywołania: W tym przypadku całkowity czas będzie odpowiadają za czas wątku głównego jest zablokowany, po zakończeniu pracy asynchronicznego.

  ![Blokowanie ramki wywołania](media/perfview-blocking-call-frames.png)

Jeden z innymi widokami w śledzeniu, które mogą być przydatne do określenia wpływu będzie "Stosy obciążenia obrazu". Można zastosować filtry tej samej, jak stosować do widoku "Wątku czasu stosy" i sprawdzić wszystkie zestawy ładowane z powodu kod wykonywany przez pakiet załadowany automatycznie.

Jest ważne zminimalizować liczbę zestawów załadowanych wewnątrz procedura inicjowania pakietu, ponieważ każdy dodatkowego zestawu będzie obejmować We/Wy dysku dodatkowe, które może to spowolnić uruchamiania znacznie wolniejsze maszynach.

## <a name="summary"></a>Podsumowanie

Uruchamiania programu Visual Studio został jeden z obszarów, które firma Microsoft stale przesyłania opinii dotyczących. Naszym celem zgodnie z wcześniej jest dla wszystkich użytkowników do uruchomienia spójne środowisko niezależnie od tego, czy składniki i rozszerzenia, które są zainstalowane i chcemy pracować z rozszerzenia właścicieli, aby ułatwić im pomóc nam osiągnięcie tego celu. Wskazówki dotyczące powyżej powinny być pomocne w zrozumienie wpływu rozszerzenia podczas uruchamiania i albo uniknięcie automatycznie obciążenia lub załadować asynchronicznie, aby zminimalizować wpływ na wydajność pracy użytkownika.
