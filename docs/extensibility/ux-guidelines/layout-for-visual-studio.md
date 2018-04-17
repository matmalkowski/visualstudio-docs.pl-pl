---
title: Układ dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e26caa6e47f0f2ee2a20611cf12e166832e007b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="layout-for-visual-studio"></a>Układ dla programu Visual Studio
Większość okien dialogowych programu Visual Studio jest [układu okna dialogowego narzędzia](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), okna dialogowe, które są unthemed standardzie wykonaj [zasad układu okna dialogowego pulpitu systemu Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Podczas przenoszenia programu Visual Studio odświeżyć jej interfejsu użytkownika, niektóre większa okien dialogowych mają nowy projekt, który określa je jako Definiowanie produktu środowiska. Te [układu okna dialogowego motywem](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ma wygląd kompozycji.  
  
##  <a name="BKMK_UtilityDialogLayout"></a> Układ okna dialogowego narzędzia  
  
-   Wszystkich kontrolek w oknie dialogowym narzędzia należy rozpocząć od górnego/lewego i przepływu w dół.  
  
-   Nigdy nie center formantów w oknie dialogowym w celu wypełnienia obszaru duże.  
  
-   Użyj czcionki środowiska dla całego tekstu w oknie dialogowym. Podczas zapisywania visual specyfikacji, określ zamiast zaznaczania określonej czcionki i rozmiar czcionki środowiska. Zobacz [czcionki środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Umożliwia obsługę celem jakości craftsmanship w odstępy formantu spójne i umieszczania.  
  
-   Okna dialogowe może stać się bardziej złożonych z większą liczbą formanty i unikatowe zestawienie formantów. W tych sytuacjach złożonych Zezwalaj odpowiednia ilość miejsca między grupowania formantu umożliwiają użytkownika przepływ logiczny do analizy.  
  
### <a name="utility-dialog-layout-examples"></a>Przykłady układu okna dialogowego narzędzia  
 Wszystkie wymiary są wyrażane jako pikseli.  
  
 ![Okno dialogowe odstępy dla etykiety powyżej formanty](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **Rysunek 08.01-a: Wytyczne odstępy w oknach dialogowych narzędzie z etykietami powyżej formantów**  
  
 ![Okno dialogowe odstępy dla etykiety do lewej strony kontrolki](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **Rysunek 08.01-b: Wytyczne odstępy w oknach dialogowych narzędzie z etykiety na lewo od formantów**  
  
### <a name="layout-details"></a>Szczegóły układu  
  
#### <a name="margins"></a>Marginesy  
  
-   Wszystkie okna dialogowe ma obramowanie 12 piksela wokół krawędzi wszystkie.  
  
-   Marginesy w ramce grupy powinna być 9 pikseli z krawędzi ramki.  
  
-   Marginesy w formancie karty powinna być 6 pikseli z krawędzią formantu karty.  
  
#### <a name="command-buttons"></a>Przyciski poleceń  
  
-   Przyciski poleceń działają na ramki okna dialogowego, a nie na zawartość. Powinna zostać umieszczona na dole prawo, a powinien mieć wystarczającej ilości miejsca zmiennej powyżej, aby skonfigurować osobno osobne przycisków.  
  
-   W przypadku przycisków poziomy, które działają w oknie dialogowym konfiguracji przycisk polecenia jest pionowy stosu w prawym górnym rogu. Zobacz [przyciski poleceń wewnętrzne](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) poniżej.  
  
-   Miejsce na lewo od przyciski poleceń (niższe od lewej/środka okna dialogowego) jest uznawany za część "poza pasmem" formanty okna dialogowego operacji. Jedyną operacją, który powinien mającym w tym miejscu jest łącze pomocy, które jest odpowiednie do zadania ogólnej lub okna dialogowego.  
  
-   Przyciski poleceń powinny być 75 x 23 pikseli.  
  
-   Przyciski poleceń powinny być 6 pikseli od siebie.  
  
 ![Wyrównanie przycisku podstawowe](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
 **Rysunek 08.01 — c: Wyrównanie przycisku podstawowe**  
  
#### <a name="labels"></a>Etykiety  
  
-   Wyrównaj do lewej wszystkich etykiet.  
  
-   Dla etykiet, które znajdują się nad kontrolką one powinien lewej align dokładnie za pomocą formantu poniżej i dołu etykieta powinna być 5 pikseli powyżej górnej innych formantu (na przykład pole kombi).  
  
-   Dla etykiet, które znajdują się na lewo od formantów minimalna szerokość między etykiety i kontrolki wprowadzania jest 10 pikseli. Dorozumiany drugiej kolumny należy ustanowić wyrównywania pola tekstowe, pola kombi lub inne formanty.  
  
-   Etykiety są zdaniu i są z dwukropkiem. Zobacz [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### <a name="distance-between-controls"></a>Odległość między formantami  
 Stos formanty rozsądny sposób. Nie ma żadnych bezwzględną wytyczna odstępów między formantami skumulowany. Szczelność między formantami mogą się nieco różnić między okien dialogowych. Zalecane jest 20 pikseli dla pionowego etykiety kontroli/par i 9 pikseli dla par poziome formantu/etykiety. Odstępy formantu minimalną dla pary poziomy to 6 pikseli.  
  
 ![Zalecane odległość między formantami](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **Rysunek 08.01 — d: Zalecenia dotyczące odległość między formantami**  
  
#### <a name="control-indentation"></a>Wcięcie formantu  
 Jeśli formanty są zagnieżdżone, wyrównanie wewnętrzny formantów w poziomie z lewą krawędzią formantu powyżej, zwykle etykiety.  
  
 ![Zagnieżdżone kontroli nad położeniem](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **Rysunek 08.01 — e: Wyrównanie formantu zagnieżdżone**  
  
#### <a name="control-width"></a>Szerokość formantu  
 Szerokość pola tekstowego lub inne podobne formanty powinny nie przekraczać średni dane wejściowe dla pola. Średnia angielskiej wersji językowej programu word jest pięć znaków. Na przykład pola tekstowego, która wymaga długiej nazwy powinna być tak długo, jak pozwala na układ poziomy, podczas listy rozwijanej nazwy platformy tylko powinna być długości, która umożliwia najdłuższego wpisu.  
  
#### <a name="helper-text"></a>Tekst pomocy  
  
-   Okno dialogowe można wyświetlić tekst pomocy, zawierający więcej informacji dotyczących przeznaczenia okna dialogowego. To zwykle znajduje się u góry i może być zdań 1 i 2.  
  
-   Długość powinna być doświadczenia szerokości dla użytkownika przeanalizować i do odczytu. Okno dialogowe średnia powinna być co najwyżej 550 pikseli szerokości.  
  
####  <a name="BKMK_InteriorCommandButtons"></a> Przyciski poleceń wewnętrzne  
 W oknach dialogowych bardziej złożonych wewnętrznej kontroli może mieć własną przycisków powiązane, które mogą mieć wpływ na którym przycisków zatwierdzania okna dialogowego znajdują się.  
  
-   Wyrównanie w pionie (kolumna) wnętrza przyciski, gdy użycie **OK**/**anulować** poziomie są ukierunkowane w prawym dolnym rogu.  
  
-   Wyrównanie w poziomie (wiersz) wnętrza przyciski, gdy użycie **OK**/**anulować** pionowo są ukierunkowane w prawym górnym rogu. Ta sytuacja jest mniej typowych.  
  
-   Rozmiar przycisku wewnętrzne powinny docelowy rozmiar przycisku standardowe 75 x 23 pikseli, dopasowania rozmiaru **OK**/**anulować** przyciski, gdy jest to możliwe. Jeśli etykieta przycisku sprawia, że przycisk przekracza rozmiar przycisku standardowa, ten rozmiar szersze powinno odpowiadać innych przycisków w tym zestawie.  
  
 ![Przyciski poziome OK i Anuluj](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
 **Rysunek 08.01-f: Pionowy wnętrza przycisków z poziome OK/Anuluj**  
  
 ![Przyciski pionowy OK i Anuluj](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
 **Rysunek 08.01-g: Poziome przycisków wewnętrzne pionowy OK/Anuluj**  
  
#### <a name="browse-button"></a>[Przeglądaj] przycisk  
 **[Przeglądaj]**  przyciski znajdujące się poniżej pola tekstowego powinna pełnych "Przeglądaj..." w całości, w tym wielokropka. Jeśli miejsca jest mocno lub dostępnych jest wiele **[Przeglądaj]**  przyciski na ekranie przycisku można zmniejszyć do właśnie wielokropka.  
  
##  <a name="BKMK_ThemedDialogLayout"></a> Układ okna dialogowego motywów  
 Motywem okien dialogowych w programie Visual Studio mają jaśniejszy wygląd i oferują więcej biały znak. Typografii zawiera więcej nacisk i odsetek, oferując więcej Otwórz odstępy i różnic rozmiary czcionek i wagi. Jeśli to możliwe, chrome i paska tytułu zostały zredukowane lub usunięte. Układ tych okien dialogowych, należy wykonać ten wzorzec podstawowe:  
  
1.  Tło okna dialogowego jest białe.  
  
2.  Szary pośredniej wartość jest obramowanie reguła 1 piksela.  
  
3.  Tytuł okna dialogowego nie znajduje się w pasku tytułu, ale zapewnia visual odsetek i wyróżnienia w większym rozmiarze punktu. (Zobacz sekcję rozmiar czcionki w [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)  
  
4.  Etykiety w połączeniu z dodatkowych tekstu, na przykład opis, powinny być **czcionki środowiska + Bold**.  
  
5.  Wewnętrzne kolumn są oddzielone reguła 1 piksela światła szary.  
  
6.  Domyślne łącza mają nie znaku podkreślenia. Aktywowanie i stanów naciśniętego ma zmiana koloru i podkreślenia.  
  
7.  Zatwierdź przycisków (takich jak **OK**/**anulować**) znajdują się w prawym dolnym rogu.  
  
### <a name="themed-dialog-layout-examples"></a>Przykłady układu okna dialogowego motywów  
 ![Układ okna dialogowego motywem](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **Rysunek 08.01-h: Motywem okna dialogowego**  
  
 ![Wymiary okna dialogowego motywem](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **Rysunek 08.01-i: Motywem okno - wymiarów**  
  
 ![Czcionki okna dialogowego motywem](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **Rysunek 08.01-j: Okno motywem - czcionek**  
  
 ![Kolory motywów okna dialogowego](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **Rysunek 08.01-k: Motywem okno - kolorów**  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Formanty (system Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Okna dialogowe (system Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)