---
title: Obrazów i ikon dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fae6a5350d5204219edcb14732c7686984035e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="images-and-icons-for-visual-studio"></a>Obrazów i ikon dla programu Visual Studio
##  <a name="BKMK_ImageUseInVisualStudio"></a> Obraz używany w programie Visual Studio  
 Przed utworzeniem kompozycji, rozważ przekształcenie Użyj 1000 + obrazy [Biblioteka obrazów w usłudze Visual Studio](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Typy obrazów  
  
-   **Ikony**. Małe obrazy, które są widoczne w poleceń, hierarchii, szablonów i tak dalej. Domyślny rozmiar ikony używane w programie Visual Studio jest PNG 16 x 16. Automatycznie tworzone przez usługę obrazu ikony Generowanie format XAML HDPI pomocy technicznej.  
  
     **Uwaga:** obrazy są używane w systemie menu, nie należy tworzyć ikony dla każdego polecenia. Zapoznaj się [menu i poleceń programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) aby zobaczyć, czy polecenia należy uzyskać ikony.  
  
-   **Miniatury.** Obrazy używane w obszarze podglądu okna dialogowego, takie jak okna dialogowego Nowy projekt.  
  
-   **Okno dialogowe obrazów.** Obrazy, które są wyświetlane w oknach dialogowych lub kreatorów, jako opisową grafiki czy wskaźniki wiadomości. Użyj rzadko i tylko wtedy, gdy jest to niezbędne do zilustrowanie koncepcji trudne lub uzyskania uwagi użytkownika (alertu, ostrzeżenie).  
  
-   **Animowany obrazów.** Używane w wskaźniki postępu, pasków stanu i operacji w oknach dialogowych.  
  
-   **Kursory.** Służy do wskazania, czy operacja jest dozwolona, za pomocą myszy, gdy obiekt może zostać porzucony i tak dalej.  
  
##  <a name="BKMK_IconDesign"></a> Ikona projektu  
  
### <a name="overview"></a>Omówienie  
 Ikony stylu modern, które czystą geometrii i 50/50 saldo plus/minus (jasny/ciemny) i użyj metafory bezpośrednie, zrozumiały dla korzysta z programu Visual Studio. Kluczowe ikonę Centrum punkty projektu wokół przejrzystości, uproszczenie i kontekstu.  
  
-   **Jasności:** skupić się na metaphor core, zawierający ikonę jego znaczenie i indywidualizm.  
  
-   **Uproszczenie:** zmniejszyć ikony znaczenia core — pobranie motywu tylko niezbędne elementy i nie frills.  
  
-   **Kontekst:** należy wziąć pod uwagę wszystkie aspekty ikona roli podczas tworzenia koncepcji, który ma kluczowe znaczenie podczas podejmowania decyzji o elementy, które stanowią metaphor core ikony.  
  
 Ikony istnieje wiele punktów projektu, aby uniknąć:  
  
-   Nie należy używać ikony, które wskazują elementy interfejsu użytkownika, z wyjątkiem, gdy jest to konieczne. Wybierz podejście bardziej abstrakcyjny lub symbolicznych, jeśli element interfejsu użytkownika nie jest ani wspólne, manipulacji, ani unikatowy.  
  
-   Nie nadużywać wspólne elementy, takie jak dokumentów, foldery, strzałki i lupę. Użyj tych elementów tylko wtedy, gdy jest to istotne znaczenie tej ikony. Na przykład Lupa prawej powinny wskazywać tylko wyszukiwanie, przeglądanie i znajdowanie.  
  
-   Mimo że niektóre elementy starsza wersja ikony Obsługa korzystanie z perspektywy, nie należy tworzyć nowe ikony z perspektywy chyba, że element nie jest przejrzyste bez niego.  
  
-   Nie cram zbyt dużej ilości informacji do ikony. Proste obrazu, który można łatwo rozpoznać lub rozpoznane jako symbolu rozpoznawalnych przydaje się bardziej niż zbyt skomplikowane obrazu. Ikona nie wiadomo, cały artykuł.  
  
### <a name="icon-creation"></a>Tworzenie ikony  
  
#### <a name="concept-development"></a>Programowanie koncepcji  
 Visual Studio w jego interfejsie użytkownika zawiera szereg różnych typów ikony. Należy rozważyć typ ikony, podczas tworzenia. Nie używaj jasne lub rzadko obiektów interfejsu użytkownika dla elementów ikony. Wybrać symboliczne w tych przypadkach, takich jak ikoną tagów inteligentnych. Należy pamiętać, że znaczenie abstrakcyjny tagu po lewej stronie bardziej oczywistymi niż wersja niezrozumiała, oparty na interfejsie użytkownika po prawej stronie:  
  
|||  
|-|-|  
|**Prawidłowe użycie symboliczne obrazów**|**Nieprawidłowe użycie symboliczne obrazów**|  
|![Ikony jest poprawna tagów inteligentnych](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404 01_SmartTagCorrect")|![Niepoprawne ikona tagów inteligentnych](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 02_SmartTagIncorrect")|  
  
 Istnieją sytuacje, w których działają elementy interfejsu użytkownika standardowego, zrozumiała dla ikony. Dodaj się, że okno jest jednym z przykładów:  
  
|||  
|-|-|  
|**Poprawne elementu interfejsu użytkownika w ikony**|**Nieprawidłowy element interfejsu użytkownika w ikony**|  
|![Ikony jest poprawna okno Dodawanie](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 03_AddWindowCorrect")|![Niepoprawne ikonę okna Dodawanie](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 04_AddWindowIncorrect")|  
  
 Nie używaj dokumentu jako podstawowy element, chyba że jest istotne znaczenie tej ikony. Bez dokumentu elementu na dodawanie dokumentu (patrz poniżej) znaczenie zostało utracone lub z odświeżania jest niepotrzebne do komunikowania się znaczenie element dokumentu.  
  
|||  
|-|-|  
|**Prawidłowe użycie ikonę dokumentu**|**Nieprawidłowe użycie ikonę dokumentu**|  
|![Ikony jest poprawna dokumentu](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 05_DocumentIconCorrect")|![Niepoprawne ikonę dokumentu](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 06_DocumentIconIncorrect")|  
  
 Pojęcie "Pokaż" powinny być reprezentowane przez ikonę, która najlepiej ilustruje, co jest wyświetlane, takie jak w przykładzie Pokaż wszystkie pliki. Metaphor obiektyw może być służy do wskazania pojęcie "Widok", w razie potrzeby, takie jak w przykładzie widok zasobów.  
  
|||  
|-|-|  
|**"Show"**|**"View"**|  
|![Pokaż ikonę](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 07_Show")|![Ikona widoku](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 08_View")|  
  
 Wskazująca w prawo powiększanie ikonę szkła powinien reprezentują wyszukiwanie tylko, wyszukiwania i przeglądania. Wariant lewej ze znakiem plus lub minus powinien reprezentują tylko Powiększ / pomniejszyć.  
  
|||  
|-|-|  
|**"Wyszukiwanie"**|**"Powiększenia"**|  
|![Ikona wyszukiwania](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 09_Search")|![Ikona powiększenia](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 10_Zoom")|  
  
 W widokach drzewa nie używać ikonę folderu i modyfikujący. Jeśli to możliwe, używaj tylko modyfikatora.  
  
|||  
|-|-|  
|**Poprawne drzewa widoku ikon**|**Ikony widoku drzewa nieprawidłowa**|  
|![Ikona widoku drzewa poprawne &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![ikona widoku drzewa poprawne &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![Ikona widoku drzewa nieprawidłowa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![ikona widoku drzewa nieprawidłowa &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 14_ TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Styl Szczegóły  
  
#### <a name="layout"></a>Układ  
 Elementy stosu pokazany dla standardowych ikon 16 x 16:  
  
 ![Stos układu dla ikony 16 x 16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 15_LayoutStack")<br />Stos układu dla ikony 16 x 16
  
 Stan powiadomienia elementy są bardziej używanego jako autonomiczny ikon. Istnieją kontekstów, jednak, w których powiadomienie powinny być skumulowany na base element takich jak ikoną zadanie ukończone:  
  
 ![Autonomiczny powiadomień w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")<br />Autonomiczny ikony powiadomień
  
 ![Ikona ukończenia zadania](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 17_TaskComplete")<br />Ikona ukończenia zadania
  
 Ikony projektu są zazwyczaj pliki ICO, które zawierają różne rozmiary. Większość ikon 16 x 16 zawierają te same elementy. Wersje 32 x 32 mają więcej szczegółów, w tym typ projektu, jeśli jest to wymagane.  
  
 ![Projekt ikony w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")<br />Ikony projektu biblioteki kontrolki Windows VB, 16 x 16 i 32 x 32 
  
 Centrum ikony w swojej ramce pikseli. Jeśli nie jest to możliwe, wyrównanie ikony do góry i/lub prawo do ramki.  
  
 ![Ikona wyśrodkowany w ramce pikseli](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 19_IconCentered")<br />Ikona wyśrodkowany w ramce pikseli
  
 ![Ikona wyrównany do prawej ramki pikseli z góry](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 20_IconTopRight")<br />Ikona wyrównane do górnej prawo do ramki
  
 ![Ikona wyśrodkowany i wyrównane do górnej ramki pikseli](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 21_IconTopAlign")<br />Ikona wyśrodkowany i wyrównane do górnej ramki
  
 Uzyskanie idealne wyrównanie i saldo, należy unikać utrudniają działanie tej ikony element base z akcji symboli. Umieść symbolu u góry po lewej elementu podstawowego. Podczas dodawania dodatkowy element, należy wziąć pod uwagę wyrównanie i saldo ikony.  
  
|||  
|-|-|  
|**Wyrównanie poprawne i saldo**|**Nieprawidłowe wyrównanie i saldo**|  
|![Popraw saldo ikonę i wyrównanie](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![Ikona niepoprawne saldo i wyrównanie](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|  
  
 Upewnij się, parzystości rozmiar ikon, elementy, które są używane w zestawach. Należy pamiętać, że w niepoprawne parowanie kółko i Strzałka są zbyt duże i nie są zgodne.  
  
|||  
|-|-|  
|**Parzystość odpowiedni rozmiar**|**Niepoprawny rozmiar parzystości**|  
|![Popraw rozmiar ikon i parzystość](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 24_SizeParityCorrect")|![Ikona niepoprawny rozmiar i parzystość](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 25_SizeParityIncorrect")|  
  
 Użyj wiersza spójne i wagi visual. Należy ocenić, jak ikony, które tworzysz porównuje innych ikony przez porównanie side-by-side. Nigdy nie używaj całą ramkę 16 x 16, użyj 15 x 15 lub mniejsza. Powinien być 50/50 ujemna dodatnie stosunek (ciemny światła).  
  
|||  
|-|-|  
|**Poprawne stosunek ujemna dodatnie**|**Niepoprawne stosunek ujemna dodatnie**|  
|![Popraw visual waga dla ikony &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![Popraw visual waga dla ikony &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![Popraw visual waga dla ikony &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![Nieprawidłowa waga visual dla ikony](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 29_VisualWeightIncorrect")|  
  
 Do tworzenia elementów bez ograniczania integralności elementu, należy użyć kształtów proste, można porównywać i kąty dopełniający. Jeśli to możliwe, należy użyć kątów 45 lub 90°.  
  
 ![Popraw kąty ikona](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspektywa  
 Zachowaj ikonę Wyczyść i zrozumieć. Za pomocą perspektywy i źródła światła tylko wtedy, gdy jest to konieczne. Chociaż należy unikać za pomocą perspektywy dla elementów, ikona, niektóre elementy są nierozpoznawalną bez niego. W takich przypadkach stylizowane perspektywy komunikuje się jasności elementu.  
  
 ![perspektywy punktu 3](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 31_3PointPerspective")<br />perspektywy punktu 3
  
 ![perspektywy punktu 1](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 32_1PointPerspective")<br />perspektywy punktu 1
  
 Większość elementów powinny być skierowane lub pod kątem z prawej strony:  
  
 ![Ikony pod kątem prawo](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 33_AngledRight")  
  
 Użyj źródła światła tylko podczas dodawania jasności niezbędne do obiektu.  
  
|||  
|-|-|  
|**Poprawnego źródła światła**|**Niepoprawne źródła światła**|  
|![Popraw źródła światła dla ikony](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![Niepoprawne źródła światła dla ikony](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|  
  
 Użyj zawiera tylko w celu zwiększenia czytelności lub lepszego przekazywania metaphor. Dodatnia wartość ujemna saldo (ciemny światła) powinna być 50/50.  
  
|||  
|-|-|  
|**Prawidłowe użycie konspektów**|**Nieprawidłowe użycie konspektów**|  
|![Popraw opisanych](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 36_OutlinesCorrect")|![Zawiera niepoprawne](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Typy ikon  
 **Skorupach i polecenia paska** ikony składają się z maksymalnie trzech z następujących elementów: jeden podstawowy, jeden modyfikator, akcji lub jeden stan.  
  
 ![Przykłady skorupach i polecenia pasek ikon](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 38_ShellIcons")<br />Przykłady skorupach i polecenia pasek ikon
  
 **Pasek poleceń okna narzędzia** ikony składają się z maksymalnie trzech z następujących elementów: jeden podstawowy, jeden modyfikator, akcji lub jeden stan.  
  
 ![Przykłady okna narzędzia polecenia pasek ikon](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")<br />Przykłady ikony paska poleceń okna narzędzi
  
 **Disambiguator widoku drzewa** ikony składają się z maksymalnie trzech z następujących elementów: jeden podstawowy, jeden modyfikator, akcji lub jeden stan.  
  
 ![Przykłady drzewa widoku ikon disambiguator](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 40_TreeViewIcons")<br />Przykłady drzewa widoku ikon disambiguator
  
 **Taksonomii oparte na stanie wartość** ikony istnieje w następujących stanów: aktywne, aktywne wyłączone i wyłączone nieaktywne.  
  
 ![Przykłady ikon taksonomii oparte na stanie wartość](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")<br />Przykłady ikon taksonomii wartość oparte na stanie
  
 **IntelliSense** ikony składają się z maksymalnie trzech z następujących elementów: jeden podstawowy, jeden modyfikator i jeden stan.  
  
 ![Przykłady ikon IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 42_IntelliSenseIcons")<br />Przykłady ikon IntelliSense
  
 **Małe (16 x 16) projektu** ikony powinna mieć nie więcej niż dwa elementy: jednego typu podstawowego i jeden modyfikator.  
  
 ![Przykłady małe (16 x 16) projektu ikony](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 43_16x16Project1") ![ikona 16 x 16 projektu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 44_16x16Project2") ![ikona 16 x 16 projektu &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 45_16x16Project3")<br />Przykłady małych ikon projektu (16 x 16)
  
 **Duże projektu (32 x 32)** ikony zawierać nie więcej niż cztery następujące elementy: jeden podstawowy, Modyfikatory jednej do dwóch i jeden język nakładki.  
  
 ![Przykłady duże (32 x 32) projektu ikony](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 46_32x32Project")<br />Przykłady dużych ikon projektu (32 x 32)
  
### <a name="production-details"></a>Szczegóły produkcji  
 Wszystkie nowe elementy interfejsu użytkownika należy utworzyć przy użyciu systemu Windows Presentation Foundation (WPF), a wszystkie nowe ikony dla WPF powinna mieć format PNG 32-bitowych. PNG 24-bitowego jest starszego formatu, który nie obsługuje przezroczystość i dlatego nie jest zalecana dla ikon.  
  
 Zapisz rozdzielczości 96 DPI.  
  
#### <a name="file-types"></a>Typy plików  
  
-   **PNG 32-bitowe:** w formacie ikon. Dane bezstratny kompresji formacie, który może przechowywać obrazów rastrowych pojedynczego (w pikselach). 32-bitowe pliki PNG obsługuje kanał alfa przezroczystości, korekcja gamma i przeplotu.  
  
-   **32-bitowe BMP:** dla formantów z systemem innym niż WPF. Skrót, Windows XP lub kolor wysoka, BMP 32-bitowych jest to format obrazu RGB/A, obraz true koloru z kanału alfa przezroczystości. Kanał alfa to warstwa przezroczystość wymienionych na liście Adobe Photoshop, który następnie jest zapisywana w map bitowych jako dodatkowe (czwarty) kanału koloru. Czarne tło jest dodawany podczas produkcji kompozycji do wszystkich plików BMP 32-bitowych, aby zapewnić szybkie wizualnie o głębi kolorów. Ta czarnym tle reprezentuje obszaru do zamaskowania wychodzących w interfejsie użytkownika.  
  
-   **32-bitowe ICO:** ikon projektu i Dodawanie elementu. Wszystkie pliki ICO są true kolor 32-bitowy z kanału alfa przezroczystości (RGB/A). Ponieważ pliki ICO można przechowywać wielu rozmiarów i liczby kolorów, Vista ikony są często w formacie ICO zawierające 16 x 16, 32 x 32 48 x 48 i rozmiary obrazów 256 x 256. Aby można było wyświetlać się poprawnie w Eksploratorze Windows, pliki ICO musi być zapisany rozwijanej liczby 24-bitowego i 8-bitowych kolorów dla każdego rozmiaru obrazu.  
  
-   **XAML:** powierzchni projektowania i definiowania układu systemu Windows. Ikony XAML są pliki obrazów wektorowej, które obsługują skalowanie, obracanie zgłoszenia i przezroczystość. Nie są obecnie często używane w programie Visual Studio, ale stają się coraz bardziej popularne ze względu na ich elastyczność.  
  
-   **SVG**  
  
-   **BMP 24-bitowego:** na pasku poleceń Visual Studio. Format obrazu true kolor RGB BMP 24-bitowego jest Konwencja ikonę, która tworzy warstwę przezroczystości przy użyciu amarantowy (R = 255, G = 0, B = 255) jako klucz kolor warstwę w poziomie przeciwstukowe przezroczystości. W BMP 24-bitowego wszystkie powierzchnie amarantowym są wyświetlane na kolor tła.  
  
-   **GIF 24-bitowego:** na pasku poleceń Visual Studio. Wartość true kolor RGB obrazu formacie, który obsługuje przezroczystość. GIF — pliki są często używane w Kreatorze kompozycji i animacji GIF.  
  
### <a name="icon-construction"></a>Ikona konstrukcji  
 Najmniejszy rozmiar ikony w programie Visual Studio jest 16 x 16. Największy wspólny użycie jest 32 x 32. Należy pamiętać, nie w celu wypełnienia całego ramki 16 x 16, 24 x 24 lub 32 x 32 podczas projektowania ikony. Ikona czytelne, jednolity konstrukcji jest niezbędne do rozpoznawania użytkownika. Podczas kompilowania ikony, należy stosować się do następujących punktów.  
  
-   Ikony powinna być Wyczyść, zrozumienia i spójne.  
  
-   Zaleca się, użyj elementów powiadomień stan jako pojedynczy ikony, a nie stosu je na górze ikonę element base. W niektórych kontekstach interfejsu użytkownika może wymagać elementu stanu, aby łączyć się z elementu podstawowego.  
  
-   Ikony projektu są zazwyczaj pliki ICO, które zawierają kilku rozmiarów. Trwa aktualizowanie tylko ikony 16 x 16, 24 x 24 i 32 x 32. Większość ikon 16 x 16 i 24 x 24 będzie zawierać te same elementy. Ikony 32 x 32 zawierają więcej szczegółów, w tym typu język projektu, jeśli ma to zastosowanie.  
  
-   Ikony 32 x 32 podstawowe elementy mają zwykle grubość linii 2 pikseli. Grubość linii 1 lub 2 pikseli może służyć do szczegółów elementów. Użyj najlepsze własnym zdrowym rozsądkiem, aby ustalić, które jest bardziej odpowiednie.  
  
-   Ma co najmniej 1 piksela odstępy między elementami dla 16 x 16 i ikony 24 x 24. Ikony 32 x 32 użyć 2 pikseli odstępy między elementami i między modyfikator i base element.  
  
 ![Element odstępy dla ikony o rozmiarze 16 x 16, 24 x 24 i 32 x 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 47_ElementSpacing")<br />Odstępy elementów ikon o rozmiarze 16 x 16, 24 x 24 i 32 x 32
  
#### <a name="color-and-accessibility"></a>Kolor i ułatwień dostępu  
 Wytycznych dotyczących zgodności programu Visual Studio wymaga, że wszystkie ikony w produkcie przekazać wymagania związane z dostępem do kolorów i kontrastu. Jest to osiągane przez odwracanie ikonę, a podczas projektowania, należy pamiętać, że będą one być programowo zmieniany w produkcie.  
  
 Aby uzyskać więcej informacji na temat używania kolorów w Visual Studio ikony, zobacz [przy użyciu kolorów w obrazach](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a> W przypadku obrazów przy użyciu kolorów  
  
### <a name="overview"></a>Omówienie  
 Ikony w programie Visual Studio są głównie monochromatyczny. Kolor jest zarezerwowana do przekazywania określonych informacji i nigdy nie dekoracji. Kolor jest używany:  
  
-   Aby wskazać, akcja  
  
-   Aby powiadomienia o stanie użytkownika  
  
-   można określić przynależność do języka  
  
-   rozróżnianie elementów w obrębie IntelliSense  
  
### <a name="accessibility"></a>Ułatwienia dostępu  
 Wytycznych dotyczących zgodności programu Visual Studio wymaga, że wszystkie ikony zaznaczone w przebiegu produktu wymagania związane z dostępem do kolorów i kontrastu. Kolorów w palecie języka visual zostały przetestowane i spełnić te wymagania.  
  
#### <a name="color-inversion-for-dark-themes"></a>Odwracanie kolorów dla ciemnego motywów  
 Aby ustawić ikony wyświetlane ze stosunek poprawne kontrastu w ciemny motyw programu Visual Studio, odwracanie jest stosowany programowo. Kolory w tym przewodniku zostały wybrane w części, aby ich Odwróć poprawnie. Ogranicz do tej palety kolorów lub otrzymasz nieprzewidywalne skutki, po zastosowaniu odwracanie.  
  
 ![Przykłady ikony, które miały ich kolory odwrócony](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 01_DarkThemeInversion")<br />Przykłady ikony, które miały nich odwrócone kolory
  
### <a name="base-palette"></a>Podstawowy palety  
 Wszystkie standardowe ikony zawiera trzy podstawowe kolorów. Ikony zawierają nie gradientach lub cieni z co najmniej dwa wyjątki dla ikony narzędzia 3D.  
  
|Użycie|Nazwa|Wartość (motywu jasny)|Próbki|Przykład|  
|-----------|----------|---------------------------|------------|-------------|  
|Tło/ciemny|VS BG|424242 / 66,66,66|![Próbka 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Przykład podstawowego palety](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 02_BasePaletteExample")|  
|Pierwszego planu/lekki|VS FG|F0EFF1 / 240,239,241|![Próbka F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Kontur|VS limit|F6F6F6 / 246,246,246|![Próbka F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Oprócz podstawowego kolory każda z ikon może zawierać jeden dodatkowe kolor z palety rozszerzonej.  
  
### <a name="extended-palette"></a>Rozszerzone palety  
  
#### <a name="action-modifiers"></a>Modyfikatory akcji  
 Cztery kolory poniżej wskazują typy akcji wymaganych przez Modyfikatory akcji:  
  
|Użycie|Nazwa|Wartość (wszystkie motywów)|Próbki|  
|-----------|----------|--------------------------|------------|  
|Dodatnie|Zielony akcji VS|388A34 / 56,138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Ujemne|Czerwony akcji VS|A1260D / 161,38,13|![Próbka A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutralna|Niebieski akcji VS|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Utwórz nowy|Kolor pomarańczowy akcji VS|C27D1A / 194,156,26|![Próbka C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Przykłady  
 Zielony służy do Modyfikatory dodatnią akcji, takich jak "Dodaj", "Wykonywania," "Play" i "Weryfikacji."  
  
|||||  
|-|-|-|-|  
|![Uruchomienie ikonę](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Uruchom|![Wykonanie kwerendy ikona](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 04_ExecuteQuery")<br />Wykonanie kwerendy|![Odtwórz wszystkie ikony procedury](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 05_PlayAllSteps")<br />Odtwórz wszystkie kroki|![Dodaj formant ikona](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 06_AddControl")<br />Dodawanie formantu|  
  
 Czerwony służy do Modyfikatory ujemna akcji, takich jak "Delete", "Zakończ", "Anuluj" i "Zamknij".  
  
|||||  
|-|-|-|-|  
|![Ikona relacji usuwania](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 07_DeleteRelationship")<br />Usuwanie relacji|![Ikona kolumna usunąć](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 08_DeleteColumn")<br />Usuwanie kolumn|![Ikona zapytania stop](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 09_StopQuery")<br />Zatrzymaj kwerendę|![Ikona w trybie offline połączenia](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 10_ConnectionOffline")<br />Połączenia w trybie Offline|  
  
 Niebieski jest stosowany do akcji neutralne Modyfikatory najczęściej reprezentowane jako strzałki, takie jak "Otwórz," "Dalej", "Wstecz", "Zaimportować" i "Eksportuj".  
  
|||||  
|-|-|-|-|  
|![Przejdź do pola ikona](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 11_GoToField")<br />Przejdź do pola|![Umieścić w zadaniu wsadowym wyboru&#45;w ikonę](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 12_BatchedCheckIn")<br />Wsadowej operacji zaewidencjonowania|![Ikona Edytor adres](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 13_AddressEditor")<br />Edytor adresów|![Ikona Edytor skojarzenia](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 14_AssociationEditor")<br />Edytor skojarzenia|  
  
 Ciemny złota jest używany głównie dla modyfikator "New".  
  
|||||  
|-|-|-|-|  
|![Ikona nowego projektu](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 15_NewProject")<br />Nowy projekt|![Utwórz nową ikonę wykres](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 16_CreateNewGraph")<br />Utwórz nowy wykres|![Ikona nowego testu jednostki](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 17_NewUnitTest")<br />Nowego testu jednostkowego|![Ikonę Nowy element listy](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 18_NewListItem")<br />Nowy element listy|  
  
#### <a name="special-cases"></a>Specjalne przypadki  
 W szczególnych przypadkach modyfikator kolorowe akcji może być używany niezależnie jako ikonę autonomicznych. Kolor ikony odzwierciedla akcje, które jest skojarzona ikona. To jest ograniczona do małego podzbioru ikony, w tym:  
  
||||||  
|-|-|-|-|-|  
|![Uruchomienie ikonę](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Uruchom|![Ikona stop](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 19_Stop")<br />Zatrzymywanie|![Ikona usuwania](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 20_Delete")<br />Usuwanie|![Zapisz](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 21_Save")<br />Zapisanie|![Przejdź wstecz ikona](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 22_NavigateBack")<br />Przejdź do tyłu|  
  
### <a name="code-hierarchy-palette"></a>Kod hierarchii palety  
  
#### <a name="folder"></a>Folder  
  
|Użycie|Nazwa|Wartość (wszystkie motywów)|Próbki|Przykład|  
|-----------|----------|--------------------------|------------|-------------|  
|Foldery|Folder|DCB67A / 220,182,122|![Próbka DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona kolor folderu](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Visual Studio języki  
 Każdy z typowych języków lub platform dostępne w programie Visual Studio ma skojarzone kolor. Te kolory ikonę podstawowej lub Modyfikatory języka, pojawiające się w prawym górnym rogu złożone ikon.  
  
|Użycie|Nazwa|Wartość (wszystkie motywów)|Próbki|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|Niebieski HTML WPF ASP|0095D 7 / 0,149,215|![Próbka 0095 D 7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|Purpurowy CPP|9B4F96 / 155,79,150|![Próbka 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS zielony (zielony akcji VS)|388A34 / 56,138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|Czerwony CSS|BD1E2D / 189,30,45|![Próbka BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|Purpurowy FS|672878 / 103,40,120|![Próbka 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|Kolor pomarańczowy JS|F16421 / 241,100,33|![Próbka F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|Niebieski VB (VS akcji niebieski)|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|Kolor pomarańczowy usług terminalowych|E04C06 / 224,76,6|![Próbka E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|Kopiuj zielony|879636 / 135,150,54|![Próbka 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Przykłady ikon z języka modyfikatorów  
  
|||||||  
|-|-|-|-|-|-|  
|![Ikona Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 25_VB")<br />VB|![C&#35; ikona](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 26_CSharp")<br />C#|![C&#43;&#43; icon](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; ikona](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 28_FSharp")<br />F#|![Ikona JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 29_JavaScript")<br />JavaScript|![Ikona Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 30_Python")<br />Python|  
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 31_HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 32_WPF")<br />WPF|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 33_ASP")<br />ASP|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 34_CSS")<br />CSS|![Ikona typeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 35_TypeScript")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 Ikony IntelliSense używać palety kolorów wyłącznego. Kolorów te służą do użytkowników szybko rozróżnienie dwóch różnych elementów na liście podręcznego IntelliSense.  
  
|Użycie|Nazwa|Wartość (wszystkie motywów)|Próbki|  
|-----------|----------|--------------------------|------------|  
|Klasa zdarzeń|Kolor pomarańczowy akcji VS|C27D1A / 194,125,26|![Próbka C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Metody rozszerzenia, delegat metody, moduł,|Purpurowy akcji VS|652D 90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Pola, elementu wartości wyliczeniowej, makra, struktury, typ wartości Unii, operatora, interfejs|Niebieski akcji VS|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Obiekt|Zielony akcji VS|388A34 / 56,138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Stała, wyjątku, element Enum, mapy, element mapy, Namespace, szablon, definicji typu|Tła (VS BG)|424242 / 66,66,66|![Próbka 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Przykłady ikon IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Ikona Klasa IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 36_IntelliSenseClass")<br />Class|![Ikona Zdarzenie prywatne IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent")<br />Zdarzenie prywatne|![Ikona delegata IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 38_IntelliSenseDelegate")<br />Delegate|![Ikona friend metody IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend")<br />Friend — metoda|![Ikona pola](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 40_Field")<br />Pole|  
|![Ikona elementu enum chronione IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem")<br />Chroniony element wyliczenia|![Ikona obiektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 42_IntelliSenseObject")<br />Obiekt|![Ikona szablonu IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 43_IntelliSenseTemplate")<br />Szablon|![Ikona skrótu wyjątek IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut")<br />Skrót wyjątku||  
  
### <a name="notifications"></a>Powiadomienia  
 Powiadomień w programie Visual Studio są używane do wskazywania stanu. Palety powiadomień używa następujących czterech kolorów, a także Opcje wypełnienia biały lub czarny pierwszego planu, w celu zdefiniowania powiadomienia o następujących poziomach stanu.  
  
|Użycie|Nazwa|Wartość (wszystkie motywów)|Próbki|  
|-----------|----------|--------------------------|------------|  
|Stan: neutralne|Niebieski powiadomienia (na niebiesko VS)|1BA1E2 / 27,161,226|![Próbka 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Stan: dodatnią|Zielony powiadomienia (zielony VS)|339933 / 51,153,51|![Próbka 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Stan: ujemna|Powiadomienie czerwony (czerwony VS)|E51400 / 229,20,0|![Próbka E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Stan: ostrzeżenie|Powiadomienia, żółty (kolor pomarańczowy VS)|FFCC00 / 255,204,0|![Próbka FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Wypełnienie pierwszego planu|Czarne powiadomienia (czarny)|000000 / 0,0,0|![Próbka &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Wypełnienie pierwszego planu|Białe powiadomienia (biały)|FFFFFF / 255,255,255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Przykłady ikony powiadomień  
  
|||||  
|-|-|-|-|  
|![Ikona alertu](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 45_Alert")<br />Alert|![Ikona ostrzeżenia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 48_Warning")<br />Ostrzeżenie|![Ikona pełną](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 46_Complete")<br />Zakończenie|![Ikona stop](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 47_Stop")<br />Zatrzymywanie|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 Ogólnie rzecz biorąc Visual Studio Online składa się z funkcji obsługiwanych w przeglądarce. Kolor może być różna w różnych środowiskach, ale styl jest taka sama.  
  
|Grupa|Użycie|Nazwa|Wartość (wszystkie motywów)|Próbki|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Tło|TFSO BG|656565/ 101, 101, 101|![Próbka 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Kontur|TFSO LIMIT|FFFFFF / 255 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Tło|biały|FFFFFF / 255 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Tło|biały|FFFFFF / 255 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Tło|biały|FFFFFF / 255 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normalny|F12 Grey_Primary|555555 / 85, 85, 85|![Próbka 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Umieść kursor|F12 Blue_Hover|2279BF / 34,121,191|![Próbka 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Wyłączone|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Próbka ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Umieść kursor w tle|Umieść kursor bg|D9EBF7 / 217,235,247|![Próbka D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Tło wciśnięty|Bg wciśnięty|B2D7F0 / 178,215,240|![Próbka B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Kontur|VS LIMIT|F6F6F6 / 246,246,246|![Próbka F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Informacje|Informacje|00BCF2 / 0,188,242|![Próbka 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Ostrzeżenie|Ostrzeżenie|F28300 / 242,131,0|![Próbka F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Błąd / ujemna|Error_Negative|E81123 / 232,17,35|![Próbka E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Start / dodatnią|Start_Positive|009E49 / 0,158,73|![Próbka 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Typ podziału|Typ podziału|9B4F96 / 155,79,150|![Próbka 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Oznacz zdarzeń|Oznacz zdarzeń|A51F00 / 165,31,0|![Próbka A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Oznacz użytkownika|Oznacz użytkownika|F16220 / 241,98,32|![Próbka F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Przykłady programu Visual Studio Online ikon  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Ikona zespołu TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 49_TFSOnlineTeam")<br />Zespół usługi online|![Ikona informacji TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 50_TFSInformation")<br />Informacje|![Ikona historii TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 51_TFSHistory")<br />Historia|![Ikona gałęzi TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 52_TFSBranch")<br />Odgałęzienie|  
  
|Napa||||  
|----------|-|-|-|  
|![Ikona zawartości Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 53_NapaContent")<br />Zawartość|![Ikona poczty office Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 54_NapaOfficeMail")<br />Office poczty|![Ikona programu SharePoint Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 55_NapaSharePoint")<br />Program SharePoint|![Ikona w okienku zadań Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 56_NapaTaskPane")<br />Okienka zadań|  
  
|Monaco||||  
|------------|-|-|-|  
|![Ikona pliki Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 57_MonacoFiles")<br />Pliki|![Ikona Monaco Git](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 58_MonacoGit")<br />Git|![Ikona wyszukiwania Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 59_MonacoSearch")<br />Wyszukaj|![Ikona tekstu Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 60_MonacoText")<br />Tekst|  
  
|F12|||  
|---------|-|-|  
|![Ikona kodu pretty F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 61_F12PrettyCode")<br />Łatwa kodu|![Ikona ostrzeżenia F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 62_F12Warning")<br />Ostrzeżenie|![Ikona emulować F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 63_F12Emulate")<br />Emulowanie|