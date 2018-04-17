---
title: Menu i poleceń programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16f67faf7ffe3a3fd119b7ddf002ab463822a830
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu i poleceń programu Visual Studio
## <a name="command-usage"></a>Sposób użycia polecenia  
  
### <a name="overview"></a>Omówienie  
 W przeciwieństwie do programu Microsoft Office, która jest pakietem, który obejmuje wiele oddzielnych produktów, Visual Studio zawiera wiele produktów każdego przyczyniają się ich zestawy poleceń do globalnego programu Visual Studio IDE. IDE zarządza złożoność tysiące polecenia filtrowania funkcji dostępnych dla użytkownika na podstawie kontekstu.  
  
 Podczas zmiany kontekstu użytkownika — takie jak przełączanie z okna projektu do kodu, okno edycji — funkcje niezwiązanych ze sobą na nowy kontekst zniknie. W tym samym czasie, nowych funkcji powierzchni oraz powiązane informacje dynamicznych, takie jak opcje właściwości i przybornika. Użytkownik nie należy zauważyć, wymiana zestawu dostępnych poleceń. Jeśli użytkownik jest efektów lub mylić przez polecenia pojawiające się lub zniknął, projektu interfejsu użytkownika wymaga dostosowania. Bieżącego kontekstu użytkownika jest zawsze wskazane jeden lub więcej sposobów, takich jak w pasku tytułu IDE, okno właściwości lub okna dialogowego strony właściwości.  
  
 Paski poleceń umożliwiają elastyczność w interfejsie użytkownika. Tylko polecenia konstrukcje dostępu do właściwych dla programu Visual Studio środowisku są głównego menu i pasek poleceń głównego, który zarówno można dostosować i nawet ukryte. Inne pasków poleceń pojawiają się i znikają oparte na stan aplikacji. Narzędzia systemu windows i edytory dokumentu może również zawierać osadzone paski narzędzi w ich krawędzi okna.  
  
#### <a name="basic-guidelines"></a>Podstawowe wskazówki  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Korzystanie z istniejących poleceń udostępnionego, grupy poleceń i menu, jeśli to możliwe.  
 Ponieważ polecenia są zwykle wyświetlane na podstawie w kontekście, zastosowanie istniejące udostępnionego menu i grupy polecenia zapewnia, że struktura polecenia pozostaje względnie stabilna między zmiany w kontekście. Ponowne użycie polecenia udostępnionego i wprowadzenie do nowych poleceń bliski pokrewne polecenia udostępnionego również zmniejsza złożoność IDE i tworzy użytkownikom większy komfort pracy. Jeśli nowego polecenia musi być zdefiniowana, spróbuj umieść go w istniejącej grupie udostępnionego polecenia. Jeśli nowej grupy musi być zdefiniowana, umieść go do istniejącego menu udostępnionego bliski grupy pokrewne polecenia przed utworzeniem nowego menu najwyższego poziomu.  
  
##### <a name="do-not-create-icons-for-every-command"></a>Nie należy tworzyć ikony dla każdego polecenia.  
 Należy dokładnie rozważyć przed utworzeniem ikona polecenia. Ikony powinny być tworzone tylko dla polecenia który:  
  
-   są wyświetlane na pasku narzędzi domyślne.  
  
-   prawdopodobnie mają zostać dodane przez użytkowników do narzędzi za pośrednictwem **Dostosuj...**  okna dialogowego.  
  
-   ma ikony skojarzone z tą samą akcją z innym produktem firmy Microsoft.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limit dodawania skróty klawiaturowe  
 Większość użytkowników stosować ułamek niewielki rozmiar wszystkich dostępnych skrótów. W razie wątpliwości, nie należy powiązać z funkcji skrótu klawiaturowego. Pracy za pomocą użytkownika wystąpić zespołu przed dodaniem nowych skrótów.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Nadaj polecenia domyślna lokalizacja menu.  
 Należy pamiętać, że poleceniach zostaną dostosowane przez innych użytkowników i odpowiednio je projekt. Nie ma coś takiego jak ukryte polecenia. Wszystkie polecenia programu Visual Studio są wyświetlane w **Narzędzia > Dostosuj** okna dialogowego, w oknie polecenia, funkcja automatycznego uzupełniania **Narzędzia > Opcje > klawiatury** okno dialogowe i programowanie narzędzia środowiska (DTE). Upewnij się dać poleceniach nazwę i etykietki narzędzia w pliku .ctc, dzięki czemu użytkownicy mogą łatwo je odnaleźć.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Nie zduplikowane udostępnionego polecenia osadzonych paska narzędzi.  
 Warto polecenia należy umieścić w pobliżu obszaru fokus użytkownika. Jednym ze sposobów jest tworzenie osadzonych narzędzi u góry dokumentu lub okna narzędzia edytora. Polecenia umieszczone na pasku narzędzi powinny być specyficzne dla obszar zawartości okna. Nie zduplikowane udostępnionych poleceń na tych pasków narzędzi. Na przykład nigdy nie należy umieścić ikoną "Zapisz" w ramach narzędzi osadzony.  
  
### <a name="content-and-command-visibility"></a>Widoczność zawartości i polecenia  
 Polecenia istnieje w następujących zakresów: **środowiska**, **hierarchii**, i **dokumentu**. Znajomości mają zaufanie położenie polecenia każdego zakresu.  
  
 Polecenia w **środowiska** zakres ustanawia kontekstu podstawowego i są współużytkowane przez wielu kontekstów. Zmiany ich widoczności lub dokumentów i okien narzędzi. Wśród poleceń w środowisku są zakresu **nowy projekt**, **Połącz z serwerem**, **proces Attach**, **Wytnij**,  **Kopiuj**, **Wklej**, **znaleźć**, **opcje**, **dostosować**, **nowe okno**, i **Wyświetl Pomoc**.  
  
 Polecenia w **hierarchii** zakres zarządzania hierarchii w programie Visual Studio, w tym **projektu**, **zespołu**, i **danych**. Odnoszą się do projektu kontekst podrzędny — na przykład **debugowania**, **kompilacji**, **testu**, **architektura**, lub **analizy** . Polecenia w hierarchii zakresu należą **Dodaj nowy element**, **nowe zapytanie**, **ustawienia projektu**, **Dodaj nowe źródło danych**, **Uruchom Kreatora wydajności**, i **nowy Diagram**.  
  
 Polecenia w **dokumentu** act zakres zawartości dokumentu, takie jak kodu projektu i zapytanie o element roboczy (WIQ). Ponadto działania w widoku okna narzędzia lub w przeciwnym razie są specyficzne dla tego okna narzędzia. Polecenia zakresu dokumentu również działać w obiektach plików, które same hierarchii specyficzne dla, takich jak **Usuń z projektu**. Wśród poleceń w dokumencie są zakresu **Refaktoryzuj > Zmień nazwę**, **utworzyć kopii elementu roboczego**, **Rozwiń wszystkie**, **Zwiń wszystkie**, i **Utworzyć zadanie użytkownika**.  
  
### <a name="command-placement-decisions"></a>Decyzje dotyczące umieszczenia polecenia  
 Gdy uznasz utworzyć polecenie, musisz określić położenia odpowiedniej i czy chcesz utworzyć skrót. Tej ścieżki decyzji ustanowienie gdzie umieścić polecenia:  
  
 ![Wykres decyzji — polecenie umieszczania](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 a_CommandPlacement")  
  
 **Decyzja ścieżka do polecenia umieszczania w programie Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Położenie polecenia w menu  
  
#### <a name="main-menu-bar"></a>Pasek menu głównego  
 Na pasku menu główne powinny być standardowe miejsce dla poleceń wszelkie pakiety menu specyficznej dla kontekstu, które przyczyniają się do interfejsu użytkownika. Na pasku menu głównego różni się od innych konstrukcji polecenia, w tym środowisku używa go do kontroli, które polecenia są widoczne. Wszystkie inne pasków poleceń po prostu wyłączyć poleceń, które są poza kontekstem, czy zostały one umieszczone w menu lub na pasku narzędzi.  
  
 Środowisko definiuje zestaw poleceń wbudowane na pasku menu głównego, obejmujące cały IDE i wielu domen zadań. Te polecenia są zawsze widoczne niezależnie od których VSPackages są ładowane do środowiska. Mimo że VSPackages można rozszerzyć ten zestaw poleceń, zestaw z każdego produktu i umieszczania ich poleceń poleceń jest odpowiedzialny za każdego zespołu.  
  
 Struktura głównego menu programu Visual Studio można podzielić na następujące kategorie menu:  
  
##### <a name="core-menus"></a>Menu Core  
  
-   Plik  
  
-   Edytowanie  
  
-   Widok  
  
-   Narzędzia  
  
-   Okno  
  
-   Pomoc  
  
##### <a name="project-specific-menus"></a>Menu specyficznego dla projektu  
  
-   Projekt  
  
-   Kompilacja  
  
-   Debugowanie  
  
##### <a name="context-specific-menus"></a>Menu specyficznej dla kontekstu  
  
-   Zespół  
  
-   Dane  
  
-   Test  
  
-   Architektura  
  
-   Analiza  
  
##### <a name="document-specific-menus"></a>Menu specyficznych dla dokumentu  
  
-   Format  
  
-   tabela  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Podczas projektowania menu głównego, należy stosować się do tych reguł:  
  
-   Nie może przekraczać 25 elementów najwyższego poziomu w podanym kontekście  
  
-   Menu nigdy nie powinna przekraczać 600 pikseli w wysokości.  
  
-   Ocenia menu głównego w wielu sytuacjach, takich jak w wersji Ultimate i profilu ogólne.  
  
-   Menu wysuwane są dozwolone.  
  
-   Menu wysuwane powinien zawierać co najmniej trzy elementy i nie więcej niż 7.  
  
-   Menu wysuwane powinien pojawiać tylko jeden poziom głębokości — niektóre elementy menu programu Visual Studio ma podmenu w kaskadowego, ale nie zaleca tego wzorca.  
  
-   Użyj nie więcej niż sześciu separatorów. Grupy należy stosować się do poniższej ilustracji:  
  
     ![Wytyczne dotyczące grupowanie w menu głównym](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 b_MainMenus")  
  
-   Gdy nie jest wymagane w celu zapewnienia każda grupa na ilustracji, dodawanie dodatkowych grup są ograniczone.  
  
-   Każda grupa ma od dwóch do siedmiu elementów menu.  
  
#### <a name="main-menu-ordering"></a>W menu głównym kolejności  
 Przed dodaniem nowego elementu najwyższego poziomu, należy rozważyć umieszczenie polecenia do istniejącego menu najwyższego poziomu. Podczas dodawania nowego menu najwyższego poziomu, należy umieścić w poprawnej lokalizacji. Zdecyduj, czy menu jest specyficzne dla projektu, kontekstu lub dokumentu. Zachowaj krótkie nazwy menu najwyższego poziomu i korzystać tylko jedno słowo.  
  
 Menu core powinien zakładkę pozostałe polecenia. Plik, Edytuj i wyświetl zawsze należy do lewej, a także narzędzi okna i pomocy powinna zawsze być po prawej stronie.  
  
#### <a name="context-menus"></a>Menu kontekstowe  
 Wprowadzenie zbyt wiele funkcji w menu kontekstowe powoduje interfejs trudne do informacji. Wszystkie główne funkcje powinny być dostępne za pośrednictwem paska menu głównego. Umieszczanie polecenia powinien być uzgodniony z istniejących poleceń, aby uniknąć zduplikowanych poleceń. Menu kontekstowe powłoki definiuje grupy standardowe menu, które mają zostać uwzględnione w zależności od tego, czy menu kontekstowe jest do rozwiązania, węzeł projektu lub elementu projektu.  
  
 Podczas projektowania menu kontekstowe, należy stosować te same reguły, jak w przypadku menu głównego, a ponadto:  
  
-   Nie może przekraczać 25 elementów menu najwyższego poziomu.  
  
-   Menu wysuwane są dozwolone, ale musi przekroczyć głębokości jeden poziom — nigdy nie używaj menu kaskadowych wysuwanych.  
  
-   Użyj nie więcej niż sześciu separatorów.  
  
### <a name="command-placement-in-toolbars"></a>Polecenie umieszczania na paskach narzędzi  
  
#### <a name="general-toolbars"></a>Ogólne paski narzędzi  
 Podczas projektowania i rozmieszczanie paski narzędzi, postępuj zgodnie z tymi standardami:  
  
-   Nie używaj więcej niż jedno zlecenie na przycisku. Jeden z przycisków = jedną akcję.  
  
-   Użyj tekstu obok ikony, tylko wtedy, gdy musi on być wzmocnione z etykietą.  
  
-   Użyj pola kombi wyłącznie dla właściwości, które będzie można przełączyć wiele razy w jednej sesji. W przeciwnym razie ujawnić właściwości w innym miejscu.  
  
-   Szerokość pola kombi powinna być równa szerokości elementu najdłuższym w pole + 30%. Na przykład jeśli element najdłuższym znajduje się 200 pikseli, pola kombi należy 260 pikseli szerokości.  
  
-   Ograniczenia używania separatorów. Korzystanie z separatorem obok listy rozwijanej jest układ wzorzec, ponieważ kształt z listy rozwijanej, sama działa jako separatora wizualnego.  
  
-   Ikona grupy powinna zawierać od 3 do 6 ikon.  
  
-   Jeśli wynik kwalifikatory w wielu poleceń przydatne, użyj przycisku podziału, która przechowuje ostatniego ustawienia:  
  
     ![Podziel przycisków w programie Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 c_SplitButtons")  
  
     **Przykład przycisku podziału. Sześć polecenia po lewej stronie zamiast tego można zmieścić w jeden przycisk.**  
  
#### <a name="product-specific-toolbars"></a>Paski narzędzi określonego produktu  
 Każdy produkt może zapewnić narzędzi domyślny, który zawiera często używane i polecenia ważne i narzędzi domyślną każdego produktu powinna zostać wyświetlona przy pierwszym uruchomieniu programu Visual Studio po instalacji produktu.  
  
 Produkty również powinny wykorzystywać funkcję grup udostępnionych poleceń i menu udostępnianych przez IDE. Każda grupa udostępnionego polecenia jest umieszczany w menu udostępnionego przeznaczone do organizowania pokrewnych poleceń w sposób zrozumiały dla użytkownika. Należy korzystać z tej struktury udostępnionego polecenie, aby zmniejszyć złożoność.  
  
#### <a name="global-toolbars"></a>Globalne paski narzędzi  
 Paski narzędzi globalnych są wymagane do mieści się na jeden wiersz zaraz po jego zainstalowaniu. Podczas tworzenia nowych narzędzi globalnych, postępuj zgodnie z wytycznymi dla tego typu paska narzędzi.  
  
 **Pasek narzędzi ogólne wytyczne:**  
  
-   Każdy narzędzi ma 24 pikseli w formantów wspólnych (uchwytu, przepełnienie).  
  
-   Przycisku paska narzędzi jest 22 pikseli szerokości, w tym dopełnienia. Tworzenie ikony przycisku podziału dodaje innego 11 pikseli szerokości.  
  
-   Duplikowanie poleceń na paski narzędzi jest dozwolone.  
  
 **Paski narzędzi specyficznych dla dokumentu** znajdują się w przypadku niektórych typów plików jest aktywna i znikają w przypadku aktywowania innego typu pliku.  
  
-   Paski narzędzi specyficznych dla dokumentu nie może mieć więcej niż 12 przycisków.  
  
-   Łączna szerokość paska narzędzi nie może przekraczać 300 pikseli.  
  
-   Każdy typ pliku może mieć jeden pasek narzędzi osadzony lub jedną globalnego paska narzędzi specyficznych dla dokumentu, ale nie oba.  
  
 **Paski narzędzi specyficznej dla kontekstu** są wyświetlane po niektórych kontekst jest ustawiona i mogą pozostać aktywne przez dłuższy czas.  
  
-   Limit przycisk wszystkie paski specyficznej dla kontekstu jest 18.  
  
-   Jeśli większość użytkowników spójnie nie stosować ten pasek narzędzi poleceń, gdy kontekst jest aktywny, następnie nie skojarzyć ten pasek narzędzi z kontekstem.  
  
-   Upewnij się, że pasek narzędzi zniknie podczas zamykania kontekstu. Żaden z nich powinna pojawić się podczas uruchamiania.  
  
 **Paski narzędzi z kontekstem nie** nigdy nie są automatycznie wyświetlane. Pokazują, tylko gdy użytkownik aktywuje je. Zachowaj maksymalną szerokość poniżej 200 pikseli.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Ogólne organizacji i grup zdefiniowanych przez powłoki  
 Użyj istniejących poleceń udostępnionego, grupy poleceń i menu. Jeśli nowego polecenia musi być zdefiniowana, spróbuj umieść go w istniejącej grupie udostępnionego polecenia. Jeśli nowej grupy musi być zdefiniowana, spróbuj umieścić go do istniejącego menu udostępnionego bliski grupy pokrewne polecenia przed utworzeniem nowego menu najwyższego poziomu. Pozwala to ograniczyć złożoność polecenia przy jednoczesnym zapewnieniu jej położenie polecenia spójne w IDE.  
  
 Udostępniony **Format** menu, zazwyczaj jest wyświetlana w kontekście systemu windows dokumentu projektanta stylu przedstawiono na poniższej ilustracji:  
  
 ![Visual Studio Format menu z objaśnieniami](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 d_FormatMenu")  
  
 **Grupy menu w programie Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Zmniejszanie i ponowne użycie polecenia  
 Polecenia są zwykle wyświetlane oparte na w kontekście, aby zmniejszyć liczbę poleceń, które użytkownik będzie widział w danym momencie. Jednak również należy używać ponownie istniejących udostępnionego menu i grupy polecenia, aby upewnić się, że struktura polecenia pozostaje względnie stabilna między zmianami w kontekście.  
  
 Ponowne użycie polecenia udostępnionego i wprowadzenie do nowych poleceń bliski pokrewne polecenia udostępnionego zmniejsza się złożoność IDE i tworzy użytkownikom większy komfort pracy.  
  
## <a name="naming-commands"></a>Nazwy poleceń  
  
### <a name="naming-conventions"></a>Konwencje nazewnictwa  
 Polecenie spójne nazewnictwa jest szczególnie ważne, dzięki czemu użytkownicy mogą znaleźć i wykonywać polecenia, albo za pomocą wiersza polecenia lub powiązanie z skrótów klawiaturowych. Nazwy poleceń również pomóc zrozumieć, jakie celu służy polecenie pojawi się na pasku narzędzi lub w menu kaskadowych lub w kontekście użytkownika.  
  
#### <a name="when-naming-commands"></a>Gdy nazw poleceń:  
  
-   Konstruować tekst tak, aby łatwo lokalizowalny. Aby uzyskać więcej informacji na temat lokalizowania tekstu, zobacz [World gotowości dla programu Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Być zwięzły. Polecenia należy używać słowa nie więcej niż trzy.  
  
-   Użyj wielkich liter w nazwach własnych: pierwszą literę każdego wyrazu należy wpisać wielkimi literami. Aby uzyskać więcej informacji dotyczących formatowania tekstu w programie Visual Studio, zobacz [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Wziąć pod uwagę, w którym zostaną umieszczone polecenia. Jest to w menu najwyższego poziomu lub wysuwane okno? Na przykład, gdy grupowanie poleceń w wysuwane okno, a polecenia najwyższego poziomu powinien być "Align" i poleceń menu wysuwane powinien być "Left" "Prawej", "Center", "Justify" itd. Jest zbyteczna nazwę polecenia wysuwane okno "Wyrównaj do lewej" lub "Wyrównaj do prawej".  
  
     ![Visual Studio Format menu](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 a_FormatMenu")  
  
### <a name="using-icons-with-commands"></a>Przy użyciu ikony poleceń  
 W przypadku użycia ikona parowanie z poleceń można Reserve Sparing Table. Mimo że kojarzenie unikatowy obrazu za pomocą polecenia hastens zdolność użytkownika do identyfikowania tego polecenia, bałaganu visual i nieefektywne podejście są wykonywane z nadmierne zużycie obrazu. Następujące reguły pomoc przy podejmowaniu decyzji utworzyć ikonę polecenia.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Ikona za pomocą polecenia tylko wtedy, gdy:  
  
-   Tego samego polecenia zawiera ikonę skojarzona z inną poświęcone produktem firmy Microsoft, takiej jak aplikacje pakietu Microsoft Office.  
  
-   Polecenie zostaną umieszczone na pasku narzędzi domyślne.  
  
-   To polecenie jest polecenie specjalne, które użytkownicy mogą dodać je przy użyciu narzędzi **"Dostosować..."** okna dialogowego.  
  
## <a name="access-and-shortcut-keys"></a>Klucze dostępu i skrótów  
  
### <a name="overview"></a>Omówienie  
 Istnieją dwa rodzaje przypisania klawiszy klawiatury:  
  
-   **Klucze dostępu** (znanej także jako akceleratorów) dostęp do klawiatury za pomocą menu droższe i do każdej etykiety w oknie dialogowym interfejsu użytkownika. Klucze dostępu służą głównie do ułatwień dostępu, są przypisane do wszystkich menu i formantów okna dialogowego większości nie mają być memorized, mają wpływ tylko bieżące okno i są zlokalizowane.  
  
-   **Klawisze skrótu** przede wszystkim użyj formantu (Ctrl) i funkcji (Fn) klucza sekwencji. Są one przeznaczone więcej dla użytkowników zaawansowanych i pomocy w przypadku wydajności. One przypisanych tylko do większości często używanych poleceń i umożliwia szybki dostęp podczas pomijanie menu głównego. Klawisze skrótów mają być memorized i z tego powodu musi być przypisany spójne ze schematem profilu. Skrót klucza schematy może się różnić profilu profilu. Użytkownik może dostosować klawiszy skrótów za pośrednictwem **Narzędzia > Opcje > klawiatury**.  
  
### <a name="assigning-access-keys"></a>Przypisywanie klawiszy skrótów  
 Klawisze dostępu składa się z klawisze Alt plus alfanumeryczne. Przypisz klucz dostępu do poszczególnych elementów menu, bez wyjątku. Postępuj zgodnie z systemu Windows i typowych konwersji dla przypisywanie klawiszy skrótów. na przykład klucz dostępu dla **Plik > Nowy** powinna zawsze być **Alt, F, N**.  
  
 Nie używaj litery jednym pikseli szerokości, takie jak "i" (w wielkich i małych liter) lub małe "l", a znaków z wydłużeń dolnych (g, j p, q i y) są trudne do odróżnienia one.  
  
 Unikaj zduplikowanych klawiszy, jeśli jest to możliwe. W przypadku dublowania nieuniknione menu system obsługuje konflikty cyklicznie przez wszystkie polecenia, które używają klucza. Przykładowo dla hipotetycznego "Number" polecenia w menu Plik, który stanowi duplikat klucza dostępu "N" **Alt, F, N** spowodowałoby utworzenie nowego pliku i **Alt, F, N, N** czy wykonania polecenia "Numer".  
  
### <a name="assigning-shortcut-keys"></a>Przypisywanie klawiszy skrótów  
 Należy unikać przypisywania nowe klawisze skrótów, ponieważ nie są wymagane dla każdego polecenia i podatku systemu (i pamięci użytkownika), jeśli nadmiernego obciążenia. Dane z programu poprawy jakości obsługi klienta (CEIP) wskazuje, że użytkowników programu Visual Studio korzystać tylko mały podzbiór zintegrowane skrótów.  
  
 Podczas definiowania skrótów, należy wykonać następujące czynności:  
  
-   **Użyj kontroli (Ctrl) i funkcji (Fn) klucza sekwencji.**  
  
-   **Zachowaj często używanych skrótów.** Obsługa najpopularniejszych skrótów.  
  
-   **Ułatw Edytor skróty do typu.** Skróty — w typie należy powiązać poleceń, że deweloperzy muszą większość podczas pisania kodu. Na przykład **Edit.InvokeSmartTag** musi mieć klucz szybkie skrótów, takich jak Ctrl +/ i nie Alt + Shift + F10.  
  
-   **Dokładamy wszelkich starań, skróty spójnie motywów.**  
  
-   **Zgodna z wytycznymi systemu Windows, aby określić, które modyfikator kluczy fragmentów.** Użyj kombinacji klawiszy Ctrl dla polecenia, które mają wpływ na dużą skalę, takich jak polecenia mające zastosowanie do całego dokumentu. Użyj kombinacji klawisza Shift poleceń, które rozszerzać lub uzupełniają akcje klawisz skrótu standardowa. Nie należy używać kombinacji klawiszy Ctrl + Alt.  
  
-   **Usuń nadmiarowe skrótów.** Jeśli funkcja starszej wersji, rozważ usunięcie skrótów, które są używane z najwyższą infrequency (mniej niż 10 razy w danych CEIP) lub umiarkowane infrequency (mniej niż 100 razy w danych CEIP), jeśli klucz dostępu zapewnia szybki dostęp do tego samego polecenia. Na przykład: C Alt, H, zostanie otwarty/spis treści pomocy.  
  
 Nie jest prosty sposób sprawdzić dostępność skrótów. Jeśli chcesz dodać skrót, wykonaj następujące kroki:  
  
1.  Sprawdź listę [skróty programu Visual Studio 2013](http://visualstudioshortcuts.com/2013/) do ustalenia, czy są podobne poleceń, aby Twój z grupy.  
  
2.  Przejdź do **Narzędzia > Opcje > środowiska > klawiatury** i testowania skrót. Sprawdź, czy każdy schemat mapowania klawiatury wymienione w obszarze "Zastosuj następujący schemat mapowania klawiatury dodatkowych". Profile ogólne, C#, VB i C++, należy sprawdzić, jak udostępniać te skróty unikatowy. Skrót jest dostępna, jeśli nie jest zmapowany w dowolnej z tych miejscach.