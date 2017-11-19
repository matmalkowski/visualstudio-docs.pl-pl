---
title: Ocena Tools for Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 04a2d2c404f60712169639a73ff8d138fdd9323a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="evaluation-tools-for-visual-studio"></a>Ocena Tools for Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista kontrolna craftsmanship dla programu Visual Studio  
 Ta lista kontrolna umożliwia oceń jakość środowiska użytkownika w szczegóły visual i interakcji.  
  
### <a name="overview"></a>Omówienie  
  
-   Upewnij się, że wszystkie polecenia skutkować opinii informujący użytkowników, czy przeprowadzono ich poleceń.  
  
-   Sprawdź, czy wszystkie elementy interfejsu użytkownika i kontrolek są widoczne w wszystkie motywy oraz w trybie dużego kontrastu.  
  
-   Upewnij się, że wybór stanem nieaktywnym i aktywnym zawsze są zróżnicowane, zarówno w trybie dużego kontrastu, jak i standard.  
  
-   Sprawdź, czy fokus jest zawsze widoczne i oczywista.  
  
### <a name="performance"></a>Wydajność  
  
-   Sprawdź, czy niektóre rodzaju "zajęty" wskaźnika jest wyświetlany, jeśli polecenie ma więcej niż jednej sekundy do ukończenia.  
  
-   Sprawdź, czy polecenie ma więcej niż 10 sekund, pasek postępu jawne, albo określania (preferowane) lub nieokreślony, jest wyświetlana.  
  
### <a name="ui-text"></a>Tekst interfejsu użytkownika  
  
-   Sprawdź, czy pisownia tytułów lub zdaniu wszystkich etykiet i że nie został tekst wyłącznie małe litery.  
  
    ||Popraw|Niepoprawne|  
    |-|-------------|---------------|  
    |**Tekst polecenia, (wszystkie wersje)**|Zdaniu:<br /><br /> **Nazwa katalogu:**|Nazwa katalogu:|  
    |**Tekst przycisku (klient)**|Wielkość liter:<br /><br /> **[Ustaw jako domyślny]**|USTAW JAKO DOMYŚLNY|  
    |**Tekst przycisku (online)**|Zdaniu:<br /><br /> **Ustaw jako domyślny]**||  
  
-   Sprawdź, czy wszystkie etykiety, z wyjątkiem nagłówka grupy i przyciski, się kończyć dwukropkiem, a poprzedzać formantu, z którym są skojarzone.  
  
-   Sprawdź, czy przycisków, poleceń i łączy polecenia Uruchom interfejs użytkownika do przechwycenia danych wejściowych użytkownika kończy się wielokropek **[...]** .  
  
     Przykłady:  
  
    -   **[Zaawansowane...]**  przycisk w oknie dialogowym.  
  
    -   Opcje polecenia w menu Narzędzia (**Narzędzia > Opcje**) nie powinno być wyświetlane wielokropek, ponieważ uruchamianie się okno dialogowe jest celem polecenia.  
  
-   Sprawdź, czy interfejs użytkownika zawiera nie skrótów, oprócz standardowych warunków. Na przykład HTML ani TCP/IP muszą być pisane, chociaż za mało pamięci (mało pamięci) i dane osobowe (dane osobowe) powinny.  
  
### <a name="keyboard-access"></a>Dostęp za pomocą klawiatury  
  
-   Sprawdź, czy istnieje sposób wykonywania poszczególnych zadań za pomocą klawiatury. Zwykle odbywa się za pomocą klawiatury dostępu dla każdego formantu, ale niektóre wizualnymi obszarów jest dopuszczalne obejście, takich jak przechodzenie do widoku kodu.  
  
-   Upewnij się, że można przełączać się między formantów w logiczną kolejnością (od lewej do prawej i góry do dołu). Jest to najlepsze rozwiązanie dla większości formantów, nie wszystkie formanty wymagają tej metody. Na przykład sprawdzić tego przycisku radiowego, który formanty znajdują się w grupie z tabulatorów.  
  
-   Sprawdź, czy wszystkie formanty miały etykiety, a każda etykieta ma wartość (wyjątków należą niektóre formanty etykietą, które może skorzystać z etykietą kontrolki na karcie).  
  
-   Sprawdź, czy nie występują żadne konflikty skrótu.  
  
### <a name="fonts"></a>Czcionki  
  
-   Sprawdź, czy wszystkie czcionki (krój, rozmiar, kolor) są zawsze używane i Obsługa hierarchii.  
  
-   Sprawdź, czy wszystkie elementy interfejsu użytkownika używają środowiska usługi czcionki. (Zobacz [czcionek i formatowania dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Aby sprawdzić, czy usługa jest używana, przejdź do **Narzędzia > Opcje > czcionki i kolory**. Na liście rozwijanej Ustawienia czcionki środowiska i zmienić krój czcionki do stylistically inny (na przykład Comic sieci SAN lub Mochnacki) lub ustaw rozmiar na 12 punktów. Kliknij przycisk OK. Może być konieczne ponowne uruchomienie IDE, ale większość interfejsu użytkownika zmieni się natychmiast. Obszary, które nie należy zbierać zmiana czcionki, nawet w przypadku ponownego uruchomienia nie są przy użyciu czcionki środowiska.  
  
-   Sprawdź, czy czcionek, które są zależnych usługi (na przykład tekst pogrubieniem lub rozszerzonej) zachowania ich rozmiar i formatowanie względem tekstu "normal", gdy zmienia się rozmiar czcionki środowiska.  
  
-   Sprawdź, czy nie występują żadne błędy wycinka z powodu rozszerzonej czcionki. Czcionki, które uzyskać przycięte prawdopodobnie są wynikiem stałą wysokość formantów lub kontenery stałą wysokość.  
  
### <a name="dialogs"></a>Okna dialogowe  
  
-   Sprawdź, czy tytuł okna dialogowego jest taka sama jak polecenia, który go uruchomić.  
  
-   Sprawdź, czy wszystkie formanty standardowe są zgodne z systemem operacyjnym: kolor tła jest standardowe i żadne formanty nie powinna mieć stylu szablonem ponowna specjalne są wyświetlane różne od formantów standardowych.  
  
-   Sprawdź, czy marginesy w formularzu powinny być 12 pikseli i powinna zostać wyświetlona uniform i spójny.  
  
-   Sprawdź, czy okna dialogowe są wyświetlane wyśrodkowany w powłoce programu IDE lub okna zduplikowany je.  
  
-   Gdy jest to przydatne, okna dialogowe powinna być o zmiennym rozmiarze. W oknach dialogowych, które są o zmiennych rozmiarach Sprawdź, czy po zmianie rozmiaru, kontrole należy zmienić rozmiar, podczas gdy inne części okna dialogowego pozostają takie same.  
  
-   Upewnij się, że rozmiar okna dialogowe utrwalić dowolnej wielkości dostosowane przez użytkownika (rozmiar, lokalizacji, rozszerzenia formantów okna dialogowego i tak dalej).  
  
-   Sprawdź, czy jest brak ikony na pasku tytułu.  
  
-   Sprawdź, że nie ma żadnych przyciski na pasku tytułu.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Okno dialogowe operacji przycisków (tylko klient VS)  
  
-   Sprawdź, czy operacja przycisków w następującej kolejności: **OK**, **anulować**, **Zastosuj**.  
  
-   Sprawdź, czy **OK** i **anulować** przyciski są standardowy rozmiar: 75 x 23 pikseli.  
  
-   Sprawdź, czy **OK** i **anulować** przyciski mają taki sam rozmiar niezależnie od długości ciągu.  
  
-   Jeśli etykieta przycisku operacja wymaga przycisku za większy niż standardowe, upewnij się, że odpowiednie **anulować** przycisk jest taki sam rozmiar.  
  
-   Sprawdź, czy jest uzupełnienie 6 pikseli między przycisków i skojarzonych formantów.  
  
-   Sprawdź, czy **OK** i **anulować** przyciski nie mają mnemonik (klucze dostępu zdefiniowanych przez podkreślona litera).  
  
-   Sprawdź, że jeden z przycisków (zazwyczaj **OK**) domyślnie ma fokus.  
  
-   Sprawdź, czy **Esc** anuluje okna dialogowego  
  
-   Sprawdź, czy **Enter** wykonuje przycisk domyślny, jeśli fokus nie jest formant, który przetwarza Enter.  
  
-   Sprawdź, czy **OK** i **anulować** przycisków znajdują się w prawym dolnym rogu okna dialogowego. W rzadkich wyjątki dopuszczalne jest dla nich być ułożone pionowo w prawym górnym rogu.  
  
-   Sprawdź, czy pionowy konfiguracji jest używany tylko wtedy, gdy inne przyciski w wyrównanie w poziomie w oknie dialogowym.  
  
### <a name="control-standards"></a>Standardy formantu  
  
#### <a name="general"></a>Ogólne  
  
-   Sprawdź, czy, jeśli to możliwe, wartości domyślne dobrej aby przyspieszyć interakcji z użytkownikiem i poinstruować użytkowników kierunku wyniku wspólnej lub sejfie.  
  
-   Sprawdź, czy formanty standardowe działają tak samo, tak aby użytkownicy wiedzieli, co się stanie, na podstawie doświadczeń wcześniejszych.  
  
#### <a name="label-controls"></a>Etykieta kontrolki  
  
-   Sprawdź, czy każdego formantu ma etykietę, oraz czy każda etykieta będzie łączyć się z jego kontrolą (zazwyczaj w zakresie pikseli 4 – 6) i jest bliżej niż jego odpowiedniego formantu do innych kontrolek.  
  
-   Sprawdź, czy etykiety są rozmieszczone opróżnić lewej za pomocą formantu lewej krawędzi, jeśli znajduje się powyżej i wyśrodkowany w poziomie, dlatego, że linia bazowa etykiety jest wyrównany z linią bazową elementu wejściowego tekstu, jeśli znajduje się po lewej stronie.  
  
-   Sprawdź, czy jeśli kilka skumulowany etykiety i kontrolki wejściowe są pozycjonowane do lewego rogu formantu, etykiety jest wyrównany do lewej oraz samej odległości od krawędzi okna dialogowego, nigdy nie opróżnić prawo i samej odległości od formantów. Pary powinny rozmieszczana równomiernie, o ile nie potrzebują dodatkowych odstępów wskazująca grupowania.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Kontrolki wejściowe (pola tekstowe i pola kombi)  
  
-   Sprawdź, czy podczas korzystania z domyślnej czcionki środowiska, wysokość ekranu dla pól tekstowych, pól kombi i przyciski są wszystkie piksele 23.  
  
-   Jeśli używane jest tekst podpowiedzi, sprawdź, czy kolor ma ustawioną `Environment.ControlEditHintText` przy użyciu usługi kolorów.  
  
-   Jeśli pole jest wymagane pola, które muszą być określone jako takie, sprawdź:  
  
    -   tło jest ustawiona `Environment.ControlEditRequiredBackground` i ma ustawioną wartość pierwszego planu`Environment.ControlEditRequiredHintText`  
  
    -   Brak tekstu podpowiedzi wewnątrz formantu, który jest wyświetlany jako **"\<wymagany >"**  
  
#### <a name="button-controls"></a>formanty przycisków  
  
-   Sprawdź, czy przyciski minimalny rozmiar 75 x 23 pikseli, chyba że obsługa dłużej tekstu.  
  
-   Sprawdź, czy przyciski jeszcze, a następnie kliknij prawym przyciskiem myszy marginesy 3 – 5 pikseli, a także uzupełnienie zawartości.  
  
-   Można używać małych kwadratowym przycisku tylko osoba lub grupa **[...]**  na nim zamiast **[Przeglądaj]**  przycisk (lub podobne funkcje). Jeśli używana, sprawdź przycisk 23 x 23 rozmiar.  
  
-   Jeśli istnieje więcej niż jeden **[Przeglądaj]**  przycisk w oknie dialogowym, a następnie sprawdź, czy skróconej wersji (tylko do wielokropka **[...]** ) jest używany w przypadku wszystkich.  
  
-   Sprawdź, że wielokropka **[...]**  przyciski nie mają wartość. Gdy fokus jest ustawiony na kontrolki wprowadzania obok siebie, jedna karta powinien Przenieś fokus na przycisk wielokropka.  
  
-   Sprawdź, czy przycisków, poleceń i łączy polecenia Uruchom dodatkowej interfejs użytkownika, który przechwytuje więcej danych wejściowych użytkownika musi kończyć się wielokropek **[...]** .  
  
#### <a name="hyperlinks"></a>Hiperłącza  
  
-   Sprawdź, czy formant hiperłącza nigdy nie pojawi się na chwilę czerwony, gdy jest aktywny. Jest to wskaźnik koloru usługi nie jest używana  
  
-   Sprawdź, czy kolory programu VS, używane są:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Sprawdź, czy hiperłącza kolorze niebieskim z bez podkreślenia, chyba że osadzonych akapitu.  
  
#### <a name="check-boxes"></a>Zaznaczanie pól  
  
-   Jeśli pole wyboru ma wiele wierszy tekstu, sprawdź, czy pole wyrównana z pierwszego wiersza tekstu nie wyśrodkowane w pionie w obrębie wszystkich wierszy.  
  
-   Sprawdź, czy pola wyboru zawsze wskazywać binarne wyboru i nie użytkownik lub Otwórz nowe okno lub strony.  
  
-   Jeśli pole wyboru opcji związanych z kontrolki wprowadzania, sprawdź, czy jest umieszczony opróżnić po lewej i bardzo Zamknij pod kontrolą tego wskazująca jego relacji.  
  
-   Sprawdź, czy pole wyboru jest **nigdy nie** używane jako środek do włączania całą zawartość okna dialogowego lub strony.  
  
#### <a name="group-boxes"></a>Pola grupy  
  
-   Sprawdź, czy okno dialogowe zawiera pole o pojedynczej grupy, w jego zawierający całą zawartość okna dialogowego.  
  
-   Sprawdź, czy masz co najmniej dwóch formantów w każdym polu grupy.  
  
-   Rzadko powinny istnieć więcej niż dwa pola grupy w oknie dialogowym.  
  
-   Sprawdź, że nie ma żadnych grup zagnieżdżonych pól.  
  
### <a name="icons"></a>Ikony  
  
-   Sprawdź, czy ikony są wyświetlane poprawnie odwrócony w przypadku ciemnego motywu.  
  
-   Upewnij się, że wszystkie ikony są oparte na podstawowe koncepcje.  
  
-   Sprawdź, czy ikona każdej distinct, łatwe do rozpoznania i nie zawiera więcej niż dwa pojęcia (bez modyfikatora stan/język).  
  
-   Sprawdź, czy podstawowy pojawi się ikona wyśrodkowane w obszarze.  
  
-   Sprawdź, czy wszystkie ikony są wyświetlane w trybie dużego kontrastu do odczytania.  
  
-   Sprawdź, czy żadnych kolor używany wyrównana z normami użycia kolorów.  
  
-   Sprawdź, czy nie występują żadne otoczek (obramowanie) wokół ikon. (Jeśli jest obecny, otoczki powinna odpowiadać kolor tła sąsiadujących interfejsu użytkownika).  
  
### <a name="touch-enabled-ui"></a>Dotykowe interfejsu użytkownika  
  
-   Sprawdź, czy interaktywnych kontrolek są wystarczająco duże, aby można łatwo touchable — minimalna **pikseli 23 x 23** rozmiaru  
  
-   Sprawdź, czy formanty najczęściej używane są co najmniej **40 40 pikseli** rozmiar.  
  
-   Sprawdź, czy interaktywnych kontrolek mają co najmniej **5 pikseli odstępy** między nimi