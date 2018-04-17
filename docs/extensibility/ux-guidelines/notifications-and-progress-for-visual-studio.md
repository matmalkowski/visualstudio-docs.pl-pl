---
title: Powiadomienia i postępu dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 237ed5c382a6ac880b0be59165a33ad338370976
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="notifications-and-progress-for-visual-studio"></a>Powiadomienia i postępu dla programu Visual Studio
##  <a name="BKMK_NotificationSystems"></a> Systemy powiadomień  
  
### <a name="overview"></a>Omówienie  
 Istnieje kilka sposobów, aby poinformować użytkownika, co dzieje się w programie Visual Studio dotyczące ich zadań rozwoju oprogramowania.  
  
 Podczas wdrażania jakiejkolwiek powiadomień:  
  
-   **Zachowaj liczba powiadomień do minimum** numer skuteczne. Komunikaty powiadomień należy zastosować większość użytkowników programu Visual Studio lub użytkownikom określonego funkcji/obszaru funkcji. Nadmiernego wykorzystania powiadomienia mogą sidetrack użytkownika lub zmniejszenia postrzegana łatwość użycia systemu.  
  
-   **Upewnij się, prezentuje Wyczyść, można wykonać wiadomości** czy użytkownik może użyć do wywołania odpowiedniego kontekstu do wprowadzania opcji bardziej złożone i podejmowania dalszych działań.  
  
-   **Przedstawia odpowiednio synchroniczne i asynchroniczne wiadomości.** Synchroniczne powiadomienia wskazują, że coś wymaga natychmiastowej reakcji, takich jak po awarii usługi sieci web lub kod wyjątku. Użytkownik powinien mieć świadomość, tych sytuacji od razu w taki sposób, który wymaga danych wejściowych, takich jak w modalnego okna dialogowego. Asynchroniczne powiadomienia są te, które użytkownik warto wiedzieć, ale nie muszą oni oddziaływać natychmiast, takie jak po zakończeniu operacji tworzenia lub a zakończeniu wdrożenia witryny sieci web. Te komunikaty powinny być bardziej otoczenia i nie przerywają pracy przepływ zadań użytkownika.  
  
-   **Użyj modalne okna dialogowe tylko wtedy, gdy jest to niezbędne uniemożliwić użytkownikowi podjęciem dalszych działań** przed potwierdzeniem wiadomości lub podjęciem decyzji o przedstawionych w oknie dialogowym.  
  
-   **Usuń otoczenia powiadomienia, gdy nie są już prawidłowe.** Wymaga od użytkownika odrzucić powiadomienie, jeśli już zostały działania w celu rozwiązania problemu, które zostały powiadamiany.  
  
-   **Należy pamiętać, że powiadomienia może prowadzić do korelacji wartość false.** Użytkownicy mogą nadzieję, że co najmniej jeden z nich działania ma wyzwalane powiadomienie, gdy w rzeczywistości nie było żadnych przyczynowego. Można w komunikatu powiadomienia o kontekście wyzwalacza i źródła powiadomienia.  
  
### <a name="choosing-the-right-method"></a>Wybór właściwej metody  
 Użyj tej tabeli, aby ułatwić wybór właściwej metody w celu powiadomienia użytkownika wiadomości.  
  
|Metoda|Zastosowanie|Nie należy używać|  
|------------|---------|----------------|  
|[Modalne błąd komunikatu w oknach dialogowych](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Użyj, jeśli odpowiedź użytkownika jest wymagana przed kontynuowaniem.|Należy używać, gdy nie istnieje potrzeba aby zablokować użytkownika i przerwania ich przepływu. Unikaj używania modalne okna dialogowe, jeśli jest to możliwe wyświetlić komunikat w sposób inny, ta opcja jest mniej pożądana.|  
|[Pasek stanu środowiska IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Użyj po otoczenia tekstową informacji dotyczących stanu procesu.|Nie używaj samodzielnie. Najlepiej używane w połączeniu z innego mechanizmu opinii.|  
|[Osadzony informacyjny](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|W oknie narzędzia lub okna dokumentu używany do powiadamiania postępu, błąd, wyniki i/lub informacji przydatnych wyników.|Należy używać, jeśli informacje nie są odpowiednie do lokalizacji, w którym znajduje się pasek informacyjny.<br /><br /> Nie należy używać poza oknem dokumentu/narzędzia.|  
|[Zmiany kursora myszy](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Może służyć do powiadomienia, że proces trwa. Umożliwia również powiadomienie, że jest zmiana stanu myszy, takie jak podczas przeciągania/upuszczania jest w toku lub wskaźnik myszy jest w niektórych trybie, takie jak tryb rysowania.|Nie należy używać krótkich postępu zmian lub fluttering z kursor jest prawdopodobnie (na przykład, jeżeli związany z części dłużej procesu uruchomionego zamiast całego procesu).|  
|[Wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Użycie, gdy potrzebne do raportu postępu (określony lub nieokreślony). Istnieją różne typy wskaźnik postępu i użycia określonego dla każdego. Zobacz [wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Visual Studio powiadomienia okna](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Okno powiadomień nie jest publicznie rozszerzonego. Jest on jednak używany do komunikowania się szereg wiadomości dotyczące programu Visual Studio, w tym krytyczne problemy z licencji i informacyjną powiadomienia o aktualizacji dla programu Visual Studio lub pakietów.|Nie należy używać innych typów powiadomień.|  
|[Lista błędów](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Problem odnosi się bezpośrednio do użytkownika aktualnie otwarte rozwiązanie o problemu (błąd/ostrzeżenie/info), może być muszą do wykonania akcji na kod.<br /><br /> Obejmuje to, na przykład:<br /><br /> -Komunikaty kompilatora (/ ostrzeżenia/informacje o błędzie)<br /><br /> -Code Analyzer/Diagnostyka wiadomości o kodzie<br /><br /> -Kompilacji wiadomości<br /><br /> Może być odpowiednie dla problemów dotyczących plików projektu lub rozwiązania, ale najpierw należy wziąć pod uwagę oznaczenie Eksploratora rozwiązań.|Nie używaj dla elementów, które nie mają żadnych relacji do kodu Otwórz rozwiązanie użytkownika.|  
|Edytor powiadomienia: żarówka|Stosowane, gdy użytkownik ma dostępne rozwiązać problem, który istnieje w otwartego pliku rozwiązania.<br /><br /> Należy pamiętać, że żarówki powinny być również używany hostingu szybkie akcje, które są pobierane dla kodu użytkownika na żądanie, takich jak refaktoryzacje, ale w takim przypadku nie będzie wyświetlany "styl powiadomień".|Nie używaj dla elementów, które nie mają żadnych relacji do otwartego pliku.|  
|Edytor powiadomienia: zygzaki|Użyj, aby ostrzec użytkownika wystąpił problem z określonego zakresu ich Otwórz kodu (na przykład czerwona falista błędów).|Nie używaj dla elementów, które nie odnoszą się do określonego zakresu ich Otwórz kodu.|  
|[Paski stanu osadzonych](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Umożliwia uzyskanie stanu dotyczące zawartości lub proces w kontekście określone okno, okno dokumentu lub okna dialogowego.|Nie należy używać produktu ogólne powiadomienia, procesów lub elementy, które nie mają żadnych relacji do zawartości w określonym oknie.|  
|[Powiadomień na pasku zadań systemu Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Służy do powierzchni powiadomienia dla procesów poza procesem lub pomocniczy aplikacji.|Nie używaj dla powiadomień, które mają zastosowanie w środowisku IDE.|  
|[Dymki powiadomień](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Użyj, aby powiadomić zdalnego procesu lub zmień **poza** IDE.|Nie należy używać jako środek do powiadamiania użytkownika procesów **w** IDE.|  
  
### <a name="notification-methods"></a>Metody powiadamiania  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> Modalne błąd komunikatu w oknach dialogowych  
 Komunikat Błąd modalne okno dialogowe służy do wyświetlania komunikat o błędzie, który wymaga zatwierdzenia lub akcji użytkownika.  
  
 ![Modalne komunikat](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **Okno dialogowe wiadomości modalnej błąd alerty użytkownika nieprawidłowe parametry połączenia z bazą danych**  
  
####  <a name="BKMK_IDEStatusBar"></a> Pasek stanu środowiska IDE  
 Prawdopodobieństwo, że użytkownicy zauważyć tekst na pasku stanu są powiązane z ich obsługi wszechstronne komputera i określonej doświadczenia z platformy Windows. Zwykle klientów programu Visual Studio wystąpić w obydwu tych obszarach chociaż nawet wiedzę użytkowników systemu Windows może pominąć zmian w pasku stanu. W związku z tym na pasku stanu najlepiej nadaje się do celów informacyjnych lub jako nadmiarowe wskazówki dla informacje przedstawione w innym miejscu. Dowolny rodzaj krytyczne informacje, że użytkownik musi zostać rozpoznany natychmiast należy podać w oknie dialogowym lub w oknie narzędzia powiadomienia.  
  
 Pasek stanu programu Visual Studio zaprojektowano w celu umożliwienia różne informacje mają być wyświetlane. Scenariusz jest podzielony na regiony dla opinii, Projektant pasek postępu, animacji i klienta.  
  
 Region opinii i region projektanta są zawsze widoczne. Pasek postępu i animacji regiony zawsze są dynamiczne i w zależności od kontekstu użytkownika. Region projektanta ma statyczny szerokość określa długość ciągu są pobierane z towarzyszącym zasobu wiadomości tekstowych. Umożliwia to lokalizacja zmienić rozmiar szerokość bez konieczności zmiany kodu. Dla języka angielskiego szerokość ten ciąg jest około 220 pikseli. Region projektanta będzie działać normalnie i region Opinia zostanie przyjęcia pozostałe miejsce.  
  
 Na pasku stanu jest również pokolorowane pozwala dodać visual zainteresowań i funkcjonalności wartość komunikując różnych zmian stanu IDE, np. gdy IDE w trybie debugowania.  
  
 ![Pasek koloru zmiany stanu IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **Kolory paska stanu środowiska IDE**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> Osadzony informacyjny  
 Można pasek informacyjny w górnej części okna dokumentu lub okna narzędzia informują użytkownika o stanu lub warunek. Można również zaoferować poleceń, dzięki czemu użytkownik może mieć sposób łatwo podjęcia odpowiednich działań. Pasek informacyjny jest standardowa powłoka kontrolą. Unikaj tworzenia własnych, co będzie działać i występować niespójne z innymi osobami w IDE. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) dla wskazówki dotyczące użycia i szczegóły implementacji.  
  
 ![Osadzone informacyjnym](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **Pasek informacyjny osadzony w oknie dokumentu, alerty użytkownika, który jest IDE w trybie debugowania historycznego i edytor nie będzie odpowiadać w taki sam sposób jak w trybie standardowym debugowania.**  
  
####  <a name="BKMK_MouseCursorChanges"></a> Zmiany kursora myszy  
 W przypadku zmiany kursora myszy, Użyj kolorów, które są powiązane z usługą VSColor i są już skojarzone z kursora. Kursor zmiany mogą służyć do wskazywania trwającą operacją, a także trafień stref, w którym użytkownik jest umieszczony nad docelowych, które mogą być przeciągnięte, upuszczone na lub używany do wybierania obiektu.  
  
 Tylko wtedy, gdy wszystkie dostępne czas procesora CPU musi być zarezerwowana dla operacji uniemożliwia wyrażanie żadnych dalszych danych wejściowych użytkownika za pomocą kursora myszy zajęty oczekiwania. W większości przypadków z dobrze napisanych aplikacji przy użyciu wielowątkowość powinna być rzadko razy, gdy użytkownicy nie będą mogli wykonywania innych operacji.  
  
 Należy pamiętać o tym, czy kursor zmiany są przydatne, nadmiarowe wskazówki informacje przedstawione w innym miejscu. Nie należy polegać na zmianę kursora jako jedyny sposób komunikowania się z użytkownikiem, szczególnie w przypadku próby przekazania coś, co jest ważne, czy użytkownik musi adresów.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> Wskaźniki postępu  
 Wskaźniki postępu są ważne w przypadku przekazywania opinii użytkowników podczas procesów, które przyjmują więcej niż kilka sekund. Wskaźniki postępu mogą być wyświetlane w miejscu (obok punkt uruchamiania działania w toku), na pasku stanu osadzone, modalnego okna dialogowego lub na pasku stanu programu Visual Studio. Postępuj zgodnie ze wskazówkami w [wskaźniki postępu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) dotyczące ich użycie i wdrożenie.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio powiadomienia okna  
 Okno programu Visual Studio powiadomienia powiadamia deweloperów o licencjonowania, środowisko (Visual Studio), rozszerzenia i aktualizacje. Użytkownicy, można odrzucić indywidualne powiadomienia lub zignorować określonych typów powiadomień. Na liście ignorowanych powiadomień jest zarządzana w **Narzędzia > Opcje** strony.  
  
 Okno powiadomień nie jest obecnie rozszerzonego.  
  
 ![Visual Studio powiadomienia okna](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Okno narzędzia usługi Visual Studio powiadomienia**  
  
####  <a name="BKMK_ErrorList"></a> Lista błędów  
 Powiadomienie w liście błędów wskazują błędów i ostrzeżeń, które wystąpiły podczas kompilacji i lub proces kompilacji i umożliwia użytkownikowi nawigację w kodzie do tego określonego kodu błędu.  
  
 ![Lista błędów](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Lista błędów w programie Visual Studio**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> Paski stanu osadzonych  
 Ponieważ pasek stanu IDE jest dynamiczny, jego kontekst regionu klienta ustawiono aktywne okno dokumentu i informacje o aktualizacji w kontekście użytkownika i/lub odpowiedzi systemu, trudno Obsługa ciągłego wyświetlania informacji o lub nadaj stanu dla długoterminowego asynchroniczne procesów. Na przykład na pasku stanu IDE nie jest odpowiedni dla powiadomień wyników uruchomienia testu dla wielu działa i/lub wybrane elementy można natychmiast wykonać elementu. Należy zachować takie informacje o stanie w kontekście okna dokumentu lub narzędzia gdzie użytkownika powoduje, że zaznaczenie lub rozpoczyna się proces.  
  
 ![Pasek stanu osadzonych](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Pasek stanu osadzonym w programie Visual Studio**  
  
####  <a name="BKMK_WindowsTray"></a> Powiadomień na pasku zadań systemu Windows  
 Zegar systemu Windows jest obok system w obszarze powiadomień na pasku zadań systemu Windows. Wielu narzędzi i składników oprogramowania Podaj ikony w tym obszarze, dzięki czemu użytkownik może uzyskać menu kontekstowe dla zadania systemowe, takie jak zmiana rozdzielczości ekranu lub uzyskiwania aktualizacji oprogramowania.  
  
 Powiadomień z poziomu środowiska powinny być udostępniane w Centrum powiadomień usługi Visual Studio nie obszaru powiadomień systemu Windows.  
  
####  <a name="BKMK_NotificationBubbles"></a> Dymki powiadomień  
 Dymki powiadomień może występować jako informacyjny w edytorze/projektanta lub jako część obszaru powiadomień systemu Windows. Użytkownik przewiduje te dymki jako problemy, które mogą rozwiązać później, czyli korzyści niekrytyczne powiadomień. Dymki nie mają zastosowania do kluczowych informacji, które użytkownik może rozwiązać od razu. Jeśli używasz dymki powiadomień w programie Visual Studio, wykonaj [Windows Desktop wskazówki dotyczące powiadomień dymki](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Powiadomienie w dymku](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Bąbelków powiadomień w obszarze powiadomień systemu Windows używane dla programu Visual Studio**  
  
##  <a name="BKMK_ProgressIndicators"></a> Wskaźniki postępu  
  
### <a name="overview"></a>Omówienie  
 Wskaźniki postępu są ważnym elementem systemu powiadomień nadanie opinie użytkowników. Informują one użytkownika, gdy ukończy procesy i działania. Typy wskaźników znanych obejmują paski postępu, kursory Obracająca i animowany ikon. Typ i położenia wskaźnika postępu zależy od kontekstu, w tym, co jest raportowane i jak długo procesu lub operacji spowoduje przejście do wykonania.  
  
#### <a name="factors"></a>Czynniki  
 Aby ustalić, jakiego typu wskaźnika jest odpowiednia, należy określić następujące czynniki.  
  
1.  **Czas:** czas operacji potrwa  
  
2.  **Modalność:** Określa, czy operacja jest modalne środowiska (blokady interfejsu użytkownika do czasu ukończenia procesu)  
  
3.  **Trwała/przejściowy:** Określa, czy wynik końcowy postępu musi być zgłoszony i/lub możliwych do wyświetlenia w późniejszym czasie  
  
4.  **Określony/nieokreślone:** czy od czasu zakończenia operacji i może zostać obliczona  
  
5.  **Grafika/Textual lokalizacji:** czy postępu lub procesu jest przechwyconych wbudowanych w treści wiadomości lub określonego formantu, takie jak formantu drzewa  
  
6.  **Zbliżeniowe:** czy postęp powinna być w pobliżu interfejsu użytkownika, który jest powiązany. (Na przykład może być na pasku stanu, która może być daleko, lub czy musi znajdować się w pobliżu przycisku, który uruchomił proces?)  
  
#### <a name="determinate-progress"></a>Określony postępu  
  
|Typ postępu|Kiedy i jak używać|Uwagi|  
|-------------------|-------------------------|-----------|  
|Pasek postępu (określania)|Oczekiwany czas trwania > 5 sekund.<br /><br /> Może obejmować tekstowy opis szczegóły procesu.|**Nie** osadzenia tekstu w animacji.|  
|Pasek informacyjny|Do obsługi komunikatów skojarzony z kontekstowe interfejsu użytkownika. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Może obejmować tekstowy opis szczegóły procesu.|**Nie** używać wielu infobars, gdy należy wskazać wiele procesów. Zamiast tego użyj paski postępu skumulowanych.|  
|Okno wyniku|Przejściowa powiadomień: procesu na poziomie aplikacji użytkownik chce **Przejrzyj** szczegóły po zakończeniu.|**Nie** Użyj, jeśli użytkownik musi odwoływać się do danych później.|  
|Plik dziennika|Łączyć się z intransient powiadomienia w przypadku, gdy ważne jest, aby **zapisać** szczegóły po zakończeniu.||  
|Pasek stanu|Przejściowa powiadomień: procesu na poziomie aplikacji ten użytkownik będzie **nie jest konieczne** szczegóły po zakończeniu.<br /><br /> Zawiera osadzony postępu zawierającej pasek.<br /><br /> Może obejmować tekstowy opis szczegóły procesu.||  
  
#### <a name="indeterminate-progress"></a>Nieokreślony postępu  
  
|Typ postępu|Kiedy i jak używać|Uwagi|  
|-------------------|-------------------------|-----------|  
|Pasek postępu (nieokreślony)|Oczekiwany czas trwania > 5 sekund.<br /><br /> Może obejmować tekstowy opis szczegóły procesu.|**Nie** osadzenia tekstu w animacji.|  
|Mrówki (animowany punktów w poziomie)|Obiegu do serwera.<br /><br /> Umieścić punktu near kontekstu górze kontenera nadrzędnego.|**Nie** Użyj, jeśli nie nadrzędnym całego kontenera.|  
|Pokrętła (postępu pierścienia)|Proces skojarzonego z kontekstowe interfejsu użytkownika lub miejsce w przypadku jest brany pod uwagę.<br /><br /> Może obejmować tekstowy opis szczegóły procesu.||  
|Pasek informacyjny|Do obsługi komunikatów skojarzony z kontekstowe interfejsu użytkownika. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Nie** używać wielu infobars, gdy należy wskazać wiele procesów. Zamiast tego użyj paski postępu skumulowanych.|  
|Okno wyniku|Przejściowa powiadomień: procesu na poziomie aplikacji ten użytkownik będzie chciał **Przejrzyj** szczegóły po zakończeniu.|**Nie** informacji, który ma zostać zachowany między sesjami.|  
|Plik dziennika|Łączyć się z intransient powiadomienia w przypadku, gdy ważne jest, aby **zapisać** szczegóły po zakończeniu.||  
|Pasek stanu|Przejściowa powiadomień: procesu na poziomie aplikacji ten użytkownik będzie **nie jest konieczne** szczegóły po zakończeniu.<br /><br /> Zawiera osadzony postępu zawierającej pasek.<br /><br /> Może obejmować tekstowy opis szczegóły procesu.||  
  
### <a name="progress-indicator-types"></a>Typy wskaźnika postępu  
  
#### <a name="progress-bars"></a>Paski postępu  
  
##### <a name="indeterminate"></a>Nieokreślony  
 ![Pasek postępu indeterminate](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **Pasek postępu indeterminate**  
  
 "Nieokreślony" oznacza ogólny postęp operacji lub nie można ustalić procesu. Użyj paski postępu nieokreślonym w operacjach wymagających niezwiązana ilość czasu lub uzyskania dostępu nieznany liczbę obiektów. Opis tekstowy umożliwia towarzyszą, co się stało. Użyj przekroczeń limitu czasu, aby nadać granice do czasową operacji. Paski postępu nieokreślony umożliwia wyświetlanie postępu odbywa się, że żadne inne informacje Podaj animacji. Nie należy wybierać pasek postępu indeterminate oparte tylko na możliwe brak dokładności samodzielnie.  
  
##### <a name="determinate"></a>Określony  
 ![Pasek postępu określania](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **Pasek postępu określania**  
  
 "Określony" oznacza, że działanie lub proces wymaga ograniczoną ilość czasu, nawet jeśli nie można dokładnie przewidzieć tego przedziału czasu. Wyraźnie wskazuje ukończenia. Niech pasek postępu, przejdź do 100 procent, chyba że działanie zostało zakończone. Animacja paska postępu określania Przenosi od lewej do prawej z zakresu od 0 do 100%.  
  
 Nigdy nie będzie przenoszony do tyłu podczas operacji wskaźnik postępu. Pasek należy przejść do przodu stopniowo po rozpoczęciu operacji i osiągnięcie 100% po jej zakończeniu. Punkt paska postępu jest dają pogląd jak długo całą operację przyjmuje, niezależnie od tego, ile kroki są związane z użytkownika.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Równoczesne raportowania (paski postępu skumulowany)  
 Jeśli operacja potrwa długo - prawdopodobnie kilka minut —, a następnie paski postępu dwóch mogą być używane, co który przedstawia ogólny postęp operacji i drugi dla postępu bieżącego etapu. Na przykład jeśli program instalacyjny kopiuje wiele plików, następnie co pasek postępu można wskazują, jak długo cały proces trwa podczas drugiej można wskazać, jaki procent bieżącego pliku lub katalogu są kopiowane. Nie zgłaszaj więcej niż pięć jednoczesnych operacji lub za pomocą paski postępu skumulowanych. Jeśli masz więcej niż pięć jednoczesnych operacji lub procesów do raportu za pomocą modalnego okna dialogowego przycisk Anuluj i raport szczegóły postępu w oknie danych wyjściowych.  
  
##### <a name="textual-descriptions"></a>Opis tekstowy  
 Użyj opis tekstowy towarzyszące, co dzieje się i szacowany czas do ukończenia. Jeśli nie jest możliwe ustalenie, jak długo trwa operacja, lepszym rozwiązaniem do przekazywania opinii może być animowane ikony zamiast pasek postępu.  
  
 Program Visual Studio udostępnia pasek postępu standard na pasku stanu, które mogą być używane przez każdego produktu zintegrowane w programie Visual Studio. Tekstowy opis co się dzieje, gdy jest animowany pasek postępu może zostać zaktualizowana tekst na pasku stanu.  
  
#### <a name="other-progress-indicators"></a>Inne wskaźniki postępu  
  
##### <a name="ants-animated-horizontal-dots"></a>Mrówki (animowany punktów w poziomie)  
 ![Postęp Mrówki](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 "Mrówki," animowany punktów w poziomie, stanowią wizualny materiał referencyjny w procesie serwera obustronne nieokreślony.  
  
##### <a name="spinner-progress-ring"></a>Pokrętła (postępu pierścienia)  
 ![Postęp pokrętła](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 Pokrętła (znanej także jako "pierścień postępu") jest wskaźnik postępu indeterminate używane głównie w odniesieniu do kontekstowe interfejsu użytkownika. Wyświetlanie pokrętło w pobliżu do jego zawartości powiązane, np. nagłówek kategorii tekstową, wiadomości lub kontrolki.  
  
##### <a name="cursor-feedback"></a>Kursor opinii  
 Dla operacji, które przyjmują od 2 do 7 sekund wyrazić swoją opinię kursora. Zazwyczaj oznacza to, za pomocą kursora oczekiwania dostarczane przez system operacyjny. Aby uzyskać wskazówki, zobacz artykuł w witrynie MSDN [Cursors.Wait właściwości](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Lokalizacje wskaźnik postępu  
  
##### <a name="status-bar"></a>Pasek stanu  
 Pasek stanu daje aplikacji miejsca do wyświetlania wiadomości i przydatne informacje do użytkownika bez przerywania pracy użytkownika. Zazwyczaj są wyświetlane w dolnej części okna, postępu będzie w stanie Porada okienka narzędzi zawierający komunikat dotyczący postępu miary w połączeniu ze wskaźnikiem pasek postępu.  
  
 ![Pasek stanu ze pasek postępu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **Pasek stanu ze pasek postępu**  
  
 ![Pasek stanu z obsługą wiadomości](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **Pasek stanu ze opis tekstowy**  
  
##### <a name="infobar"></a>Pasek informacyjny  
 Podobny do paska stanu paska informacyjnego zapewnia kontekstowe powiadomień i wiadomości, które również mogą łączyć się z wskaźniki postępu nieokreślony, np. paska postępu lub pokrętła. Paska informacyjnego nie powinien zawierać szczegółowym poziomie postępu lub oznaczenie określania postępu. Zobacz [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Pasek informacyjny z paska postępu i wiadomości](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **Pasek informacyjny pasek postępu i opis tekstowy**  
  
 ![Pasek informacyjny w oknie](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
##### <a name="inline"></a>Wbudowany  
 Wskazuje postęp wbudowanego może być reprezentowany przez dowolnego typu modułu ładującego postępu. Zazwyczaj wskaźnik postępu jest łączyć się z obsługą wiadomości, ale nie jest wymagane.  
  
 ![Wbudowany postępu pokrętła](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **Pokrętła połączone z opis tekstowy**  
  
 ![Paski postępu skumulowany wbudowanego](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **Paski postępu skumulowany określania**  
  
 ![Wbudowany postępu wiadomości](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **Tekst wbudowany Eksploratora serwera: odświeżanie...**  
  
##### <a name="tool-windows"></a>Okna narzędzi  
 Wskazuje postęp globalnego jest reprezentowany przez pasek postępu indeterminate znajduje się bezpośrednio pod paska narzędzi.  
  
 ![Pasek postępu indeterminate globalne](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **Team Explorer globalne nieokreślony ProgressBar**  
  
##### <a name="dialogs"></a>Okna dialogowe  
 Okna dialogowe może zawierać żadnego z typów modułu ładującego postępu. Wskaźniki postępu można można łączyć się z obsługą wiadomości jak również połączona z różnych poziomów wskazuje postęp reprezentują szczegółowego i procesy podrzędne.  
  
 ![Okno dialogowe zawierające wiele typów wskaźnika postępu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **Visual Studio okna dialogowego z procesów współbieżnych i wiele typów wskaźnika postępu**  
  
 ![Okno dialogowe z modułu ładującego postępu i wiadomości](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **Visual Studio okna dialogowego postępu modułu ładującego i wbudowanego wydawanie poleceń do obsługi komunikatów**  
  
##### <a name="document-well"></a>Dobrze dokumentu  
 W połączeniu z formantami dokumentu oraz można wyświetlić wiele typów modułu ładującego postępu.  
  
 ![Postęp wiadomości w dokumencie również](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **Pasek postępu indeterminate poniżej paska narzędzi**  
  
##### <a name="output-window"></a>Okno wyniku  
 W oknie danych wyjściowych jest odpowiednia dla obsługi postępu procesu i stan trwającej postępu za pośrednictwem wbudowanego wiadomości tekstowej. Należy używać paska stanu oraz wszelkie dane wyjściowe okna postępu raportowania.  
  
 ![Postęp w oknie danych wyjściowych do obsługi komunikatów](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **Okna wyjściowego ze stanem ciągły proces, a następnie zaczekaj do obsługi komunikatów**  
  
##  <a name="BKMK_Infobars"></a> Infobars  
  
### <a name="overview"></a>Omówienie  
 Infobars Przypisz użytkownika wskaźnik blisko punktu ich uwagi i za pomocą kontroli udostępnionych pasek informacyjny zapewnia spójność wyglądu i interakcji.  
  
 ![Infobar](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **Infobars w programie Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Odpowiednie używa pasek informacyjny  
  
-   Aby dać nieblokującą, ale ważne wiadomości odpowiednie dla bieżącego kontekstu użytkownika  
  
-   Aby wskazać, że interfejs użytkownika jest w niektórych stanu lub warunek, który prowadzi niektóre efekty interakcji, takich jak debugowanie historyczne  
  
-   Aby powiadomić użytkownika, że system wykrył problemy, takie jak kiedy rozszerzenie powoduje problemy z wydajnością  
  
-   Aby przyznać użytkownikowi sposób łatwo przełączyć akcji, na przykład jeśli edytor wykryje, że plik zawiera różne karty i spacji  
  
##### <a name="do"></a>Wykonaj:  
  
-   Zachowaj tekst komunikatu informacyjnym krótko i do punktu.  
  
-   Tekst łącza i przyciski, Zachowaj zwięzły.  
  
-   Upewnij się, że opcje "Akcja", które zapewniają użytkownikom są minimalne, pokazujący tylko wymagane akcje.  
  
##### <a name="dont"></a>Nie:  
  
-   Użyj paska informacyjnego oferowanie standardowych poleceń, które powinny być umieszczone w pasku narzędzi.  
  
-   Użyj paska informacyjnego zamiast modalnego okna dialogowego.  
  
-   Utwórz wiadomość przestawne poza oknem.  
  
-   Użyj wielu infobars w kilku lokalizacjach, w tym samym oknie.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Wiele infobars można wyświetlić w tym samym czasie?  
 Tak, wiele infobars można wyświetlić w tym samym czasie. Będą one wyświetlane w kto, obsługiwane w pierwszej kolejności z pierwszego przedstawiający na górnej i dodatkowe infobars przedstawiający poniżej paska informacyjnego.  
  
 Użytkownik będzie widział maksymalnie trzy infobars w czasie, po, więcej infobars są dostępne, region informacyjnym staną się przewijanego.  
  
### <a name="creating-an-infobar"></a>Tworzenie pasek informacyjny  
 Pasek informacyjny ma cztery sekcje od lewej do prawej:  
  
-   **Ikona:** jest to, gdzie należy dodać wszystkie ikona może zostać wyświetlony na pasku informacyjnym, takie jak ikona ostrzeżenia.  
  
-   **Tekst:** można dodać jest tekst opisujący użytkownika scenariusza/sytuacji, wraz z łączami w tekście, jeśli jest to wymagane. Należy pamiętać o zachowaniu zwięzły tekstu.  
  
-   **Akcje:** w tej sekcji powinny zawierać łącza i przyciski akcje wykonywane przez użytkownika na Twoje informacyjnym.  
  
-   **Przycisk Zamknij:** ostatniej sekcji z prawej strony może mieć przycisk Zamknij.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Tworzenie standardowych pasek informacyjny w kodzie zarządzanym  
 Klasa InfoBarModel może służyć do tworzenia źródła danych dla paska informacyjnego. Użyj jednej z tych czterech konstruktory:  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 Oto przykład, w którym tworzy InfoBarModel z tekstem hiperłącza, przycisku akcji i ikony.  
  
 ![Pasek informacyjny z hiperłączem](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Tworzenie standardowych pasek informacyjny w kodzie natywnym  
 Zaimplementuj interfejs IVsInfoBar zapewnić pasek informacyjny z kodu macierzystego.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Pobieranie pasek informacyjny UIElement z pasek informacyjny  
 Implementacja InfoBarModel lub IVsInfoBar są modeli danych, które musi być włączony do elementu UIElement celu będzie wyświetlany w interfejsie użytkownika. W usłudze elementu SVsInfoBarUIFactory/IVsInfoBarUIFactory można pobrać elementu UIElement.  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>Umieszczanie  
 Infobars można wyświetlić w co najmniej jednej z następujących lokalizacji:  
  
-   Okna narzędzi  
  
-   Na karcie dokumentu  
  
> [!IMPORTANT]
>  Istnieje możliwość umieść pasek informacyjny umożliwiają komunikat o kontekście globalnym. Zostanie wtedy wyświetlony między paski narzędzi i dobrze dokumentu. Nie jest to zalecane, ponieważ powoduje problemy z "skoku i jerk" IDE i należy unikać, chyba że bezwzględnie konieczne i właściwe.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Umieszczenie pasek informacyjny w obiektu ToolWindowPane  
 Metody ToolWindowPane.AddInfoBar(IVsInfoBar) można użyć do dodawania paska informacyjnego do okna narzędzia. Ten interfejs API można dodać IVsInfoBar (które InfoBarModel jest domyślna implementacja), lub elementu IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Umieszczenie pasek informacyjny w dokumencie lub z systemem innym niż obiektu ToolWindowPane  
 Umieszcza pasek informacyjny w dowolnym IVsWindowFrame, Pobierz IVsInfoBarHost ramki, użyj właściwości elementu vsfpropid_infobarhost zakończyło, a następnie dodaj pasek informacyjny UIElement.  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Umieszczenie pasek informacyjny w oknie głównym  
 Aby umieścić pasek informacyjny w oknie głównym, użyj VSSPROPID_MainWindowInfoBarHost usługi elementu IVsShell, aby uzyskać IVsInfoBarHost okno główne, a następnie dodaj pasek informacyjny UIElement do niego.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Będzie wiadomo, gdy użytkownik wykona akcję na mój informacyjnym?  
 Tak, wrócimy każda akcja zdarzeń autorowi paska informacyjnego. Następnie jest autorem informacyjnym podejmowanie działań w oparciu o wybór użytkownika na pasku informacyjnym IDE. Infobars zostaną automatycznie usunięte z hosta, którego Zamknij przycisk został kliknięty, ale jeśli Zamknij inne infobars muszą zostać usunięte po, są wymagane dodatkowe czynności. Dane telemetryczne również należy niezależnie rejestrowane przy każdym informacyjnym.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Odbieranie zdarzeń pasek informacyjny w obiektu ToolWindowPane  
 Obiektu ToolWindowPane ma dwa zdarzenia dla infobars. Zdarzenie InfoBarClosed jest wywoływane, gdy pasek informacyjny w obiektu ToolWindowPane jest zamknięty. Zdarzenie InfoBarActionItemClicked jest wywoływane, gdy hiperłącze lub przycisku w pasku informacyjnym zostanie kliknięty.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Odbieranie zdarzeń informacyjnym bezpośrednio z UIElement  
 IVsInfoBarUIElement.Advise umożliwia subskrybowanie zdarzeń bezpośrednio z UIElement informacyjnym. Implementowanie IVsInfoBarUIEvents umożliwi autora otrzymywanie Zamknij i zdarzenia kliknięcia.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> Błąd sprawdzania poprawności  
 Gdy użytkownik wprowadza informacje, które nie jest akceptowane, np. gdy zostanie pominięty wymaganego pola lub danych została wprowadzona w nieprawidłowy format, lepszym rozwiązaniem jest użycie kontroli poprawności lub opinii w pobliżu formantu zamiast blokowania okna dialogowego błędu menu podręczne.  
  
### <a name="field-validation"></a>Sprawdzanie poprawności pola  
 Weryfikacja formularza i pola składa się z trzech składników: formantu, ikonę i etykietkę narzędzia. Gdy kilka typów formantów użyć tej funkcji, pola tekstowego będzie służyć jako przykład.  
  
 ![Pole weryfikacji &#40;puste&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 Jeśli pole jest wymagane, powinien istnieć znaku wodnego tekst z informacją  **\<wymagany >** i tło pola powinna być jasny żółty (VSColor: `Environment.ControlEditRequiredBackground`) i pierwszego planu powinna być szary (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Pole weryfikacji z etykietą "Required"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 Program można określić, że formant jest w stanie *nieprawidłową zawartość wprowadzona* gdy fokus zostanie przeniesiony do innego formantu lub gdy użytkownik kliknie przycisk Zatwierdź [OK] lub gdy użytkownik zapisuje do formularza lub dokumentu.  
  
 Jeśli określana jest nieprawidłowy stan zawartości, pojawi się ikona w formancie lub po prostu obok siebie. Etykietka narzędzia zawierająca opis błędu powinny być wyświetlane przy aktywowaniu ikony lub kontrolki. Ponadto 1 piksel powinna pojawić się wokół formantu, który tworzy nieprawidłowy stan.  
  
 ![Pola specyfikacji układu weryfikacji](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **Specyfikacje układu dla pola weryfikacji**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Dopuszczalne odchyleń dla położenie ikony  
 Brak niezliczonych unikatowych przypadków, w których użytkownicy musieli informowany o błędach weryfikacji. Biorąc pod uwagę — typ formantu i Konfiguracja interfejsu użytkownika wybierz odpowiednie do sytuacji położenie ikony.  
  
 ![Dopuszczalne lokalizacje położenie ikony](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **Dopuszczalne odchyleń dla pola weryfikacji ikonę lokalizacji**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Sprawdzanie poprawności wymagające obiegu do serwera lub połączenia sieciowego  
 W niektórych przypadkach obiegu do serwera jest wymagany, aby sprawdzić zawartość i istotne do wyświetlenia użytkownika postępu, weryfikacji i stanów błędu. Poniżej rysunku przedstawiono przykład tego przypadku i zalecane interfejsu użytkownika.  
  
 ![Weryfikacja obejmujące obiegu do serwera](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **Sprawdzanie poprawności obejmujące obiegu do serwera**  
  
 Należy pamiętać, że aby zmieścił "Weryfikowanie..." i "Ponów" należy podać odpowiednie miejsca po prawej stronie formantu.  
  
#### <a name="in-place-warning-text"></a>Tekst ostrzeżenia w miejscu  
 W przypadku miejsca można umieścić komunikat o błędzie bliski formantu w stan błędu to zalecane jest stosowanie tylko tooltip.  
  
 ![W&#45;umieść ostrzeżenie](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **Tekst ostrzeżenia w miejscu**  
  
#### <a name="watermarks"></a>Znaki wodne  
 Czasami całego kontrolki lub okna jest w stanie błędu. W takiej sytuacji należy użyć znaku wodnego wskazująca błąd.  
  
 ![Znak wodny](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 07_Watermark")  
  
 **Sprawdzanie poprawności pola znaku wodnego**