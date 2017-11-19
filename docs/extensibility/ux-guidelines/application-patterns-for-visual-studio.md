---
title: Wzorce aplikacji dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fad2e8d63b0005addab20756501d18fe872b4c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="application-patterns-for-visual-studio"></a>Wzorce aplikacji dla programu Visual Studio
##  <a name="BKMK_WindowInteractions"></a>Interakcje okna  
  
### <a name="overview"></a>Omówienie  
Dwa typy okno główne używane w programie Visual Studio są edytory dokumentu i okien narzędzi. Rzadkich, ale możliwe, są duże Niemodalne okna dialogowe. Mimo że są to wszystkie niemodalne w powłoce, ich wzorców są różni. W tej sekcji omówiono różnica między okna dokumentów, okien narzędzi i Niemodalne okna dialogowe. Wzorce modalnego okna dialogowego są objęte [okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Porównywanie wzorców użycia okna  
**Dokument windows** prawie zawsze są wyświetlane w tym dokumencie na również. Zapewnia edytor dokumentów "center etap" ułożyć dodatkowe narzędzia windows wokół.  
  
A **okna narzędzia** najczęściej jest wyświetlany jako okno oddzielnych, krótszych zwinięte względem krawędzi IDE. Może to być widoczny, ukryty lub ukryte automatycznie. Jednak czasami narzędzia windows przedstawiona w tym dokumencie dobrze, usuwając zaznaczenie pola wyboru **okna/dokowanie** właściwość okna. Powoduje to więcej nieruchomości, ale również decyzja projektowa common: podczas próby integracji w programie Visual Studio, należy zdecydować, czy funkcja Twoje powinien wyświetlać okno narzędzia lub okna dokumentu.  
  
**Niemodalne okna dialogowe** są niezalecane w programie Visual Studio. Najbardziej Niemodalne okna dialogowe zgodnie z definicją przestawne okna narzędzi i powinny być implementowane w ten sposób. Niemodalne okna dialogowe są dozwolone w przypadkach, gdy rozmiar okna narzędzia normalne zadokowane po stronie powłoki będzie zbyt ograniczenie. Mogą one również w przypadku, gdy użytkownik prawdopodobnie Przenieś okno dialogowe do monitora pomocniczego.  
  
Wziąć pod uwagę dokładnie informacje dotyczące typu kontenera należy. Typowe kwestie dotyczące wzorca użycia dla projektu interfejsu użytkownika znajdują się w poniższej tabeli.  
  
||Okna dokumentu|Okna narzędzi|Niemodalne okna dialogowego|  
|-|---------------------|-----------------|---------------------|  
| **Stanowisko** | Zawsze również znajduje się w dokumencie i nie dokowanie wokół krawędzi IDE. Go może być "pobierane" tak, że jest ona wyświetlana oddzielnie z poziomu głównego powłoki. | Zazwyczaj kartę zadokowane wokół krawędzi środowiska IDE, ale może być dostosowane będą zmienne, ukryte automatycznie (nieprzypiętych) lub zadokowane również w tym dokumencie.|Duże przestawne okno niezależnie od IDE. |  
| **Zatwierdź modelu** | *Opóźnione zatwierdzania*<br /><br /> Aby można było zapisać dane w dokumencie, użytkownik musi wysłać **pliku &gt; zapisać**, **Zapisz jako**, lub **Zapisz wszystko** polecenia. Okno dokumentu korzysta z koncepcji dane znajdujące się w nim trwa "dirtied", następnie zatwierdzone do jednego z zapisu poleceń. Podczas zamykania okna dokumentu, cała zawartość są zapisywane na dysku lub utracony. | *Natychmiastowe zatwierdzania*<br /><br /> Nie istnieje bez zapisywania modelu. Dla okien narzędzi inspektora wspomagające edycji pliku plik musi być otwarty w edytorze active lub projektanta i Edytor lub designer jest właścicielem zapisywania. | *Opóźnione lub natychmiastowe zatwierdzania*<br /><br /> W większości przypadków dużych niemodalnego okna dialogowego wymaga akcję w celu zatwierdzenia zmian i pozwala na operację "Anuluj", która wycofuje wszystkie zmiany wprowadzone w oknie dialogowym sesji.  Odróżniającą niemodalnego okna dialogowego z poziomu okna narzędzia, z tego narzędzia windows zawsze ma modelu natychmiastowego zatwierdzania. |  
| **Widoczność** | *Otwórz/Utwórz (plik), a następnie zamknij*<br /><br /> Otwieranie okna dokumentów odbywa się przy użyciu otwierania istniejącego dokumentu lub przy użyciu szablonu, aby utworzyć nowy dokument. Brak nie "Otwórz \<Edytor >" polecenia. | *Ukryj i Pokaż*<br /><br /> Okna narzędzi jednego wystąpienia może być ukryte lub pokazane. Zawartość i stanów w oknie narzędzia zachować, czy w widoku lub ukryte. Wielu wystąpieniach narzędzia windows może być zamknięte także ukryte. Po zamknięciu okna narzędzia wielu wystąpień, zawartość i stanu w oknie narzędzia zostaną odrzucone. | *Uruchomić polecenia*<br /><br /> Okna dialogowe uruchamiania polecenia opartego na zadaniach. |  
| **Wystąpienia** | *Mająca wiele wystąpień*<br /><br /> Wiele edytorów można otworzyć na tym samym czasie i edytowania różnych plików, gdy niektóre edytory również umożliwić tego samego pliku były otwarte w edytorze więcej niż jeden (przy użyciu **okna &gt; nowe okno** polecenia).<br /><br /> Pojedynczy Edytor może edytować jednego lub wielu plików jednocześnie (Projektant projektu). | *Jeden lub kilku instance*<br /><br /> Zawartość zmienia do uwzględnienia kontekstu (jak przeglądarka właściwości) lub Wypchnij fokus/kontekstu do innych okien (Lista zadań, Solution Explorer).<br /><br /> Zarówno w jednym wystąpieniu, jak i w wielu wystąpień narzędzia windows powinna być skojarzona z okna dokumentów aktywnych, chyba że przekonujący powód nie ma pozycji. | *Jednego wystąpienia* |  
| **Przykłady** | **Edytory tekstów**, takich jak Edytor kodu<br /><br /> **Projektowanie powierzchni**, takie jak projektanta formularza lub powierzchni modelowania<br /><br /> **Kontrolowanie układów podobne do okien dialogowych**, takich jak projektanta manifestu | **Eksploratora rozwiązań** zapewnia rozwiązanie i projekty zawarty w rozwiązaniu<br /><br /> **Eksploratora serwera** udostępnia hierarchiczny widok połączeń serwerów i danych, które użytkownik wybierze opcję Otwórz okno. Otwiera obiekt z bazy danych hierarchii, takie jak zapytania, zostanie otwarte okno dokumentu i umożliwia użytkownikom edytowanie zapytania.<br /><br /> **Przeglądarka właściwości** Wyświetla właściwości dla obiekt wybrany w oknie dokumentu lub innego okna narzędzia. Właściwości są prezentowane w widoku siatki hierarchiczna lub złożonych formantów okna dialogowego przypominającej i Zezwalaj użytkownikowi na ustawianie wartości tych właściwości. | |  
  
##  <a name="BKMK_ToolWindows"></a>Okna narzędzi  
  
### <a name="overview"></a>Omówienie  
Narzędzia systemu windows obsługuje pracy użytkownika, który odbywa się w dokumencie systemu windows. One może służyć do wyświetlania hierarchii, która reprezentuje obiekt główny podstawowych programu Visual Studio udostępnia i można manipulować.  
  
Rozważając nowe okno narzędzi w środowisku IDE, autorzy następujące czynności:  
  
-   Użyć odpowiednich zadań istniejących narzędzia windows i nie tworzyć nowe o podobnych możliwościach. Nowe narzędzia windows powinien zostać utworzony tylko, jeśli oferują różne "narzędzia" lub funkcje, które nie może zostać zintegrowany do podobnych okna lub wyłączając istniejącego okna do obrotowego koncentratora.  
  
-   Użyj paska poleceń standardowych, jeśli to konieczne, w górnej części okna narzędzia.  
  
-   Być zgodne z wzorców znajduje się już w innych okien narzędzi dla formantu nawigacji prezentacji i klawiatury.  
  
-   Być zgodne z prezentacji kontroli w innych okien narzędzi.  
  
-   Wyświetlaj okna narzędzi specyficznych dla dokumentu automatycznie — Jeśli to możliwe, aby były wyświetlane tylko po aktywowaniu dokumentu nadrzędnego.  
  
-   Upewnij się, że ich zawartość okna jest można nawigować przez klawiatury (klawisze strzałek pomocy technicznej).  
  
#### <a name="tool-window-states"></a>Stany okna narzędzi  
Visual Studio narzędzia windows mają różne stany, niektóre z nich są aktywowane użytkownika (na przykład funkcja autoukrywania). Inne stany, takich jak automatyczne widoczne, a także zezwalanie okna narzędzi są wyświetlane w poprawny kontekst i ukrywanych, gdy nie jest wymagane. Całkowita liczba istnieje pięć stanów okna narzędzia.  
  
-   **Zadokowane przypięty** okna narzędzi można dołączyć do dowolnego z czterech stron obszaru dokumentu. Ikonę pinezki pojawia się w pasku tytułu okna narzędzia. Okno narzędzia może być zadokowany poziomo czy pionowo wzdłuż krawędzi powłoka i inne narzędzia windows i mogą być łączone przez karty.  
  
-   **Ukryte automatycznie** odpiąć są narzędzia systemu windows. Okno można przesunąć niewidocznym, pozostawiając kartę (wraz z nazwą okna narzędzia i jego ikonę) na krawędzi obszaru dokumentu. Okno narzędzia slajdów się, gdy użytkownik znajduje się nad karcie.  
  
-   **Automatycznie widoczne** narzędzia windows automatycznie wyświetlane, gdy inny element interfejsu użytkownika, takich jak edytor jest uruchamiana lub zyskuje fokus.  
  
-   **Liczby zmiennoprzecinkowe** okna narzędzi, umieść kursor poza IDE. Jest to przydatne w przypadku konfiguracji z wieloma monitora.  
  
-   **Dokument z kartami** narzędzia windows może być również zadokowany w dokumencie. Jest to przydatne w przypadku dużych narzędzia systemu windows, takich jak przeglądarki obiektów, wymagającym nieruchomości więcej niż dokowanie krawędziami ramki umożliwia.  
  
![Narzędzie Stany okien w programie Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702 01_ToolWindowStates")<br />Stany okna narzędzia w programie Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>Jednego wystąpienia i wielu wystąpień  
Narzędzia systemu windows są wystąpienia jednego lub wielu wystąpień. Niektóre narzędzia jednego wystąpienia windows może być skojarzony z oknem aktywnego dokumentu, podczas gdy wielu wystąpieniach narzędzia windows nie może. Mająca wiele wystąpień narzędzia windows odpowiadanie na **okna &gt; nowe okno** polecenia, tworząc nowe wystąpienie klasy okna. Na poniższym obrazie przedstawiono Włączanie nowe okno polecenia, gdy wystąpienie okno jest aktywne okno narzędzia:  
  
![Okno narzędzia umożliwiające polecenia "Nowe okno", gdy wystąpienie klasy okna jest aktywna](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")<br />Okno narzędzia umożliwiające polecenia "Nowe okno", gdy wystąpienie okno jest aktywne  
  
Okna narzędzi jednego wystąpienia można ukryte lub pokazane, gdy wielu wystąpieniach narzędzia windows może zostać zamknięty, a także ukryte. Wszystkie okna narzędzia może być zadokowany łączone przez karty zmiennoprzecinkowych i ustawione jako okna podrzędnego interfejsu wielu dokumentów (MDI) (podobnie do okna dokumentu). Wszystkie narzędzia windows powinno odpowiedzieć na odpowiednie okno polecenia zarządzania w menu okna:  
  
![Polecenia zarządzania okna w menu programu Visual Studio okno](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702 03_WindowManagementControls")<br />Polecenia zarządzania okna w menu programu Visual Studio okno
  
#### <a name="document-specific-tool-windows"></a>Okna narzędzi specyficznych dla dokumentu  
Niektóre narzędzia windows zostały zaprojektowane do zmieniają się w zależności od danego typu dokumentu. Te windows stale update, aby odzwierciedlić funkcje mające zastosowanie do aktywnego okna dokumentu w IDE.  
  
Narzędzia systemu Windows, których zawartość zmieniać, aby odzwierciedlić wybrane Edytor przykładów przybornika i tworzenie konspektu dokumentu. Te okna Pokaż znak wodny, gdy Edytor ma fokus oferuje kontekstu do okna.  
  
#### <a name="navigable-list-tool-windows"></a>Listy można nawigować okna narzędzi  
Niektóre narzędzia windows wyświetlanie listy elementów można nawigować, które użytkownik może interakcyjnie przeprowadzić. W tym typie okna zawsze należy opinię dotyczącą bieżący element na liście, nawet jeśli okno jest nieaktywne. Listy powinno odpowiedzieć na **GoToNextLocation** i **GoToPrevLocation** polecenia zmieniając również aktualnie zaznaczony element w oknie  
  
Przykładem listy można nawigować narzędzia windows są Eksploratora rozwiązań i w oknie Znajdź wyników.  
  
### <a name="tool-window-types"></a>Typy okien narzędzi  
  
#### <a name="common-tool-windows-and-their-functions"></a>Typowe narzędzia systemu windows i ich funkcje

**Hierarchiczna narzędzia systemu windows**
| Okna narzędzi | Funkcja | 
| --- | --- | 
| Eksplorator rozwiązań | Hierarchiczna drzewa, który wyświetla listę dokumentów znajdujących się w projektach, różne pliki i elementy rozwiązania. Wyświetlanie elementów w obrębie projektów jest zdefiniowana przez pakiet, który jest właścicielem tego typu projektu (na przykład typy odwołania na podstawie katalogu i trybu mieszanego). | 
| Widok klas | Hierarchiczna drzewa klas i różnych elementów w zestawie roboczym dokumentów, niezależnie od same pliki. | 
| Server Explorer | Hierarchiczne drzewo do wyświetlania wszystkich połączeń serwerów i danych w rozwiązaniu. | 
| Konspekt dokumentu | Struktura hierarchiczna aktywny dokument. | 

**Okna narzędzi siatki**
| Okna narzędzi | Funkcja | 
| --- | --- | 
| Właściwości | Siatka wyświetla listę właściwości dla wybranego obiektu, wraz z selektorami wartość, aby edytować te właściwości. | 
| Lista zadań | Siatka, który umożliwia użytkownikowi tworzenie/edytowanie/usuwanie zadań i komentarze. | 

**Okna narzędzi zawartości**
| Okna narzędzi | Funkcja | 
| --- | --- | 
| Pomoc | Okno, który umożliwia użytkownikom dostęp do różnych metod uzyskiwanie pomocy od "Jak?" wideo na forach MSDN. | 
| Dynamiczna pomoc | Okno narzędzia wyświetlającą łącza, które ułatwiają tematy mające zastosowanie do bieżącego zaznaczenia. | 
| Przeglądarka obiektów | Zestaw ramek dwie kolumny z listy składników hierarchiczna obiektu w okienku po lewej stronie i obiektu właściwości i metod w prawej kolumnie. | 

**Okna narzędzi okna dialogowego**
| Okna narzędzi | Funkcja | 
| --- | --- | 
| Znajdź | Okno dialogowe, które umożliwia użytkownikom znajdowanie lub znajdowanie i zamienianie w różnych plikach w ramach rozwiązania. |
| Wyszukiwania zaawansowanego | Okno dialogowe, które umożliwia użytkownikom znajdowanie lub znajdowanie i zamienianie w różnych plikach w ramach rozwiązania. | 

**Inne okna narzędzi**
| Okna narzędzi | Funkcja | 
| --- | --- | 
| Przybornik | Okno narzędzia używane do przechowywania elementów, które zostaną usunięte na powierzchni projektu, zapewniając spójne źródła przeciągania dla wszystkich projektantów. |
| Strona początkowa | Portal użytkownika dla programu Visual Studio, dostęp do źródła wiadomości dla programistów, pomocy programu Visual Studio i ostatnich projektów. Użytkownicy mogą także tworzyć start niestandardowych stron przez skopiowanie pliku StartPage.xaml z "Common7\IDE\StartPages\" katalogu plików programu Visual Studio do folderu StartPages w programie Visual Studio dokumentów katalogu, a następnie albo edytowania XAML ręcznie lub otworzyć go w programie Visual Studio lub innego edytora kodu. | 

**Debuger okna narzędzi**
| Okna narzędzi | Funkcja | 
| --- | --- |
| Automatycznych ||  
| Natychmiastowe ||  
| Dane wyjściowe | W oknie danych wyjściowych można zawsze tekstową zdarzenia lub stan, aby zadeklarować. |  
| Pamięć ||  
| Punkty przerwania ||  
| Uruchomienie ||  
| Dokumenty ||  
| Stos wywołań ||  
| Zmienne lokalne ||  
| Obserwowanie ||  
| Dezasemblacji ||  
| Rejestruje ||  
| Wątki ||  
  
##  <a name="BKMK_DocumentEditorConventions"></a>Konwencje dokumentów edytora  
  
### <a name="document-interactions"></a>Interakcje z dokumentu  
"Także dokumentu" jest największą ilością miejsca w środowisku IDE i których użytkownik ma skupione ich uwagi do wykonywania swoich zadań, wspierana przez dodatkowe narzędzia systemu windows. Edytory dokumentu reprezentują podstawowe jednostki pracy, który użytkownik otwiera i zapisuje w programie Visual Studio. Zachowują silne zorientować się zaznaczenie związany z Eksploratora rozwiązań lub innych okien aktywnej hierarchii. Użytkownik powinien mieć możliwość wskazywał jeden z tych hierarchii systemu windows i wiedzieć, gdzie znajduje się dokument i jej zależności do rozwiązania, projektu lub innego obiektu głównego udostępniane przez pakiet programu Visual Studio.  
  
Edytowanie dokumentu wymaga spójną obsługę użytkowników. Aby zezwolić użytkownikowi skupić się na wykonywanego zadania zamiast na zarządzania systemem Windows w celu znalezienia poleceń, wybierz strategii widoku dokumentu, która najlepiej pasuje do zadań użytkownika do edycji tego typu dokumentu.  
  
#### <a name="common-interactions-for-the-document-well"></a>Typowe interakcje dobrze dokumentu  
  
-   Obsługa modelu interakcji spójna we wspólnym **nowy plik** i **Otwórz plik** wykonywania.  
  
-   Zaktualizuj funkcje w powiązanych okien i menu, po otwarciu okna dokumentu.  
  
-   Polecenia menu odpowiednio są zintegrowane z menu wspólne, takie jak **Edytuj**, **Format**, i **widoku** menu. Jeśli rozległe specjalne polecenia są dostępne, mogą być tworzone nowe menu. To menu Nowy powinny być widoczne tylko wtedy, gdy dokument ma fokus.  
  
-   Osadzony narzędzi mogą być umieszczane w górnej części edytora. To jest posiadanie oddzielnego narzędzi, który znajduje się poza edytora.  
  
-   Obsługa zawsze zaznaczenie w Eksploratorze rozwiązań lub podobne aktywne okno hierarchii.  
  
-   Dwukrotne kliknięcie dokumentu w Eksploratorze rozwiązań, należy wykonać ta sama akcja co **Otwórz**.  
  
-   Jeśli więcej niż jeden z nich może być używany dla typu dokumentu, użytkownik powinien móc zastąpienia lub zresetować domyślne działanie przy użyciu typu danego dokumentu **Otwórz za pomocą** okno dialogowe prawym przyciskiem myszy plik i wybierając **Otwórz Z** z menu skrótów.  
  
-   Nie Konstruuj również kreatora w dokumencie.  
  
### <a name="user-expectations-for-specific-document-types"></a>Oczekiwań użytkownika dla określonych typów dokumentów  
Istnieje kilka różnych typów podstawowych edytory dokumentu, a każdy ma zestaw interakcji, które są zgodne z innymi tego samego typu.  
  
-   **Edytor tekstowy:** edytora kodu, pliki dziennika  
  
-   **Dzięki powierzchni projektowej:** WPF formularze projektanta formularzy systemu Windows  
  
-   **Edytor stylów okna dialogowego:** projektanta manifestu, właściwości projektu  
  
-   **Projektant modelu:** projektanta przepływów pracy, codemap, diagram architektury, postępu  
  
Istnieje kilka typów innych niż edytora, które również za pomocą dokumentu. Podczas edytowania nie same dokumenty, muszą wykonaj standardowe interakcji dla okna dokumentów.  
  
-   **Raporty:** IntelliTrace raport raport funkcji Hyper-V raportów profilera  
  
-   **Pulpit nawigacyjny:** Centrum diagnostyki  
  
#### <a name="text-based-editors"></a>Edytory oparte na tekst  
  
-   Dokument uczestniczy w modelu kartę Podgląd, co pozwala na wyświetlanie podglądu dokumentu bez konieczności otwierania go.  
  
-   Strukturę dokumentu mogą być reprezentowane w obrębie okna narzędzia pomocnika, takich jak konspektu dokumentu.  
  
-   IntelliSense (w razie potrzeby) będą działać spójnie z innych edytory kodu.  
  
-   Wyskakujące okienka lub pomocniczej interfejsu użytkownika wykonaj podobne style i wzorce istniejących podobne interfejsu użytkownika, takie jak CodeLens.  
  
-   Komunikaty dotyczące stanu dokumentu zostanie wyświetlone w formancie informacyjnym w górnej części dokumentu lub na pasku stanu.  
  
-   Użytkownik musi mieć możliwość dostosowania wyglądu czcionek i kolorów przy użyciu **Narzędzia > Opcje** strony udostępnionym czcionki i kolory lub jeden specyficzne dla edytora.  
  
#### <a name="design-surfaces"></a>Powierzchni projektu.  
  
-   Pusty projektanta powinien mieć znaku wodnego na powierzchni wskazująca, jak rozpocząć pracę.  
  
-   Mechanizmy przełączania widoku są zgodne z istniejących wzorców, takich jak kliknij dwukrotnie, aby otworzyć Edytor kodu lub karty w oknie dokumentu, umożliwiając interakcji z obu okienka.  
  
-   Dodawanie elementów do powierzchni projektowej ma się odbywać za pośrednictwem przybornika, chyba że specjalistyczne okno jest wymagany.  
  
-   Elementy na powierzchni są zgodne z modelu spójne zaznaczenia.  
  
-   Paski narzędzi osadzony zawierać poleceń specyficznych dla dokumentu tylko, nie Typowe polecenia, takich jak **zapisać**.  
  
#### <a name="dialog-style-editors"></a>Edytory styl okna dialogowego  
  
-   Układ formantu powinna zgodne z konwencjami normalne okna dialogowego układu.  
  
-   Karty w edytorze nie powinny odpowiadać wygląd kart dokumentu, powinien spełniają jeden z dwóch stylów dozwolonych karcie wewnętrznej.  
  
-   Użytkownicy musi mieć możliwość interakcji z formantów za pomocą klawiatury. albo poprzez aktywowanie edytora i klawisza TAB przez formanty lub przy użyciu standardowych klawiszy skrótu.  
  
-   Projektant należy używać typowe zapisać modelu. Nie przyciski zatwierdzania lub Zapisz ogólną powinna zostać umieszczona na powierzchni, mimo że odpowiednie może być inne przyciski.  
  
#### <a name="model-designers"></a>Projektanci modelu  
  
-   Pusty projektanta powinien mieć znaku wodnego na powierzchni wskazująca, jak rozpocząć pracę.  
  
-   Dodawanie elementów do powierzchni projektowej ma się odbywać za pośrednictwem przybornika.  
  
-   Elementy na powierzchni są zgodne z modelu spójne zaznaczenia.  
  
-   Paski narzędzi osadzony zawierać poleceń specyficznych dla dokumentu tylko, nie Typowe polecenia, takich jak **zapisać**.  
  
-   Legenda może pojawić się na powierzchni świadczy lub a znaku wodnego.  
  
-   Użytkownik musi mieć możliwość dostosowania wyglądu czcionki kolorów przy użyciu **Narzędzia > Opcje** strony udostępnionym czcionki i kolory lub jeden specyficzne dla edytora.  
  
#### <a name="reports"></a>Raporty  
  
-   Raporty są zwykle tylko do informacji i nie brać udziału w modelu Zapisz. Jednak mogą one obejmować interakcji, takie jak łącza do innych istotnych informacji lub sekcje, które rozwijanie i zwijanie.  
  
-   Większość używanych poleceń na powierzchni powinna być hiperłącza, nie przycisków.  
  
-   Układ powinien zawierać nagłówek i postępuj zgodnie z wytycznymi układ raportu standardowego.  
  
#### <a name="dashboards"></a>Pulpity nawigacyjne  
  
-   Pulpity nawigacyjne nie ma modelu interakcji samodzielnie, ale służyć jako metoda oferowanie różnych innych narzędzi.  
  
-   Nie bierz udziału w modelu Zapisz.  
  
-   Użytkownicy musi mieć możliwość interakcji z formantów przy użyciu klawiatury, aktywacja edytora i TAB formantów lub przy użyciu standardowych klawiszy skrótu.  
  
##  <a name="BKMK_Dialogs"></a>Okna dialogowe  
  
### <a name="introduction"></a>Wprowadzenie  
Okien dialogowych w programie Visual Studio zwykle powinny obsługiwać osobne jednostki pracy użytkownika, a następnie odrzucone.  
  
Jeśli określono, że należy okna dialogowego, wyświetlane są trzy opcje, w kolejności priorytetu:  
  
1.  Włączenie funkcje do jednego z udostępnionego okien dialogowych w programie Visual Studio.  
  
2.  Utwórz własne okna dialogowego za pomocą wzorca w istniejących podobne okna dialogowego.  
  
3.  Utwórz nowe okno dialogowe, następująca interakcja i wskazówki układu.  
  
W tej sekcji opisano, jak wybierz wzorzec okna dialogowego prawidłowe w przepływach pracy programu Visual Studio i typowych konwersji dla okna dialogowego projektu.  
  
### <a name="themes"></a>Motywy  
Okna dialogowe w programie Visual Studio, wykonaj jedną z dwóch podstawowych style:  
  
#### <a name="standard-unthemed"></a>Standard (unthemed)  
Większość okien dialogowych są standardowe narzędzie okien dialogowych i powinny być unthemed. Nie nie szablonu ponowna formantów wspólnych lub próba utworzenia stylizowane przyciski "nowoczesnych" lub kontrolki. Formanty i wyglądu chrome wykonaj [standardowych wytycznych interakcji z pulpitu systemu Windows dla okien dialogowych](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Motywów  
Specjalizacja "podpisu" może być motywów. Okna dialogowe motywów ma charakterystyczny wygląd ma również pewne wzorce specjalne interakcji skojarzone z styl. Motyw Twoje okno dialogowe tylko wtedy, gdy spełnia następujące wymagania:  
  
-   Okno dialogowe jest wspólne środowisko, które będą widoczne i używany często ani przez wielu użytkowników (na przykład **nowy projekt** okna dialogowego.  
  
-   Okno dialogowe zawiera elementy marki poświęcone produktu (na przykład **ustawienia konta** okna dialogowego).  
  
-   Wyświetli się okno dialogowe jako integralną częścią większej przepływ, który zawiera inne motywem okien dialogowych (na przykład **dodać podłączonej usługi** okna dialogowego).  
  
-   Okno dialogowe jest ważnym elementem funkcjonalność, która pełni rolę strategicznych w podwyższania lub rozróżnianie wersji produktu.  
  
Podczas tworzenia motywów okna dialogowego, Użyj kolorów środowisko i wykonaj poprawne układ i wzorce interakcji. (Zobacz [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Okno dialogowe projektu  
Dobrze zaprojektowanego okien dialogowych należy wziąć pod uwagę następujące elementy:  
  
-   Zadanie użytkownika jest obsługiwane  
  
-   Okno dialogowe Styl tekstu, język i terminologia  
  
-   Formant wyboru i konwencje związane z interfejsu użytkownika  
  
-   Wyrównanie układu wizualnego specyfikacji i kontrola  
  
-   Dostęp za pomocą klawiatury  
  
#### <a name="content-organization"></a>Organizowanie zawartości  
Należy wziąć pod uwagę różnice między te podstawowe typy okien dialogowych:  
  
-   [Okna dialogowe proste](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) przedstawia kontrolek w jednym oknie modalne. Prezentacja może obejmować zmian wzorce złożone kontroli, jak również selektor pól lub pasku ikon.  
  
-   [Warstwie okien dialogowych](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) służą do w pełni wykorzystać ekranu nieruchomości gdy pojedynczy interfejs użytkownika zawiera wiele grup formantów. Grupowania w oknie dialogowym są "warstwie" za pomocą formantów karty, kontrolki listy lub przycisków, dzięki czemu użytkownik może zadecydować, aby wyświetlić w danej chwili grupowania.  
  
-   [Kreatorzy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) są przydatne w przypadku kierowanie użytkownika za pomocą logicznej sekwencji kroki do wykonania zadania. Szereg opcji są oferowane w kolejnych panele, czasami wprowadzenie różnych przepływów pracy ("gałęzie") zależy od wyboru dokonanego w poprzednim panelu.  
  
####  <a name="BKMK_SimpleDialogs"></a>Proste okien dialogowych  
Proste okno dialogowe jest prezentacji kontrolek w jednym oknie modalne. Ta prezentacja może obejmować zmian sterowania złożonego wzorców, takich jak selektor pól. W oknach dialogowych proste wykonaj standardowe ogólny układ, a także wszystkie określone układu wymagane do grupowania sterowania złożonego.
  
![> Utwórz silnej nazwy klucza jest przykład prostego okna dialogowego w programie Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 01_CreateStrongNameKey")<br />Tworzenie silnej nazwy klucza jest przykład prostego okna dialogowego w programie Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a>Okna dialogowe warstwowej  
Warstwowego okien dialogowych obejmują karty, pulpity nawigacyjne i osadzone drzewa. Są one używane w celu zmaksymalizowania wykorzystania nieruchomości, gdy istnieje wiele grup formantów w elementu interfejsu użytkownika. Grupowania są warstwie, dzięki czemu użytkownik może wybrać grupowania można wyświetlić w dowolnym momencie.  
  
W przypadku najbardziej oczywistym mechanizm przełączanie między grupowania jest formant karty. Brak dostępnych kilka rozwiązań alternatywnych. Zobacz Ustawianie priorytetów i tworzenie warstw sposobu wybierz najbardziej odpowiedni styl.  
  
**Narzędzia &gt; opcje** okno dialogowe jest przykładem warstwowego okna dialogowego za pomocą osadzonych drzewa:  
  
![Narzędzia > Opcje jest przykładem warstwowego okna dialogowego w programie Visual Studio. ] (../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 02_ToolsOptions")<br />Narzędzia > Opcje jest przykładem warstwowego okna dialogowego w programie Visual Studio.
  
####  <a name="BKMK_Wizards"></a>Kreatorzy  
Kreatorzy są przydatne w przypadku kierowanie użytkownika za pomocą logicznej sekwencji kroków w celu wykonania zadania. Szereg opcji dostępnych w kolejnych panele, a użytkownik należy kontynuować za pomocą danego kroku przed przejściem do następnego. Gdy dostępne są wystarczające domyślne **Zakończ** przycisk jest aktywny.  
  
 Modalne kreatorzy są używane do zadań które:  
  
-   Zawiera rozgałęzianie, w którym różne ścieżki są oferowane w zależności od opcji użytkownika  
  
-   Zawierają zależności między krokami, gdzie kolejne kroki zależą od poprzedniego następujące dane wejściowe użytkownika  
  
-   Są dostatecznie złożone, że interfejs użytkownika mają być używane do opcji oferowanych i możliwych wartości w każdym kroku  
  
-   Jest transakcyjna, wymagających zestaw kroków, które należy wykonać w całości przed wszelkie zmiany zostaną zatwierdzone  
  
### <a name="common-conventions"></a>Typowych konwersji  
Aby osiągnąć optymalną i funkcjonalność z okna dialogowe, wykonaj te konwencje na rozmiar okna dialogowego, pozycji, standardy, konfiguracji kontroli i wyrównania, interfejsu użytkownika tekstu, pasków tytułu, przyciski sterowania i klucze dostępu.  
  
Aby uzyskać wskazówki dotyczące układu, zobacz [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Rozmiar  
Okna dialogowe powinien mieścić się w minimalna rozdzielczość ekranu 1024 x 768, a rozmiar okna dialogowego początkowy nie może przekraczać 900 x 700 pikseli. Okna dialogowe może być o zmiennym rozmiarze, ale nie jest wymagane.  
  
Istnieją dwa zalecenia w oknach dialogowych o zmiennym rozmiarze:  
  
1.  Minimalny rozmiar jest zdefiniowany dla okna dialogowego Optymalizuj dla zestaw kontroli bez przycinania, a Dostosuj, aby zmieścił się w lokalizacji uzasadnione wzrostu.  
  
2.  Czy rozmiar skalowania użytkownika się między sesjami. Na przykład jeśli użytkownik skaluje okna dialogowego do 150%, kolejnym uruchomieniu okna dialogowego zostaną wyświetlone na 150%.  
  
#### <a name="position"></a>Pozycja  
Okna dialogowe musi występować wyśrodkowany w środowisku IDE przy pierwszym uruchomieniu. Ostatniej pozycji bez zmienny rozmiar okna dialogowe nie musi zostać utrwalony, zostaną one wyświetlone wyśrodkowane na kolejnych powoduje uruchomienie. 

W oknach dialogowych o zmiennych rozmiarach rozmiar powinny zostać utrwalony na kolejnych powoduje uruchomienie. Dla dialogów modalnych o zmiennych rozmiarach pozycja nie musi zostać utrwalony. Wyświetlanie ich wyśrodkowany w IDE uniemożliwia okna dialogowego pojawia się w pozycji nieprzewidywalne lub niezdatna do użycia, gdy zmieniła się konfiguracja wyświetlania użytkownika. 

Dla Niemodalne okna dialogowe, które można zmienić ich pozycji pozycji użytkownika należy utrzymywać na kolejnych uruchomiony jako okno dialogowe może często używane w ramach większych przepływu pracy.  
  
Gdy okien dialogowych musi zduplikować innych oknach dialogowych, znajdujących się na górze okna dialogowego powinna Kaskadowo w prawo i w dół od elementu nadrzędnego, tak że jego oczywiste dla użytkownika, którego zostały one przejście do nowego miejsca.  
  
#### <a name="modality"></a>Modalność  
Trwa modalne oznacza, że użytkownicy są wymagane, aby ukończyć lub anulować okna dialogowego przed kontynuowaniem. Ponieważ modalne okna dialogowe Zablokuj użytkownikowi interakcji z innymi składnikami środowiska, przepływ zadań z funkcji powinny być używane jako oszczędnie, jak to możliwe. Gdy modalne jest niezbędne, Visual Studio ma liczbą udostępnionego okien dialogowych, którą można zintegrować funkcje do. Jeśli musisz utworzyć nowe okno dialogowe, oparte na wzorcu interakcji istniejącego okna dialogowego o podobnych możliwościach.  
  
Gdy użytkownicy muszą wykonać jednocześnie dwóch działań, takich jak **znaleźć** i **Zastąp** podczas zapisywania nowego kodu, okno dialogowe powinna być niemodalne, dzięki czemu użytkownik może łatwo przełączać się między nimi. Visual Studio będzie korzystać zazwyczaj okien narzędzi dla tego rodzaju obsługi edytora połączonego zadania.  
  
#### <a name="control-configuration"></a>Konfiguracja kontroli  
Być zgodne z istniejącej konfiguracji kontroli, które osiągnąć ten sam efekt w Visual Studio.  
  
#### <a name="title-bars"></a>Paski tytułu  
  
-   Tekst w pasku tytułu musi odzwierciedlać nazwa polecenia, który go uruchomić.  
  
-   Ikona nie należy używać w paski tytułu okna dialogowego. W przypadkach, gdy system wymaga jednego Użyj logo programu Visual Studio.  
  
-   Okna dialogowe nie powinny mieć minimalizowanie lub maksymalizowanie przycisków.  
  
-   Przyciski pomocy na pasku tytułu są przestarzałe. Nie należy dodawać je do nowego okna dialogowe. Gdy istnieją one powinien uruchamiać tematu pomocy, który jest koncepcyjnie odpowiednie do zadania.  
  
 ![Specyfikacje wytyczne dla pasków tytułu w oknach dialogowych programu Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 03_TitleBarSpecs")<br />Specyfikacje wytyczne dla pasków tytułu w oknach dialogowych programu Visual Studio
  
#### <a name="control-buttons"></a>Kontrolki przycisków  
Ogólnie rzecz biorąc **OK**, **anulować**, i **pomocy** przyciski powinny być ułożone poziomo w prawym dolnym rogu okna dialogowego. Alternatywne stosu pionowe jest dozwolone, gdy okno dialogowe ma kilka przycisków w dolnej części okna dialogowego, który przedstawia visual pomylenia z przycisków kontrolki.  
  
![Dopuszczalne konfiguracje dla kontrolki przycisków w oknach dialogowych programu Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 04_ControlButtonConfig")<br />Dopuszczalne konfiguracje dla kontrolki przycisków w oknach dialogowych programu Visual Studio
  
Okno dialogowe musi zawierać domyślnego formantu przycisku. Aby określić najlepsze polecenie, aby użyć domyślnej, wybierz jedną z następujących opcji (wymienione w kolejności):  
  
-   Wybierz polecenie najbezpieczniejszy i najbardziej bezpieczne jako domyślny. Oznacza to, wybranie najbardziej prawdopodobne zapobiec utracie danych i uniknąć dostępu do systemu niezamierzone polecenia.  
  
-   Jeśli utratą danych i zabezpieczeń nie czynników, należy wybrać polecenie domyślny, w oparciu o wygody. Tym najprawdopodobniej polecenie domyślnie zwiększy przepływu pracy użytkownika, gdy okno dialogowe obsługuje częste lub powtarzających się zadań.  
  
Unikaj trwale destrukcyjnego akcji dla polecenia domyślny wybór. Jeśli takie polecenie jest obecny, wybierz polecenie bezpieczniejsze jako domyślny.  
  
#### <a name="access-keys"></a>Klawisze dostępu  
Nie używaj klawiszy dostępu dla **OK**, **anulować**, lub **pomocy** przycisków. Przyciski te są mapowane na klawiszy skrótu domyślnie:  
  
| Nazwa przycisku | Skrót klawiaturowy |  
| --- | --- |  
| OK | Enter |  
| Anuluj | Esc |  
| Pomoc | F1 |  
  
#### <a name="imagery"></a>Obrazów  
Oszczędne używać obrazów w oknach dialogowych. Nie używaj duże ikony w oknach dialogowych jedynie w celu użycia miejsca. Obrazy należy używać tylko wtedy, gdy są one ważnym przekazywania wiadomości dla użytkownika, takich jak ikon ostrzeżenie lub stan animacji.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a>Określanie priorytetu i Układanie warstwowo  
  
#### <a name="prioritizing-your-ui"></a>Określanie priorytetu interfejsu użytkownika  
Może być konieczne wyświetlić niektórych elementów interfejsu użytkownika programu forefront i umieścić bardziej zaawansowanych zachowanie i (w tym polecenia zasłoniętej) opcje w oknach dialogowych. Przełącz najczęściej używane funkcje programu forefront, tworząc miejsca i czyniąc ją widoczne domyślnie w Interfejsie użytkownika etykietę tekstową, gdy okno dialogowe jest wyświetlane.  
  
#### <a name="layering-your-ui"></a>Układanie warstwowo interfejsu użytkownika  
Jeśli już wiesz, czy okno dialogowe jest konieczne, ale związanych z nimi funkcji, które mają być przedstawiane użytkownikowi wykracza poza mogą być wyświetlane w oknie dialogowym prostego, następnie należy do warstwy interfejsu użytkownika. Najbardziej typowe metody Tworzenie warstw, które korzysta z programu Visual Studio są karty i hallways lub pulpitów nawigacyjnych. W niektórych przypadkach może być odpowiednie regionów, które można zwijać i rozwijać. Ogólnie rzecz biorąc adaptacyjną interfejsu użytkownika nie jest zalecane w programie Visual Studio.  
  
Brak zalety i wady różnych metod Układanie warstwowo interfejsu użytkownika za pomocą formantów typu karta. Zapoznaj się z listą poniżej, aby zapewnić wybierania metody warstwy, która jest odpowiednia w danej sytuacji.  
  
##### <a name="tabbing"></a>Klawisza TAB  
  
| Mechanizm przełączania | Korzyści i zastosowania | Wady i nieodpowiednie użycie |  
| --- | --- | --- |  
| Formantu karty | Logicznie grupują strony okna dialogowego w zestawy pokrewne<br /><br />Przydatne w przypadku mniej niż 5 (lub liczba kart, które mieszczą się w jednym wierszu w oknie dialogowym) stron pokrewnych formantów w oknie dialogowym<br /><br />Karta etykiety musi być krótka: jeden lub dwa wyrazy, które można łatwo zidentyfikować zawartości<br /><br />Typowe styl okna dialogowego systemu<br /><br />Przykład: **pliku Explorer &gt; właściwości elementów** | Tworzenie etykiety krótki opis może być trudne<br /><br />Zazwyczaj nie skalowania poza pięć kart w jednym oknie dialogowym<br /><br />Nieodpowiednie, jeśli masz zbyt wiele kart jednego wiersza (Użyj technikę alternatywnych warstwy)<br /><br />Nie rozszerzonego |  
| Pasek boczny nawigacji | Proste przełączania urządzenia, które może obsłużyć więcej kategorii niż karty<br /><br />Płaska lista kategorii (żadna hierarchia)<br /><br />Rozszerzalny<br /><br />Przykład: **dostosować... &gt;Dodaj polecenie** | Nie dobre wykorzystanie miejsca w poziomie, jeśli ma mniej niż trzech grup<br /><br />Zadania mogą być lepiej dostosowane do listy rozwijanej |  
| Formant drzewa | Umożliwia nieograniczone kategorii<br /><br />Umożliwia grupowanie i/lub hierarchia kategorii<br /><br />Rozszerzalny<br /><br />Przykład: **narzędzia &gt; opcje** | Wielokrotnie zagnieżdżone hierarchie może spowodować nadmierne przewijanie w poziomie<br /><br />Visual Studio ma overabundance widok drzewa |  
| Kreator | Ułatwia przeprowadzi użytkownika przez kroki zadań, kolejny przez zadanie zostało zakończone: Kreator przedstawia zadania wysokiego poziomu i poszczególnych paneli reprezentują podzadania potrzebne do wykonania zadania ogólnej<br /><br />Przydatne w przypadku zadania przecina granice interfejsu użytkownika, jak kiedy użytkownik w przeciwnym razie musi użycie wiele edytorów i narzędzia systemu windows do ukończenia tego zadania<br /><br />Przydatne, gdy zadanie wymaga rozgałęzianie<br /><br />Przydatne w przypadku zadania zawiera zależności między krokami<br /><br />Przydatne w przypadku kilku podobne zadania związane z rozwidlenia decyzji co może być prezentowana w jedno okno, aby zmniejszyć liczbę różnych podobne okien dialogowych | Nieodpowiednie dla dowolnego zadania, które nie wymagają sekwencyjnego przepływu pracy<br /><br />Użytkownicy mogą stać się zalewowi i mylić przez kreatora bez zbyt wiele kroków<br /><br />Kreatorzy z założenia mają ograniczoną nieruchomości ekranu |  
  
##### <a name="hallways-or-dashboards"></a>Hallways lub pulpitów nawigacyjnych  
Hallways i pulpity nawigacyjne są okien dialogowych lub panele, które stanowią uruchamianie punktów do innych okien dialogowych i systemu windows. Dobrze zaprojektowanego "korytarz" natychmiast udostępnia tylko najbardziej typowe opcje, poleceń i ustawień, co pozwala na łatwe wykonywanie typowych zadań. Jak Korytarz rzeczywistych udostępnia drzwi do dostęp do pomieszczenia za ich, w tym miejscu mniej wspólnego interfejsu użytkownika są zbierane do oddzielnych "pomieszczeń" (często innych okien dialogowych) powiązanych funkcji, które są dostępne z głównym korytarz.  
  
Alternatywnie interfejsu użytkownika, który oferuje wszystkie funkcje dostępne w jednej kolekcji, a nie refaktoryzacji mniej typowe funkcje w różnych lokalizacjach jest po prostu pulpitu nawigacyjnego.  
  
![Koncepcja korytarz udostępnianie dodatkowy interfejs użytkownika w programie Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 08_Hallway")<br />Koncepcja korytarz udostępnianie dodatkowy interfejs użytkownika w programie Outlook
  
##### <a name="adaptive-ui"></a>Adaptacyjną interfejsu użytkownika  
Wyświetlenie lub ukrycie interfejsu użytkownika na podstawie użycia lub komputera własnym zgłoszonego przez użytkownika jest innego sposobu prezentowania niezbędne interfejsu użytkownika innych części są ukryte. Nie jest to zalecane w programie Visual Studio, jako algorytmów dotyczących decydowania, kiedy do wyświetlenia lub ukrycia interfejsu użytkownika mogą być istotne znaczenie, a zasady zawsze będą nieprawidłowe dla niektórych zestawu przypadków.  
  
##  <a name="BKMK_Projects"></a>Projekty  
  
### <a name="projects-in-the-solution-explorer"></a>Projekty w Eksploratorze rozwiązań  
Większości projektów sklasyfikowanych jako odwołania na, opartych na katalogu lub mieszane. Wszystkie trzy projekty są obsługiwane jednocześnie w Eksploratorze rozwiązań. Katalog główny środowiska użytkownika w pracy z projektami odbywa się w tym oknie. Chociaż inny projekt węzły są odwołania, katalog lub projektów typu trybu mieszanego, Brak wspólnego wzorca interakcji, który ma zostać zastosowany jako punkt początkowy przed rozbieżności do wzorców użytkownika określonego projektu.  
  
Projekty powinny zawsze:  
  
-   Obsługuje możliwość dodawania foldery projektu, aby zorganizować zawartość projektu  
  
-   Obsługa spójny model trwałości projektu  
  
Projekty powinny również Obsługa modeli spójne interakcji dla:  
  
-   Usuwanie elementów projektu  
  
-   Zapisywanie dokumentów  
  
-   Edycja właściwości projektu  
  
-   Edytowanie projektu w widoku alternatywnym  
  
-   Operacje przeciągania i upuszczania  
  
### <a name="drag-and-drop-interaction-model"></a>Przeciągnij i upuść modelu  
Projekty zwykle klasyfikowania się jako odwołanie na podstawie (może pozostać tylko odwołania do elementów projektu w magazynie), katalog na podstawie (może pozostać tylko elementy projektu fizycznie przechowywane w hierarchii projektu), lub mixed (możliwe do utrwalenia odwołań lub elementów fizycznych). IDE bierze pod uwagę wszystkie trzy projekty jednocześnie poziomu **Eksploratora rozwiązań**.  
  
Z punktu widzenia przeciągania i upuszczania stosuje następujące właściwości dla każdego typu projektu w ramach **Eksploratora rozwiązań**:  
  
-   **Odwołanie do projektu:** klucza punkt jest, że projekt jest przeciąganie wokół odwołanie do elementu w magazynie. Gdy odwołanie do projektu działa jako źródło dla operacji przenoszenia, go tylko należy usunąć odwołanie do elementu z projektu. Element nie powinien rzeczywiście można usunąć z dysku twardego. Gdy odwołanie do projektu działa jako obiekt docelowy operacji przenoszenia (lub kopiowania), jego należy dodać odwołania do oryginalnego elementu źródłowego bez wprowadzania prywatnej kopii elementu.  
  
-   **Na podstawie katalogu projektu:** z punktu widzenia przeciągania i upuszczania, przeciąga wokół elementu fizycznego zamiast odwołania projektu. Katalog projektu działa jako źródło dla operacji przenoszenia, powinien kończyć się usunięcie elementu fizycznego z dysku twardego, a także usunięcie go z projektu. Jeśli projekt na podstawie katalogu działa jako obiekt docelowy operacji przenoszenia (lub kopiowania), go utworzyć kopię elementu źródłowego, w lokalizacji docelowej.  
  
-   **Mieszane docelowy projekt:** z punktu widzenia przeciągania i upuszczania, zachowanie tego typu projektu jest oparta na rodzaj elementu przeciąganie (odwołanie do elementu w magazynie) albo elementu. Poprawne zachowanie elementów fizycznych i odwołań opisanych powyżej.  
  
Gdyby tylko jeden typ projektu w **Eksploratora rozwiązań**, a następnie operacji przeciągania i upuszczania jest proste. Ponieważ każdy system projektu ma możliwość definiowania zachowania przeciągania i upuszczania, niektórych wytycznych (oparte na zachowanie przeciąganie i upuszczanie Eksploratora Windows), należy wykonać zapewnienie przewidywalnie obsługiwać użytkowników:  
  
-   Zmodyfikowane operacji przeciągania **Eksploratora rozwiązań** (gdy klawisze Shift ani Ctrl są przechowywane w dół) powinno dawać wynik operacji przenoszenia.  
  
-   Operacja przeciągania SHIFT również powinno spowodować operacji przenoszenia.  
  
-   CTRL i przeciągnij działanie powinno spowodować operacji kopiowania.  
  
-   Projektu odwołanie i mieszane systemy pojęcia Dodawanie link (lub odwołania) do elementu źródłowego. Kiedy te projekty są obiekt docelowy operacji przeciągania i upuszczania (gdy **klawisze Ctrl + Shift** przytrzymanie), powinno spowodować odwołanie do element dodawany do projektu  
  
Nie wszystkie operacje przeciągania i upuszczania są za pośrednictwem przez kombinacje, projektów odwołania na podstawie katalogu i mieszanych. W szczególności stanowi problem można podawać Zezwalaj operacji przenoszenia między projektu na podstawie katalogu źródłowego i docelowego na podstawie odwołania projektu, ponieważ projekt na podstawie katalogu źródłowego, należy usunąć elementu źródłowego po zakończeniu przenoszenia. Następnie pojawiłyby projektu docelowego odwołania na odwołanie do usuniętego elementu.  
  
Jest również mylących można podawać umożliwia kopiowanie między tymi typami projektów, ponieważ docelowy projekt odwołanie, nie należy wprowadzać niezależne kopię elementu źródłowego. Podobnie Ctrl + Shift, przeciągając do projektu na podstawie katalog docelowy nie powinien być dozwolony ponieważ nie można utrwalić odwołuje się do katalogu projektu. W przypadkach, gdy operacja przeciągania i upuszczania nie jest obsługiwana IDE należy uniemożliwić listy i wyświetlane użytkownikowi kursora nie upuść (przedstawione w poniższej tabeli wskaźnika).  
  
Aby prawidłowo zaimplementować zachowanie przeciągania i upuszczania, projekt źródłowy przeciągania musi nawiązać komunikację natury do projektu docelowego. (Na przykład, jest on opartych na odwołania lub katalogu?) Te informacje jest określane przez oferowaną przez źródło formatu Schowka. Jako źródła przeciągania (lub operacji kopiowania Schowka) projektu powinno oferować albo `CF_VSREFPROJECTITEMS` lub `CF_VSSTGPROJECTITEMS` , w zależności od tego, czy projekt jest oparte na odwołania lub na podstawie katalogu. Z tych formatów mają tę samą zawartość danych, który jest podobny do systemu Windows `CF_HDROP` formatowania, z wyjątkiem, że listy ciągów, zamiast nazw plików, są o podwójnej precyzji —`NULL` zakończone lista `Projref` ciągów (zwrócony z `IVsSolution::GetProjrefOfItem`lub `::GetProjrefOfProject` odpowiednio).  
  
Jako element docelowy upuszczania (lub operacji wklejania Schowka) projektu powinien zaakceptować oba te `CF_VSREFPROJECTITEMS` i `CF_VSSTGPROJECTITEMS`, ale dokładne obsługi operacji przeciągania i upuszczania różni się w zależności od rodzaju projektu docelowego projektu źródłowego. Projekt źródłowy deklaruje natury, czy oferuje `CF_VSREFPROJECTITEMS` lub `CF_VSSTGPROJECTITEMS`. Element docelowy upuszczania rozumie własną charakter i w związku z tym ma za mało informacji w podejmowaniu decyzji co do, czy przenoszenia, kopiowania lub łącza, które powinny być wykonywane. Użytkownik modyfikuje również operacji przeciągania i upuszczania, które należy wykonać, naciskając klawisz Ctrl, Shift, lub zarówno klawiszy Ctrl i Shift. Ważne jest, aby element docelowy upuszczania prawidłowo wskazująca, które będzie można wykonać operacji, wcześniej w jego `DragEnter` i `DragOver` metody. **Eksploratora rozwiązań** automatycznie wykrywa, czy projekt źródłowy i docelowy projekt są tego samego projektu.  
  
Przeciąganie elementów projektu w wystąpieniach programu Visual Studio (na przykład z jednego wystąpienia devenv.exe do innego) w szczególności nie jest obsługiwane. **Eksploratora rozwiązań** bezpośredni wyłącza to.  
  
Użytkownik zawsze może być możliwe ustalenie wpływ operacji przeciągania i upuszczania, wybierając element, przeciągając go do lokalizacji docelowej i przestrzegając następujących wskaźników myszy widocznego przed element zostanie porzucony:  
  
| Wskaźnik myszy | Polecenie | Opis |  
| :---: | --- | --- |  
| ![Myszy ikonę "nie listy"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | Nie listy | Nie można usunąć elementu do określonej lokalizacji. |  
| ![Ikona "Kopiuj" myszy](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 02_MouseCopy") | Kopiuj | Element zostaną skopiowane do lokalizacji docelowej. |  
| ![Ikona myszy "move"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | Przenieś | Element zostanie przeniesiony do lokalizacji docelowej. |  
| ![Ikona "Dodaj odwołanie" myszy](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | Dodaj odwołanie | Odwołanie do wybrany element zostanie dodany do lokalizacji docelowej. |

#### <a name="reference-based-projects"></a>Projekty oparte na odwołanie  
 Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także Wycinanie/kopiowanie/wklejanie), które należy wykonać w oparciu o charakter klucze elementów i modyfikator źródła naciśnięto dla projektów opartych na odwołanie do docelowych:  
  
| Modyfikator | Kategoria | Element źródłowy: odwołanie/Link | Element źródłowy: element lub plików systemowych (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Nie modyfikatora | Akcja | Przenieś | Łącze |  
| Nie modyfikatora | docelowy | Dodaje odwołanie do elementu | Dodaje odwołanie do elementu |  
| Nie modyfikatora | Źródło | Usuwa odwołania do oryginalnego elementu | Zachowuje oryginalnego elementu |  
| Nie modyfikatora | Wynik | `DROPEFFECT_MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |  
| SHIFT + przeciągania | Akcja | Przenieś | Nie listy |  
| SHIFT + przeciągania | docelowy | Dodaje odwołanie do elementu | Nie listy |  
| SHIFT + przeciągania | Źródło | Usuwa odwołania do oryginalnego elementu | Nie listy |  
| SHIFT + przeciągania | Wynik | `DROPEFFECT_MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | Nie listy |  
| CTRL + przeciągania | Akcja | Kopiuj | Nie listy |  
| CTRL + przeciągania | docelowy | Dodaje odwołanie do elementu | Nie listy |  
| CTRL + przeciągania | Źródło | Zachowuje odwołania do oryginalnego elementu | Nie listy |  
| CTRL + przeciągania | Wynik | `DROPEFFECT_COPY`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | Nie listy |  
| Ctrl + Shift + przeciągania | Akcja | Łącze | Łącze |  
| Ctrl + Shift + przeciągania | docelowy | Dodaje odwołanie do elementu | Dodaje odwołanie do elementu |  
| Ctrl + Shift + przeciągania | Źródło | Zachowuje odwołania do oryginalnego elementu | Zachowuje oryginalnego elementu |  
| Ctrl + Shift + przeciągania | Wynik | `DROPEFFECT_LINK`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_LINK`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |  
| Ctrl + Shift + przeciągania | Uwaga | Taka sama jak zachowanie przeciągania i upuszczania skróty w Eksploratorze Windows. ||  
| Wycinanie i wklejanie | Akcja | Przenieś | Łącze |  
| Wycinanie i wklejanie | docelowy | Dodaje odwołanie do elementu | Dodaje odwołanie do elementu |  
| Wycinanie i wklejanie | Źródło | Zachowuje odwołania do oryginalnego elementu|Zachowuje oryginalnego elementu |  
| Wycinanie i wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |  
| Kopiowanie i wklejanie | Akcja | Kopiuj | Łącze |  
| Kopiowanie i wklejanie | Źródło | Dodaje odwołanie do elementu | Dodaje odwołanie do elementu |  
| Kopiowanie i wklejanie | Wynik | Zachowuje odwołania do oryginalnego elementu | Zachowuje oryginalnego elementu |  
| Kopiowanie i wklejanie | Akcja | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |  
  
#### <a name="directory-based-projects"></a>Projekty oparte na katalogu  
Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także Wycinanie/kopiowanie/wklejanie), które należy wykonać w oparciu o charakter klucze elementów i modyfikator źródła naciśnięte projekty oparte na katalog docelowy:  
  
| Modyfikator | Kategoria | Element źródłowy: odwołanie/Link | Element źródłowy: element lub plików systemowych (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Nie modyfikatora | Akcja | Przenieś | Przenieś |  
| Nie modyfikatora | docelowy | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |  
| Nie modyfikatora | Źródło | Usuwa odwołania do oryginalnego elementu | Usuwa odwołania do oryginalnego elementu | | Nie modyfikatora | Wynik | `DROPEFFECT_MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |  
| SHIFT + przeciągania | Akcja | Przenieś | Przenieś |  
| SHIFT + przeciągania | docelowy | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |  
| SHIFT + przeciągania | Źródło | Usuwa odwołania do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| SHIFT + przeciągania | Wynik | `DROPEFFECT_MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |  
| CTRL + przeciągania | Akcja | Kopiuj | Kopiuj |  
| CTRL + przeciągania | docelowy | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |  
| CTRL + przeciągania | Źródło | Zachowuje odwołania do oryginalnego elementu | Zachowuje odwołania do oryginalnego elementu |  
| CTRL + przeciągania | Wynik | `DROPEFFECT_COPY`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_COPY`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |  
| Ctrl + Shift + przeciągania | | Nie listy | Nie listy |  
| Wycinanie i wklejanie | Akcja | Przenieś | Przenieś |  
| Wycinanie i wklejanie | docelowy | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |  
| Wycinanie i wklejanie | Źródło | Usuwa odwołania do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |  
| Wycinanie i wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element zostanie usunięty z oryginalnej lokalizacji w magazynie |  
| Kopiowanie i wklejanie | Akcja | Kopiuj | Kopiuj |  
| Kopiowanie i wklejanie | docelowy | Dodaje odwołanie do elementu | Kopiuje element do lokalizacji docelowej |  
| Kopiowanie i wklejanie | Źródło | Zachowuje oryginalnego elementu | Zachowuje oryginalnego elementu |  
| Kopiowanie i wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji ins magazynu |
  
#### <a name="mixed-target-projects"></a>Projektów docelowych mieszany  
Poniższa tabela zawiera podsumowanie operacji przeciągania i upuszczania (a także Wycinanie/kopiowanie/wklejanie), które należy wykonać w oparciu o charakter klucze elementów i modyfikator źródła naciśnięto dla projektów mieszanym docelowych:  
  
| Modyfikator | Kategoria | Element źródłowy: odwołanie/Link | Element źródłowy: element lub plików systemowych (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Nie modyfikatora | Akcja | Przenieś | Przenieś |
| Nie modyfikatora | docelowy | Dodaje odwołanie do elementu | Kopiuje element do lokalizacji docelowej |
| Nie modyfikatora | Źródło | Usuwa odwołania do oryginalnego elementu | Usuwa odwołania do oryginalnego elementu |
| Nie modyfikatora | Wynik | `DROPEFFECT_ MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE`jest zwracana jako akcja `::Drop` i elementu zostaną usunięte z oryginalnej lokalizacji w magazynie |
| SHIFT + przeciągania | Akcja | Przenieś | Przenieś |
| SHIFT + przeciągania | docelowy | Dodaje odwołanie do elementu | Kopiuje element do lokalizacji docelowej |
| SHIFT + przeciągania | Źródło | Usuwa odwołania do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji | 
| SHIFT + przeciągania | Wynik | `DROPEFFECT_ MOVE`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ MOVE`jest zwracana jako akcja `::Drop` i elementu zostaną usunięte z oryginalnej lokalizacji w magazynie |
| CTRL + przeciągania | Akcja | Kopiuj | Kopiuj |
| CTRL + przeciągania | docelowy | Dodaje odwołanie do elementu | Kopiuje element do lokalizacji docelowej |
| CTRL + przeciągania | Źródło | Zachowuje odwołania do oryginalnego elementu | Zachowuje oryginalnego elementu |
| CTRL + przeciągania | Wynik | `DROPEFFECT_ COPY`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ COPY`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| Ctrl + Shift + przeciągania | Akcja | Łącze | Łącze |
| Ctrl + Shift + przeciągania | docelowy | Dodaje odwołanie do elementu | Dodaje odwołanie do oryginalnego elementu źródłowego |
| Ctrl + Shift + przeciągania | Źródło | Zachowuje odwołania do oryginalnego elementu | Zachowuje oryginalnego elementu |
| Ctrl + Shift + przeciągania | Wynik | `DROPEFFECT_ LINK`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie | `DROPEFFECT_ LINK`jest zwracana jako akcja `::Drop` i element pozostaje w oryginalnej lokalizacji w magazynie |
| Wycinanie i wklejanie | Akcja | Przenieś | Przenieś |
| Wycinanie i wklejanie | docelowy | Kopiuje element do lokalizacji docelowej | Kopiuje element do lokalizacji docelowej |
| Wycinanie i wklejanie | Źródło | Usuwa odwołania do oryginalnego elementu | Usuwa element z oryginalnej lokalizacji |
| Wycinanie i wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element zostanie usunięty z oryginalnej lokalizacji w magazynie |
| Kopiowanie i wklejanie | Akcja | Kopiuj | Kopiuj |
| Kopiowanie i wklejanie | docelowy | Dodaje odwołanie do elementu | Kopiuje element do lokalizacji docelowej |
| Kopiowanie i wklejanie | Źródło | Zachowuje oryginalnego elementu | Zachowuje oryginalnego elementu |
| Kopiowanie i wklejanie | Wynik | Element pozostaje w oryginalnej lokalizacji w magazynie | Element pozostaje w oryginalnej lokalizacji w magazynie |
  
Te szczegóły należy brane pod uwagę podczas implementowania przeciąganie w **Eksploratora rozwiązań**:  
  
-   Projekt w wielu scenariuszach zaznaczenia.  
  
-   Nazwy plików (pełna ścieżka) musi być unikatowa w projekcie docelowym lub usuwania nie powinno być dozwolone.  
  
-   Nazwy folderów muszą być unikatowe (bez uwzględniania wielkości liter) na poziomie są usuwane.  
  
-   Brak zachowania różnic między plikami, które są open lub closed podczas przeciągania (niewymienione w powyższych scenariuszy).  
  
-   Pliki najwyższego poziomu zachowywać się inaczej niż plików w folderach.  
  
Inny problem, należy pamiętać o jest sposób obsługi operacji przenoszenia na elementy, które mają otwartych oknach projektantów lub edytory. Jest oczekiwane zachowanie w następujący sposób (dotyczy wszystkich typów projektów):  
  
1.  Jeśli Otwórz Edytor/projektanta nie ma żadnych niezapisanych zmian, następnie w oknie Edytor/projektant powinien zostać dyskretnie zamknięty.  
  
2.  Jeśli otwarty Edytor/projektanta mają niezapisanych zmian, następnie źródła przeciągania ma oczekiwać na docelowej i następnie poprosić użytkownika o zapisać niezatwierdzone zmiany w otwartych dokumentów przed zamknięciem okna z wiersz podobny do następującego :  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
Użytkownik daje możliwość zapisania pracy w toku, przed jego kopii sprawia, że element docelowy. Nowa metoda `IVsHierarchyDropDataSource2::OnBeforeDropNotify` został dodany do włączenia tej obsługi.  
  
Element docelowy następnie skopiuj stan elementu, ponieważ jest on w magazynie (nie tym niezapisanych zmian w edytorze, jeśli użytkownik wybrał **nr**). Po zakończeniu docelowy jego kopiowania (w `IVsHierarchyDropDataSource::Drop`), źródłowego ma możliwość wykonanie części Usuń operację przenoszenia (w `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Otwórz należy pozostawić edytory wszystkie niezapisane zmiany. Dla tych dokumentów z niezapisane zmiany to oznacza, że zostanie wykonana kopia część operacji przenoszenia, ale usunięcie części zostanie przerwana. W przypadku zaznaczenia wielu po wybraniu **nr**, dokumentów z niezapisane zmiany nie powinna być zamknięty lub usunięty, ale bez niezapisane zmiany powinny być zamknięty i usunięty.