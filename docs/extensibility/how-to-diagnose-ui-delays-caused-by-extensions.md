---
title: "Opóźnia diagnozowania rozszerzenie interfejsu użytkownika w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: PooyaZv
ms.author: pozandev
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9dede2f30a9d91e94bda3183deaae337e4c556dc
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Porady: diagnozowanie interfejsu użytkownika opóźnienia powodowane przez rozszerzenia

Gdy interfejsu użytkownika przestanie odpowiadać, Visual Studio sprawdza, czy stos wywołań wątku interfejsu użytkownika, począwszy od liścia i działają na bazie. Jeśli program Visual Studio Określa, że ramka stosu wywołań należy moduł, który jest częścią zainstalowane i włączone rozszerzenie, pokazuje powiadomienie.

![Opóźnienie reakcji interfejsu użytkownika (brak reakcji) powiadomień](media/ui-delay-notification-in-vs.png)

Powiadomienie informuje użytkownika, że opóźnienie reakcji interfejsu użytkownika (tzn. Brak reakcji w interfejsie użytkownika) mógł zostać wynik kod z rozszerzeniem. Umożliwia także użytkownika, z opcjami, aby wyłączyć rozszerzenie lub przyszłych powiadomień dla tego rozszerzenia.

W tym dokumencie opisano, jak diagnozować w kodzie rozszerzenia przyczynę powiadomienia opóźnienia interfejsu użytkownika. 

> [!NOTE]
> Nie należy używać eksperymentalne wystąpienie programu Visual Studio do diagnozowania występują opóźnienia interfejsu użytkownika. Niektórych części analizy stosu wywołań wymagane dla powiadomień opóźnienia interfejsu użytkownika są wyłączone, używając eksperymentalne wystąpienie, co oznacza powiadomienia opóźnienia interfejsu użytkownika nie mogą być wyświetlane.

Omówienie procesu diagnostyczne jest następujący:
1. Zidentyfikuj scenariusz wyzwalacza.
2. Ponowne uruchomienie programu VS z działaniem logowania.
3. Uruchom śledzenie zdarzeń systemu Windows.
4. Wyzwalanie powiadomienie, aby ponownie wyświetlone.
5. Zatrzymaj śledzenie zdarzeń systemu Windows.
6. Sprawdź dziennik aktywności można pobrać identyfikatora opóźnienia.
7. Przeanalizuj śledzenia zdarzeń systemu Windows za pomocą Identyfikatora opóźnienia w kroku 6.

W poniższych sekcjach rozszerzana tych kroków bardziej szczegółowo.

## <a name="identifying-the-trigger-scenario"></a>Identyfikujący ten scenariusz wyzwalacza

Aby zdiagnozować opóźnienia interfejsu użytkownika, należy najpierw idetify jakie (sekwencję akcji) powoduje, że Visual Studio, aby wyświetlić powiadomienie. To, aby można było możliwe do wyzwolenia powiadomienia później z włączenia funkcji dziennika.

## <a name="restarting-vs-with-activity-logging-on"></a>Ponowne uruchomienie w PORÓWNANIU z działaniem logowania

Visual Studio może wygenerować "Dziennik aktywności" udostępniająca informacje pomocne podczas debugowania problemu. Aby włączyć funkcję rejestrowania w programie Visual Studio aktywności, uruchom program Visual Studio z `/log` opcji wiersza polecenia. Po uruchomieniu programu Visual Studio dziennika aktywności są przechowywane w następującej lokalizacji:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Aby dowiedzieć się więcej na temat sposobu można znaleźć programu VS identyfikator wystąpienia, zobacz [narzędzia do wykrywania i Zarządzanie wystąpieniami programu Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Ten dziennik aktywności zostanie wykorzystany później, aby dowiedzieć się więcej informacji na temat występują opóźnienia interfejsu użytkownika i powiązane powiadomienia.

## <a name="starting-etw-tracing"></a>Uruchamianie śledzenia zdarzeń systemu Windows

Można użyć [narzędzia PerfView](https://github.com/Microsoft/perfview/) zbierać śledzenia zdarzeń systemu Windows. Narzędzia PerfView interfejs łatwy w użyciu zarówno do zbierania śledzenia zdarzeń systemu Windows i jego analizowanie. Aby zbierać śledzenia, użyj następującego polecenia:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Dzięki temu dostawcy "Programu Microsoft Visual Studio", który jest dostawcy, który używa programu Visual Studio dla zdarzenia związane z powiadomieniami opóźnienia interfejsu użytkownika. Określa również słowo kluczowe dostawcy jądra, który narzędzia PerfView służy do generowania widoku "Wątku czasu stosy".

## <a name="triggering-the-notification-to-appear-again"></a>Wyzwolenie powiadomienie, aby ponownie

Po rozpoczęciu zbierania danych śledzenia narzędzia PerfView można użyć sekwencji akcji wyzwalacza (z kroku 1), powiadomienia się ponownie. Po powiadomienie jest wyświetlane, można zatrzymać śledzenia kolekcji dla narzędzia PerfView do przetwarzania i generowanie pliku wyjściowego śledzenia.

## <a name="stopping-etw-tracing"></a>Zatrzymanie śledzenia zdarzeń systemu Windows

Aby zatrzymać zbieranie śladów, po prostu użyć `Stop collection` przycisk w oknie narzędzia PerfView. Po zatrzymaniu zbierania danych śledzenia narzędzia PerfView będzie automatycznie przetwarzać zdarzenia ETW i generuje dane wyjściowe pliku śledzenia.

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>Badania dziennika aktywności można uzyskać Identyfikatora opóźnienia

Jak wspomniano wcześniej, można znaleźć dziennika aktywności w `%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`. Za każdym razem, gdy Visual Studio wykryje rozszerzenie opóźnienia interfejsu użytkownika, zapisuje węzła do dziennika aktywności z `UIDelayNotifications` jako źródło. Ten węzeł zawiera cztery fragmentów informacji dotyczących opóźnienia interfejsu użytkownika:

- Identyfikator opóźnienia interfejsu użytkownika, kolejny numer, który unikatowo identyfikuje opóźnienia interfejsu użytkownika w sesji programu VS
- Identyfikator sesji, które jednoznacznie identyfikuje od początku, aby zamknąć sesję programu Visual Studio
- Określa, czy wyświetleniem powiadomienia dla opóźnienia interfejsu użytkownika
- Rozszerzenia plików, które może być spowodowane opóźnieniem interfejsu użytkownika

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Nie wszystkie występują opóźnienia interfejsu użytkownika powoduje powiadomienie. W związku z tym należy zawsze sprawdzić "Powiadomienia wyświetlane?" wartość poprawnie zidentyfikować prawo opóźnienia interfejsu użytkownika.

Po znalezieniu poprawne opóźnienia interfejsu użytkownika w dzienniku aktywności Zapisz podany identyfikator opóźnienia interfejsu użytkownika w węźle. Aby wyszukać odpowiednie zdarzenie ETW w następnym kroku użyjesz identyfikator.

## <a name="analyzing-the-etw-trace"></a>Analizowanie danych śledzenia zdarzeń systemu Windows

Następnie otwórz plik śledzenia. Można to zrobić przy użyciu tego samego wystąpienia narzędzia PerfView lub uruchamia nowe wystąpienie i ustawianie bieżącej ścieżki folderu w górnym lewym rogu okna do lokalizacji pliku śledzenia.

![Ustawianie ścieżki folderu w narzędzia Perfview](media/perfview-set-path.png)

Następnie w okienku po lewej stronie wybierz pliku śledzenia i otwórz go, wybierając z menu kliknij prawym przyciskiem myszy lub kontekstu Open.

> [!NOTE]
> Domyślnie narzędzia PerfView generuje archiwum Zip. Po otwarciu trace.zip automatycznie dekompresuje archiwum i otwiera śledzenia. Możesz to pominąć usuwając zaznaczenie pola wyboru pole "Zip" podczas zbierania śladu. Jednak jeśli zamierzasz przenieść i użyj ślady na różnych komputerach, szczególnie zalecamy usunięcie zaznaczenia pola "Zip". Bez tej opcji wymagane pliki PDB dla zestawów narzędzia Ngen nie zostanie przypisany śledzenia i w związku z tym symbole z zestawów narzędzia Ngen nie będą rozpoznawane na komputerze docelowym. (Zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) uzyskać więcej informacji na temat plików PDB dla zestawów narzędzia Ngen.) 

Może upłynąć kilka minut dla narzędzia PerfView do przetwarzania i otworzyć śledzenia. Po otwarciu śledzenia listę różnych "widoków" pojawiają się w nim.

![Widok podsumowania śledzenia narzędzia PerfView](media/perfview-summary-view-events-selected.png)

Najpierw używamy widok "Zdarzenia" można uzyskać przedział czasu opóźnienia interfejsu użytkownika:

1. Otwórz widok "Zdarzenia", wybierając węzeł "Zdarzenia" śledzenia i wybierając pozycję Otwórz menu kliknij prawym przyciskiem myszy lub kontekstu.
2. Wybierz opcję "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" w lewym okienku.
3. Naciśnij klawisz Enter

Zaznaczenie jest stosowana, a wszystkie `ExtensionUIUnresponsiveness` zdarzenia są wyświetlane w okienku po prawej stronie.

![Wybieranie zdarzeń w widoku zdarzeń](media/perfview-event-selection.png)

Każdy wiersz w okienku po prawej stronie odpowiada opóźnienia interfejsu użytkownika. Zdarzenie zawiera wartość "Opóźnienie ID", która powinna być zgodna z Identyfikatorem opóźnienia w dzienniku aktywności w kroku 6. Ponieważ `ExtensionUIUnresponsiveness` jest wywoływane na końcu opóźnienia interfejsu użytkownika, sygnatura czasowa zdarzenia (około) znaczniki czas zakończenia opóźnienia interfejsu użytkownika. Zdarzenie zawiera również czas trwania opóźnienia. Firma Microsoft odejmuje wartość czasu trwania z sygnatura czasowa zakończenia do uzyskania sygnatury czasowej podczas uruchamiania opóźnienia interfejsu użytkownika.

![Obliczanie opóźnienia interfejsu użytkownika w zakresie czasu](media/ui-delay-time-range.png)

Na poprzednim zrzucie ekranu na przykład sygnatura czasowa zdarzenia jest 12,125.679 i czas trwania opóźnienia jest 6,143.085 (ms). Tak więc,
* Opóźnienie rozpoczęcia jest 12,125.679 6,143.085 = 5,982.594.
* Zakres czasu opóźnienia interfejsu użytkownika jest 5,982.594 do 12,125.679.

Po mamy przedział czasu, możemy zamknąć okno widoku zdarzeń i otworzyć widok "Stosy wątków czasu (z działaniami StartStop)". Ten widok jest szczególnie przydatne, ponieważ często rozszerzeń, które blokują wątku interfejsu użytkownika jedynie oczekują na operacji I/E-granica lub inne wątki. W związku z tym widoku "Stosu Procesora", który jest opcja w większości przypadków, nie może przechwycić czasu wątek spędza, blokowanie, ponieważ nie używa Procesora w tym czasie. "Wątku czasu stosy" rozwiązuje ten problem, prawidłowo czas wyświetlania zablokowanych.

![Wątek węzła stosy czasu (z działaniami StartStop) w widoku Podsumowanie narzędzia PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Podczas otwierania "Wątku czasu stosy" wyświetlić, wybierz polecenie "devenv" proces można rozpocząć analizy.

![Widok stosy czas do interfejsu użytkownika analizy opóźnienie wątku](media/ui-delay-thread-time-stacks.png)

W widoku "Wątku czasu stosy" w górnym rogu strony, można ustawić przedział czasu do wartości, które firma Microsoft obliczona w poprzednim kroku i naciśnij klawisz Enter, więc stosy są dostosowane do tego zakresu czasu.

> [!NOTE]
> Określanie, który wątek jest interfejs użytkownika wątku (startowych) może być nielogiczne, jeśli kolekcja śledzenia jest uruchamiany po Visual Studio jest już otwarty. Jednak pierwszych elementów na stosie wątku interfejsu użytkownika (startowych) są najbardziej prawdopodobne zawsze dll systemu operacyjnego (ntdll.dll i kernel32.dll) następuje devenv!? a następnie msenv!?. Ta sekwencja można zidentyfikować wątku interfejsu użytkownika.

 ![Identyfikowanie uruchomienia wątku](media/ui-delay-startup-thread.png)

W tym widoku można również filtrować według tylko tym stosów zawierających modułów z pakietu.

* Wartość "GroupPats" pusty tekst, aby usunąć wszelkie grupowania domyślnie dodawane.
* Zestaw "IncPats" obejmować części nazwę zestawu, oprócz istniejący filtr procesu. W takim przypadku należy go "devenv; UIDelayR2 ".

![Ustawienie GroupPath i IncPath w widoku wątku czasu stosów](media/perfview-tts-group-path-inc-path.png)

Narzędzia PerfView przedstawiono szczegółowe wskazówki, w menu Pomoc, którego można użyć do zidentyfikowania wąskich gardeł wydajności w kodzie. Ponadto następujące linki udostępniają więcej informacji na temat sposobu korzystania z programu Visual Studio wątkowość interfejsy API w celu optymalizacji kodu:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

