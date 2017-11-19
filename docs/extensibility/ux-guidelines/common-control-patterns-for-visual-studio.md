---
title: "Wspólne wzorce formantu dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e06a3e89b69b2b69a97c4deb2d68d98913f6e03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="common-control-patterns-for-visual-studio"></a>Wspólne wzorce formantu dla programu Visual Studio
##  <a name="BKMK_CommonControls"></a>Formanty standardowe  
  
### <a name="overview"></a>Omówienie  
Formanty standardowe tworzą większość interfejsu użytkownika w programie Visual Studio. Należy stosować najbardziej wspólnych kontrolek używanych w interfejsie programu Visual Studio [wytyczne interakcji z pulpitu systemu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Ten temat jest przeznaczony dla programu Visual Studio i obejmuje sytuacji specjalnych lub uzyskać szczegółowe informacje, które rozszerzyć tymi wytycznymi systemu Windows.  
  
#### <a name="common-controls-in-this-topic"></a>Formanty standardowe w tym temacie  
  
-   [Paski przewijania](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Pól wejściowych](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Pola kombi oraz listy rozwijane](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Zaznaczanie pól](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Przyciski opcji](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Grupy ramki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Kontrolki tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Przyciski i hiperłącza](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Widok drzewa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
Przede wszystkim należy wziąć pod uwagę podczas style formantów jest, czy formanty będzie używany w motywem interfejsu użytkownika. Formanty w standardowy interfejs użytkownika są-motywem interfejsu użytkownika i wykonaj [stylu standardowego pulpitu systemu Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), czyli nie są ponownie szablonem i powinna pojawić się w ich domyślny wygląd formantu.  
  
-   **Okna dialogowe Standard (Narzędzia):** nie motywów. Nie ponowna szablonu. Użyj wartości domyślnych stylów formantu podstawowe.  
  
-   **Narzędzia systemu windows, edytory dokumentu, projektów i motywów okien dialogowych:** używać specjalnych wygląd kompozycji przy użyciu usługi kolorów.  
  
###  <a name="BKMK_Scrollbars"></a>Paski przewijania  
 Paski przewijania, należy stosować [paski przewijania typowe wzorce interakcji dla systemu Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) , chyba że są one rozszerzone przy użyciu informacji o zawartości, takich jak w edytorze kodu.  
  
###  <a name="BKMK_InputFields"></a>Pól wejściowych  
 Dla zachowania typowe interakcji, wykonaj [wytyczne pulpitu systemu Windows dla pól tekstowych](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
  
-   Pól wejściowych nie powinien wstawiony w oknach dialogowych narzędzia. Użyj styl podstawowy wewnętrznej do formantu.  
  
-   Motywem pól wejściowych należy używać tylko w oknach dialogowych motywów i okien narzędzi.  
  
#### <a name="specialized-interactions"></a>Interakcje specjalne  
  
-   Pola tylko do odczytu mają tła szary (wyłączone), ale pierwszy plan domyślny (aktywny).  
  
-   Wymagane pola powinny mieć  **\<wymagany >** jak znaki wodne w nich. Kolor tła z wyjątkiem w rzadkich sytuacji nie należy zmieniać.  
  
-   Błąd sprawdzania poprawności: zobacz [powiadomień i postępu dla programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Pól wejściowych należy ustalać w celu dopasowania do zawartości, nie można dopasować szerokości okna, w którym są wyświetlane ani arbitralnie zgodnie z długością pola, takie jak ścieżka. Długość może być wskazanie użytkownikowi ograniczenia dotyczące liczby znaków są dozwolone w tym polu.  
  
     ![Nieprawidłowe pole wejściowe, długość: jest mało prawdopodobne, że będzie tym długa nazwa. ] (../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Nieprawidłowe pole wejściowe, długość: jest mało prawdopodobne, że będzie tym długa nazwa.
  
     ![Popraw długość pola wejściowego: pole wejściowe jest uzasadnione szerokość oczekiwanej zawartości. ] (../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Popraw długość pola wejściowego: pole wejściowe jest uzasadnione szerokość oczekiwanej zawartości.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>Pola kombi oraz listy rozwijane  
Dla zachowania typowe interakcji, wykonaj [Windows Desktop wytyczne dotyczące listy rozwijane i pola kombi](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
  
-   W oknach dialogowych narzędzia nie ponowna szablonu formantu. Użyj styl podstawowy wewnętrznej do formantu.  
  
-   W motywem interfejsu użytkownika, listy rozwijane i pola kombi wykonaj standardowe motywów dla formantów.  
  
#### <a name="layout"></a>Układ  
Pola kombi i listach rozwijanych należy ustalać w celu dopasowania do zawartości, nie można dopasować szerokości okna, w którym są wyświetlane ani arbitralnie zgodnie z długością pola, takie jak ścieżka.  
  
![Niepoprawne: szerokość listy rozwijanej jest za długa dla zawartości, który będzie wyświetlany. ] (../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Niepoprawne: szerokość listy rozwijanej jest za długa dla zawartości, który będzie wyświetlany.
  
![Poprawne: listy rozwijanej jest dopasowywany do umożliwienia wzrostu tłumaczenia, ale nie niepotrzebnie długie. ] (../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Poprawne: listy rozwijanej jest dopasowywany do umożliwienia wzrostu tłumaczenia, ale nie niepotrzebnie długie. 
  
###  <a name="BKMK_CheckBoxes"></a>Zaznaczanie pól  
Dla zachowania typowe interakcji, wykonaj [wytycznych pulpitu systemu Windows dla pola wyboru](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
  
-   W oknach dialogowych narzędzia nie ponowna szablonu formantu. Użyj styl podstawowy wewnętrznej do formantu.  
  
-   W motywem interfejsu użytkownika pola wyboru wykonaj standardowe motywów dla formantów.  
  
#### <a name="specialized-interactions"></a>Interakcje specjalne  
  
-   Interakcja z polem wyboru nigdy nie musi pop okna dialogowego lub przejdź do innego obszaru.  
  
-   Dopasuj pola wyboru z linią bazową pierwszego wiersza tekstu.  
  
     ![Niepoprawne: pole wyboru skupia się na tekst. ] (../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Niepoprawne: pole wyboru skupia się na tekst.
  
     ![Poprawne: pole wyboru jest wyrównywana z pierwszego wiersza tekstu. ] (../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Poprawne: pole wyboru jest wyrównywana z pierwszego wiersza tekstu.
  
###  <a name="BKMK_RadioButtons"></a>Przyciski opcji  
Dla zachowania typowe interakcji, wykonaj [Windows Desktop wytyczne dotyczące przycisków radiowych](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
W oknach dialogowych narzędzia czy nie styl przycisków radiowych. Użyj styl podstawowy wewnętrznej do formantu.  
  
#### <a name="specialized-interactions"></a>Interakcje specjalne  
Nie jest konieczne wykorzystywane są ramki grupy wybór opcji, chyba że należy przestrzegać rozróżnienie grup w układzie ścisłej.  
  
###  <a name="BKMK_GroupFrames"></a>Grupy ramki  
Dla zachowania typowe interakcji, wykonaj [Windows Desktop wytyczne dotyczące grupy ramek](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
W oknach dialogowych narzędzia nie stylu ramki grupy. Użyj styl podstawowy wewnętrznej do formantu.  
  
#### <a name="layout"></a>Układ  
  
-   Nie jest konieczne wykorzystywane są ramki grupy wybór opcji, chyba że należy przestrzegać rozróżnienie grup w układzie ścisłej.  
  
-   Nigdy nie używaj ramki grupy dla pojedynczego formantu.  
  
-   Czasami jest dopuszczalne do korzystania z linią poziomą zamiast kontener ramki grupy.  
  
##  <a name="BKMK_TextControls"></a>Kontrolki tekstu

### <a name="static-text-fields"></a>Statyczne pola tekstowe

Statyczne pole tekstowe przedstawiono informacje tylko do odczytu i nie może zostać wybrane przez użytkownika. Unikaj używania go na dowolny tekst, który użytkownik może ma zostać skopiowany do Schowka. Jednak zmienić w celu odzwierciedlenia zmiany w stanie tylko do odczytu tekst statyczny. W przykładzie poniżej tekst statyczny nazwy wyjściowego zmiany grupy informacji, aby odzwierciedlić zmiany wprowadzone w polu tekstowym Namespace głównego powyżej.

Istnieją dwa sposoby wyświetlania informacji tekst statyczny.

Tekst statyczny nie może być na jego własnej w oknie dialogowym bez żadnych zawierania w przypadku nie występuje grupowania konflikt. Zdecyduj, czy wiersze dodatkowe pola są naprawdę konieczne. Przykładem jest wyświetlanie ścieżki katalogu sekcji utworzony przez wiersz grupy, jak pokazano poniżej:  

![Informacje o statyczny tekst w formantach tekstu](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informacje o statyczny tekst w formantach tekstu

W oknie dialogowym których istnieje innych obszarach grupowanych i zawierania informacji może pomóc zwiększyć czytelność i po sekcji mogą być ukryte lub pokazane (podobnie jak w **okna właściwości** okienko opisu) lub być zgodne z podobnych interfejsu użytkownika, Umieść tekst statyczny wewnątrz pola. To pole grupy powinny być jedną regułę i kolorowe z `ButtonShadow`:

![Statyczny tekst w oknie właściwości](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Statyczny tekst w oknie właściwości

### <a name="read-only-text-box"></a>Pole tekstowe tylko do odczytu

Dzięki temu użytkownikowi zaznacz tekst wewnątrz pola, ale nie można go edytować. Te pola tekstowe są otoczony zwykle Dłuto 3-z `ButtonShadow` wypełnienia.

Pole tekstowe może stać się aktywny (edytowalne), gdy użytkownik zmienia skojarzonym formancie, takich jak sprawdzanie lub usunięcie zaznaczenia pola pola wyboru lub przycisku radiowego wybranie/zaznaczenia. Na przykład w **narzędzia &gt; opcje** strony pokazano poniżej, **strony głównej** pole tekstowe staje się aktywny po **użyj ustawienia domyślnego** pole wyboru jest zaznaczone.

![Pole tekstowe tylko do odczytu, przedstawiający stanem nieaktywnym i aktywnym](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Pole tekstowe tylko do odczytu, przedstawiający stanem nieaktywnym i aktywnym

### <a name="using-text-in-dialogs"></a>Przy użyciu tekstu w oknach dialogowych

Klucza wytyczne dotyczące tekstu w oknach dialogowych:

-   Etykiety pól tekstowych, pola listy i ramek w oknach dialogowych unthemed rozpoczynać zlecenie, ma początkową wielką na pierwsze słowo i się kończyć dwukropkiem.

    > Postępuj zgodnie z formantami w oknach dialogowych motywów [wskazówki dotyczące interfejsu użytkownika pulpitu systemu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx) ale nie końcowych znaków interpunkcyjnych z wyjątkiem znaków zapytania w łącza pomocy.

-   Etykiety dla pola wyboru i przycisków opcji rozpoczynać zlecenie początkową wielką tylko pierwsze słowo i mieć bez końcowych znaków interpunkcyjnych.

-   Etykiety dla przycisków, menu, elementy menu i karty mają początkowe wersaliki na każdego wyrazu (tytuł wielkości liter).

-   Terminologia etykiety powinny być zgodne z podobnych etykiet w innych oknach dialogowych.

-   Jeśli to możliwe mieć moduł zapisujący/edytora, zapisu lub Zatwierdź tekst przed trafia do deweloperów dla implementacji.

-   Wszystkie formanty powinny mieć etykiety z wyjątkiem w wyjątkowych okolicznościach, w których klawisza TAB jest wystarczająca.
Użyj Pomocnika tekstu, gdy jest to konieczne.

### <a name="helper-text"></a>Tekst pomocy

Uwzględnione w oknach dialogowych, aby pomóc użytkownikowi w zrozumienie przeznaczenia okna dialogowego lub wskaż, jakie działania należy podjąć. Tekst pomocy należy tylko w razie potrzeby uniknąć przeładowania proste okien dialogowych. Dwie zmiany tekstu pomocnika to okno dialogowe i znak wodny.

Wykonaj wspólnej lokalizacji dla pomocnika, tekstu i należy wybrać wprowadzenie nowego obszarów. Typowe scenariusze dla tekstu pomocnika są:

-   Tekst pomocy w oknach dialogowych, aby przekazać dodatkowe kierunek o tym, jak wchodzić w interakcje z złożonych okna dialogowego.

-   Tekstu znaku wodnego w pustym narzędzia windows lub okien dialogowych, aby wyjaśnić, dlaczego nie zawartość jest widoczna.

-   Okienko opisu, u dołu, takich jak **okna właściwości**.

-   Znak wodny tekstu w edytorze puste, aby opisano czynności, użytkownik powinien wykonać, aby rozpocząć pracę.
  
### <a name="dialog-helper-text"></a>Tekst pomocy w oknie dialogowym

Projektant środowisko użytkownika może ułatwić określenie, kiedy są odpowiednie tekst pomocy. Projektant można określić, gdzie pomocnika tekstu oraz jego ogólnej zawartości. Pomoc dla użytkownika można zapisu i edytować tekst.

### <a name="watermarks"></a>Znaki wodne

Okna dialogowe korzystać z wytycznymi nieco inne znaku wodnego. Ponieważ okno dialogowe może występować zajęty wiele elementów interfejsu użytkownika (etykiety, tekst podpowiedzi, przycisków i innych kontrolek kontenera tekstem), szczególnie gdy te są wyświetlane w kolorze czarnym, znaki wodne bardziej czytelne w kolorze szarym ciemny (VSColor: `ButtonShadow`). Zwykle pojawia się znak wodny wewnątrz formantu, takich jak pole listy z białe tło (VSColor: `Window`).

-   Tekst jest wyświetlany w kolorze szarym ciemny (VSColor: `ButtonShadow`). Jednak jeśli w kolorze szarym lub inne kolorze pojawi się znak wodny (VSColor: `ButtonFace`) w tle i dotyczyć o jego czytelność, przejdź czarny tekst (VSColor: `WindowText`).

-   Znaki wodne można wyśrodkowany lub wyrównany do lewej. Zastosuj reguły projektowania standardowe podczas podejmowania decyzji wyrównania. Nie można wybrać znak wodny w tle.

![Przykład tekstu znaku wodnego](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Przykład tekstu znaku wodnego

### <a name="context-specific-dynamic-text"></a>Zależne od kontekstu tekst (dynamiczny)

Dynamiczny tekst może być używany jeden z dwóch sposobów, w oknie dialogowym lub niemodalne interfejsu użytkownika: jako dynamiczny etykiety lub jako zawartość dynamiczną.

-   Dynamiczne etykiety: użycia dynamicznych tekstu jest opisowy panele, które oferują więcej informacji dla wybranego elementu, takie jak w oknie dialogowym, który zawiera listę elementów i właściwości dla tych elementów w siatce po prawej stronie. Etykiety siatki właściwości może być dynamiczny tak, aby po wybraniu elementu po lewej stronie, na siatce po prawej stronie są wyświetlane informacje dotyczące określonego elementu.

-   Dynamiczny tekst: może być przydatne w sytuacjach, gdy trzeba wyświetlić szczegółowe informacje, a nie ogólne informacje w ten sposób, ale należy zwrócić uwagę, aby nie nadużywać.

Jeśli chcesz mieć możliwość kopiowania informacje użytkownicy dynamiczny tekst powinien być w pole tekstowe tylko do odczytu.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>Przyciski i hiperłącza  
  
### <a name="overview"></a>Omówienie  
Formanty łącza i przycisków (hiperłącza) należy stosować [podstawowe wskazówki pulpitu systemu Windows na hiperłącza](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) do użycia, terminologię, zmiany rozmiaru i odstępy.  
  
### <a name="choosing-between-buttons-and-links"></a>Wybór między przycisków i łącza  
Tradycyjnie użyto przycisków akcji i hiperłączy zostały zarezerwowane dla nawigacji. Przyciski mogą używać we wszystkich przypadkach, ale rolę łącza zostały rozszerzone w programie Visual Studio, aby przyciski i łącza są bardziej wymienne w niektórych warunkach.  
  
Kiedy należy używać przyciski poleceń:  
  
-   Podstawowy poleceń  
  
-   Wyświetlanie systemu windows używane do zbierania danych wejściowych lub wybierania opcji, nawet jeśli są one dodatkowej poleceń  
  
-   Akcje destrukcyjnego lub nieodwracalne  
  
-   Przyciski zadeklarowanej w kreatorach i przepływów strony  
  
Unikaj przyciski poleceń narzędzia systemu Windows, lub jeśli potrzebujesz więcej niż dwa wyrazy dla etykiety. Łącza może mieć etykiety dłużej.  
  
 Kiedy należy używać łącza:  
  
-   Nawigacja do innego okna, dokumentu lub strony sieci web  
  
-   Sytuacje wymagające dłużej etykiety lub krótkich zdanie do opisywania celem akcji  
  
-   Ścisłej spacji, gdy przycisk będzie przeciąży interfejsu użytkownika, pod warunkiem, że akcja nie jest destrukcyjnego lub nieodwracalne  
  
-   Dezaktywowanie myślą dodatkowej poleceń w sytuacjach, w których istnieje wiele poleceń  
  
#### <a name="examples"></a>Przykłady  
![Polecenie łącza używane na pasku informacyjnym następującego komunikatu o stanie](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Polecenie łącza używane na pasku informacyjnym następującego komunikatu o stanie
  
![Łącza używane w menu podręcznym CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />Łącza używane w menu podręcznym CodeLens
  
![Łącza używany przez polecenia dodatkowej, w którym przyciski czy przyciągania zbyt wiele uwagi](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Łącza używany przez polecenia dodatkowej, w którym przyciski czy przyciągania zbyt wiele uwagi
  
### <a name="common-buttons"></a>Typowe przycisków  
  
#### <a name="text"></a>Tekst  
Postępuj zgodnie z wytycznymi zapisu w [interfejsu użytkownika tekstu i terminologię](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
  
##### <a name="standard-unthemed"></a>Standard (unthemed)  
Większość przycisków w programie Visual Studio pojawi się w oknach dialogowych narzędzia i nie powinien być styl. Powinny one odzwierciedlać standardowe wygląd przycisków, zgodnie z ustawieniami systemu operacyjnego.  
  
##### <a name="themed"></a>Motywów  
W niektórych przypadkach przyciski mogą być używane w ramach styl interfejsu użytkownika i muszą być odpowiednio stylem tych przycisków. Zobacz [okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Aby uzyskać informacje dotyczące formantów z motywów.  
  
### <a name="special-buttons"></a>Specjalne przyciski  
  
#### <a name="browse-buttons"></a>Przeglądaj przycisków  
**[Przeglądaj]**  przycisków są używane w siatki, okna dialogowe i okien narzędzi i innych niemodalne elementów interfejsu użytkownika. Wyświetlane selektora, które pomaga wypełniania wartość w formancie użytkownika. Istnieją dwie odmiany długich i krótkich tego przycisku.  
  
![Długie przycisk [przeglądania...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />Długie przycisk [przeglądania...]
  
![Przycisk tylko do wielokropka krótkiej [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />Przycisk tylko do wielokropka krótkiej [...]
  
Kiedy należy używać tylko do wielokropka przycisk krótki:  
  
-   Jeśli istnieje więcej niż jeden długi **[Przeglądaj]**  przycisk w oknie dialogowym, takie jak kiedy kilka pól umożliwiają przeglądanie. Użyj krótkim **[...]**  przycisk dla każdego z nich w celu uniknięcia mylące klucze dostępu tworzone przez tej sytuacji (**& Przeglądaj** i **B & Przeglądaj** w tym samym oknie dialogowym).  
  
-   W oknie dialogowym ścisłej lub po nie uzasadnione miejsce do umieszczenia długi przycisku.  
  
-   Jeśli przycisk pojawi się w kontrolce siatki.  
  
Wskazówki dotyczące używania przycisku:  
  
-   Nie używaj klucza dostępu. Dostępu do niej przy użyciu klawiatury, użytkownik musi karcie z sąsiadujących ze sobą formantu. Upewnij się, że kolejność tabulacji jest taka, że znajduje się natychmiast po jej spowoduje wypełnienie pola dowolnego przycisku Przeglądaj. Nigdy nie używaj znaku podkreślenia poniżej pierwszego okresu.  
  
-   Ustaw Microsoft Active Accessibility (MSAA) **nazwa** właściwości **Przeglądaj...**  (w tym wielokropek), który ekranu czytników odczyta go jako "Przeglądaj", a nie "kropka kropka kropka" lub "czasu okres okres." Zarządzane formanty, oznacza to ustawienie **AccessibleName** właściwości.  
  
-   Nigdy nie używaj wielokropek **[...]**  przycisk jakikolwiek inny niż akcji przeglądania. Na przykład, jeśli potrzebujesz **[nowy...]**  przycisku, ale nie ma wystarczającej ilości miejsca dla tekstu, a następnie w oknie dialogowym musi być przeprojektowany.  
  
##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy  
![Zmiany rozmiaru [przeglądania...] przyciski: standardową wersję 75 x 23 pikseli, krótka wersja jest pikseli 26 x 23](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Ustawianie rozmiaru przycisków [przeglądania...]
  
![Odstępy [przeglądania...] przyciski: odstępy między pokrewnej kontrolki i standardowe pikseli 7 przycisk przeglądania, odstępy między pokrewnej kontrolki i przeglądania krótkich przycisk 5 pikseli](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Odstępy przycisków [przeglądania...]
  
#### <a name="graphical-buttons"></a>Przyciski graficznego  
Niektóre przyciski należy zawsze używać graficzny i nigdy nie zawierają tekst w celu zaoszczędzenia miejsca oraz uniknąć problemów z lokalizacji. Często są one używane w pole wyboru, a inne można sortować listy.  
  
> **Uwaga:** użytkownicy będą musieli karty, aby tych przycisków (Brak kluczy dostępu), więc umieścić je w kolejności za pośrednictwem. Mapa `name` właściwość przycisk, aby akcja, która zajmuje, dzięki czemu czytników ekranu poprawnie zinterpretować Akcja przycisku.  
  
| Funkcja | Przycisk |  
| --- | --- |  
| Dodaj | ![Przycisk "Dodaj" graficzny](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Usuń | ![Przycisk "Usuń" graficzny](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Dodaj wszystkie | ![Przycisk "Dodaj wszystkie" graficzny](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Usuń wszystkie | ![Przycisk "Usuń wszystko" graficzny](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Przenieś w górę | ![Graficzny "przycisk Przenieś w górę"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Przenieś w dół | ![Graficzny "przycisk Przenieś w dół"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Usuwanie | ![Przycisk "Delete" graficzny](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy  
Zmiany rozmiaru dla przycisków graficznego jest taka sama jak w przypadku krótkiej **[Przeglądaj]**  przycisk (w pikselach 26 x 23):  
  
![Wygląd graficznej na przycisku z włączonymi i wyłączonymi kolor przezroczysty przedstawiający](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Wygląd graficznej na przycisku z włączonymi i wyłączonymi kolor przezroczysty przedstawiający
  
### <a name="hyperlinks"></a>Hiperłącza  
Hiperłącza dobrze nadają się do nawigacji na podstawie akcji, takich jak otwieranie tematu pomocy, modalnego okna dialogowego lub kreatora. Jeśli hiperłącze jest używana dla polecenia, będzie zawsze wyświetlenie widoczne i zauważalne zmiany do interfejsu użytkownika. Ogólnie rzecz biorąc w akcji, które zatwierdzenia w akcji (np. Zapisz i Anuluj i Usuń) za pomocą przycisku lepiej są przekazywane.  
  
#### <a name="writing-style"></a>Styl pisania  
Postępuj zgodnie z [Windows Desktop wskazówki dotyczące tekst interfejsu użytkownika](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). Nie używaj "Dowiedz się więcej o," "Powiedz mi więcej o" lub "Uzyskiwanie pomocy na temat to" właściwej. Zamiast tego frazę tekst łącza pomocy pod względem pytanie główne odpowiedzi zawartości pomocy. Na przykład "**jak dodać serwer do Eksploratora serwera?**"  
  
#### <a name="visual-style"></a>Stylu wizualnego.  
  
-   Zawsze należy używać hiperłącza [usługa VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Jeśli hiperłącza nie ma zdefiniowanych poprawnie, miga czerwony, gdy jest aktywny lub zawiera inny kolor po odwiedzana.  
  
-   Nie dołączaj podkreślenia w kontroli ustawiony stan, chyba że łącze jest fragmentu zdanie w ramach pełnej zdania, podobnie jak w znaku wodnego.  
  
-   Podkreślenia nie są wyświetlane na aktywowany. Zamiast tego opinię do użytkownika, czy łącze jest aktywne jest zmiana kolorów nieznaczne i kursora odpowiednie łącze.  
  
##  <a name="BKMK_TreeViews"></a>Widok drzewa  
  
Widok drzewa zapewniają sposób organizowania złożonych wymieniono w grupy nadrzędny podrzędny. Użytkownik może rozwinąć lub zwinąć grupy nadrzędne, aby pokazać lub ukryć podstawowe elementy podrzędne. Aby dostarczyć więcej akcji można wybrać każdego elementu w widoku drzewa.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>Styl wizualny widoku drzewa  
  
#### <a name="expanders"></a>Ekspanderów znajdujących  
Formanty widoku drzewa powinna być zgodna z projektu expander, używane przez system Windows i programu Visual Studio. Każdy węzeł będzie używał kontrolki expander Wyświetl lub Ukryj podstawowych elementów. Za pomocą kontrolki expander zapewnia spójność dla użytkowników, którzy mogą występować w widokach innego drzewa w ramach systemu Windows i programu Visual Studio.  
  
![Poprawne: styl prawidłowego węzła widoku drzewa za pomocą kontrolki expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Poprawne: style właściwe za pomocą kontrolki expander węzła widoku drzewa
  
![Niepoprawne: niewłaściwy styl węzła widoku drzewa](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Niepoprawne: niewłaściwy styl węzła widoku drzewa
  
#### <a name="selection"></a>Wybór  
Po wybraniu węzła w widoku drzewa rozszerzyć zaznaczenie do pełnej szerokości formantu widoku drzewa. Pomaga to użytkownikom jednoznacznie zidentyfikować elementu, który został wybrany. Wybór kolorów odzwierciedlały bieżący motyw programu Visual Studio.  
  
![Poprawne: wyróżnienie z zaznaczonego węzła pasuje do całego szerokość formantu widoku drzewa. ] (../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Poprawne: wyróżnienie z zaznaczonego węzła pasuje do całego szerokość formantu widoku drzewa.
  
![Niepoprawne: wyróżnienie z zaznaczonego węzła nie mieści się całą szerokość formantu widoku drzewa. ] (../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Niepoprawne: wyróżnienie z zaznaczonego węzła nie mieści się całą szerokość formantu widoku drzewa.
  
#### <a name="icons"></a>Ikony  
Ikony należy używać w kontrolki widoku drzewa tylko, jeśli one ułatwić wizualnie identyfikowania różnic między elementami. Ogólnie rzecz biorąc ikony powinna być używana tylko w heterogenicznych list, w których ikony przenoszenia informacji do rozróżniania typów elementów. Na liście jednorodnych przy użyciu ikony często są widoczne jako szumu i należy unikać. W takim przypadku ikona grupy (nadrzędnego) można przekazać na typ elementów w niej. Wyjątkiem od tej reguły będzie, jeśli ikona jest dynamiczny i służy do wskazywania stanu.  
  
#### <a name="scroll-bars"></a>Paski przewijania  
Paski przewijania zawsze powinien być ukryty, jeśli zawartość mieści się w kontrolce widoku drzewa. Dopuszczalne są pasków przewijania w oknie przewijanego być ukryte lub półprzezroczysty i są wyświetlane po aktywowaniu okna zawierającego widoku drzewa lub po aktywowaniu drzewa wyświetlić sam.  
  
![Oba paski przewijania poziome i pionowe są wyświetlane, ponieważ zawartość przekroczenia limitu kontrolki widoku drzewa. ] (../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Oba paski przewijania poziome i pionowe są wyświetlane, ponieważ zawartość przekroczenia limitu kontrolki widoku drzewa.
  
###  <a name="BKMK_TreeViewInteractions"></a>Interakcje widoku drzewa  
  
#### <a name="context-menus"></a>Menu kontekstowe  
Węzła widoku drzewa może ujawnić opcje podmenu w menu kontekstowym. Zazwyczaj dzieje, gdy użytkownik kliknął prawym przyciskiem myszy element lub naciśnięty klawisz Menu na klawiaturze systemu Windows z wybranego elementu. Jest ważne, czy węzeł zyskuje fokus i wybrano. Dzięki temu użytkownikowi w poznaniu podmenu należy do elementu.  
  
![Wybrano element, który ma generować fokus zyski menu kontekstu do powiadamiania użytkownika elementu. ] (../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />Wybrano element, który ma generować fokus zyski menu kontekstu do powiadamiania użytkownika elementu.
  
#### <a name="keyboard"></a>Klawiatury  
Widok drzewa musi zapewniać możliwość wybierz elementy i Rozwiń/Zwiń węzłów za pomocą klawiatury. Dzięki temu, że nawigacji spełnia wymagania naszego ułatwień dostępu.  
  
##### <a name="tree-view-control"></a>Widok drzewa  
Formanty drzew usługi Visual Studio należy wykonać typowe nawigacji klawiatury:  
  
-   **Strzałka w górę:** wybierz elementy przez przeniesienie w górę drzewa  
  
-   **Strzałka w dół:** wybierz elementy, przenosząc niżej na drzewie  
  
-   **Strzałka w prawo:** rozwiń węzeł w drzewie  
  
-   **Strzałka w lewo:** zwinąć węzeł w drzewie  
  
-   **Wprowadź klucz:** zainicjować, obciążenia, należy wykonać wybranego elementu  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (widok drzewa i siatki)  
Formant trid jest złożone formant zawierający widok drzewa w obrębie siatki. Rozwijanie, zwijanie i nawigowanie po drzewie powinna przestrzegać tych samych poleceń klawiatury w widoku drzewa, z następującymi dodatkami:  
  
-   **Strzałka w prawo:** rozwinąć węzeł. Po rozwinięciu węzła należy kontynuować, przechodząc do najbliższej kolumnę po prawej stronie. Na koniec wiersza ma zostać zatrzymana nawigacji.  
  
-   **Karta:** Navigates do najbliższej komórki po prawej stronie.  Na koniec wiersza nawigacji w dalszym ciągu następnego wiersza.  
  
-   **Shift + Tab:** Navigates do najbliższej komórki po lewej stronie.  Na początku wiersza, nawigacji w dalszym ciągu po prawej stronie komórki w poprzednim wierszu.  
  
![Formant trid w programie Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Formant trid w programie Visual Studio