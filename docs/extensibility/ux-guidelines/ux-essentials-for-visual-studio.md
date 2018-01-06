---
title: "Podstawowe informacje dotyczące środowiska użytkownika dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f9d04da421b3b59609269b4f91a487d22adc80e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ux-essentials-for-visual-studio"></a>Podstawowe informacje dotyczące środowiska użytkownika dla programu Visual Studio
## <a name="best-practices"></a>Najlepsze praktyki  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Być zgodne w środowisku Visual Studio.  
  
-   Postępuj zgodnie z istniejącą [wzorce interakcji](interaction-patterns-for-visual-studio.md) powłoki.  
  
-   Projektowanie funkcji, aby być zgodnym z językiem visual powłoki i [wymagania craftsmanship](evaluation-tools-for-visual-studio.md).  
  
-   Użycie wspólnych poleceń i kontrolek, jeśli takie istnieją.  
  
-   Dowiedz się, w hierarchii programu Visual Studio i jak ustanawia kontekst i dyski interfejsu użytkownika.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Użyj środowiska czcionek i kolorów.  
  
-   Interfejs użytkownika należy przestrzegać bieżącego [czcionki środowiska](fonts-and-formatting-for-visual-studio.md) ustawienia, chyba że jest wystawiony dla dostosowania na stronie czcionek i kolorów w oknie dialogowym Opcje.  
  
-   Elementy interfejsu użytkownika należy użyć [usługi VSColor](colors-and-styling-for-visual-studio.md), przy użyciu udostępnionych tokeny środowiska lub tokeny właściwych dla funkcji.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Dostosowania wszystkich obrazów nowy styl VS.  
  
-   Postępuj zgodnie z zasady projektowania Visual Studio dla ikony, symbole i inne grafiki.  
  
-   Nie należy umieszczać tekst elementy graficzne.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Projekt z punktu widzenia skoncentrowane na użytkowniku.  
  
-   Utwórz przepływ zadań przed poszczególnych funkcji w nim.  
  
-   Należy zapoznać się z użytkownikami i upewnij wiedzy jawne w Twojej specyfikacji.  
  
-   Podczas przeglądania interfejsu użytkownika, należy ocenić pełnego środowiska pracy, jak również szczegóły.  
  
-   Projektowanie interfejsu użytkownika, dzięki czemu będzie funkcjonalności i atrakcyjne niezależnie od ustawień regionalnych i językowych.  
  
## <a name="screen-resolution"></a>Rozdzielczość ekranu  
  
### <a name="minimum-resolution"></a>Minimalna rozdzielczość  
 - Minimalna rozdzielczość dla programu Visual Studio Dev14 jest **1280 x 720**. Oznacza to, że jest *możliwe* używać programu Visual Studio rozdzielczością, chociaż może nie być optymalne użytkowników. Nie ma żadnej gwarancji, że wszystkie aspekty będzie można używać na niższy niż 1280 x 720 rozwiązania.  
  
 - Rozdzielczość docelowy dla programu Visual Studio jest **1366 x 768**. Jest to najniższej rozdzielczości, jaką Obiecujemy, że *dobrej* środowisko użytkownika.

 - Wysokość początkowego okna dialogowego powinna być **mniejsze niż 700 pikseli**, aby zmieścił się w minimalna rozdzielczość ramki IDE przy rozdzielczości 96 dpi.
  
### <a name="high-density-displays"></a>Wyświetla o wysokiej gęstości  
 Interfejs użytkownika w programie Visual Studio musi działają poprawnie w wszystkich DPI skalowanie czynników, które obsługuje system Windows bez: 150%, 200% i 250%.  
  
## <a name="anti-patterns"></a>Układ wzorce  
 Visual Studio zawiera wiele przykładów interfejsu użytkownika, które wykonaj nasze wskazówki i najlepsze rozwiązania. W ramach działań zmierzających do deweloperów przekazania często z podobnie jak co w przypadku tworzenia wzorce projektowe interfejsu użytkownika produktu. Chociaż jest to dobry podejście, że pomaga nam dysków spójności w interakcji z użytkownikiem i projektowania visual, czasem było funkcji więcej szczegółowych informacji, które nie spełniają nasze wskazówki ze względu na ograniczenia harmonogramu lub wady priorytetyzacji. W takich przypadkach nie chcemy zespoły skopiowanie jednego z tych "przed wzorców", ponieważ ich mnożyć się zły lub niespójny interfejsu użytkownika w środowisku Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Wymagane pola/ustawienia domyślnie wyświetlany stan błędu.  
  
#### <a name="feature-team-goals"></a>Funkcja cele zespołu  
  
-   Ostrzegaj użytkownicy dodali element, który musi być skonfigurowany.  
  
-   Należy zwrócić uwagę użytkownika obszarów, które wymagają danych wejściowych.  
  
#### <a name="anti-pattern-solution"></a>Rozwiązanie przed wzorca  
 Jak użytkownik zainicjował akcję, a przed ukończenia zadania, natychmiast umieścić ikony zatrzymanie krytyczne obszarów, które wymagają konfiguracji.  
  
#### <a name="example-manifest-designer-declarations"></a>Przykład: Deklaracje projektanta manifestu  
 Dodawanie deklaracji natychmiast do listy umieszcza je w stanie błędu, który jest zachowywana do czasu ustawiony przez użytkownika wymagane właściwości.  
  
 W takim przypadku jest dodatkowe problemu, ponieważ zawiera ikona alertu "&times;" ikony, dlatego ikonę Usuń wspólnej nie można użyć poza nim. W związku z tym interfejsu użytkownika używa przycisk Usuń, bardziej clunky formantu.  
  
 ![Wprowadzenie do interfejsu użytkownika w stanie błędu, domyślnie jest wzorzec oprogramowania Visual Studio. ] (../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti — wzorzec")<br />Wprowadzenie do interfejsu użytkownika w stanie błędu, domyślnie jest wzorzec oprogramowania Visual Studio.
  
#### <a name="alternatives"></a>Alternatywne  
 Dużo lepszym rozwiązaniem tego problemu może być:  
  
-   Zezwalaj użytkownikowi na dodawanie deklaracji bez ostrzeżenia, a następnie przenieść natychmiast, można ustawić właściwości w elemencie.  
  
-   Dodaj ikonę ostrzeżenia (gold trójkąt) po fokusu z elementu, takie jak dodanie innej deklaracji do listy lub próba zmiany karty w projektancie.  
  
-   Jeśli użytkownik próbuje zmienić karty przed ustawieniem właściwości na wszelkimi deklaracjami, okno dialogowe z informacjami o tym, że aplikacja nie zostanie utworzona pop (lub niezależnie od konsekwencje) do momentu rozwiązania ostrzeżeń. Jeśli użytkownik odrzuci okna dialogowego i zmienia karty mimo to następnie ikonę (krytyczna lub ostrzeżenie, odpowiednio) jest dodawane do zakładki deklaracje.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Wiele kliknięć, aby odrzucić interfejsu użytkownika  
  
#### <a name="feature-team-goals"></a>Funkcja cele zespołu  
 Nie Zezwalaj użytkownikowi na odrzucenie interfejs użytkownika bez zobaczenia pierwszy tekst objaśnienia.  
  
#### <a name="anti-pattern"></a>Układ wzorca  
 Zespół Wstawianie wideo łącza do różnych miejscach w Interfejsie użytkownika programu VS zdecydowała się na wspólnej strukturze "&times;" Zamknij przycisk i etykietek narzędzi wyjaśnienie określony przez UX i zamiast tego wykonuje listy rozwijanej, a łącze "Nie pokazuj ponownie".  

#### <a name="example-video-links-in-team-explorer"></a>Przykład: wideo łączy w programie Team Explorer
Wymuszanie użytkownikowi odczytywanie tekst objaśnienia przed odrzuceniu interfejsu użytkownika jest uruchomiony wzorca w programie Visual Studio. Łącza poprawnie zaprojektowane, wideo należy wyświetlić etykietkę zawierającą dodatkowe informacje na aktywowanie i klikając pozycję "&times;" należy odrzucić komunikat bez konieczności dalszej interakcji.


 ![Wyjaśniające tekst anty &#45; wzorzec & 45; niepoprawna](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Wzorzec nieprawidłowe łącze wideo
  
#### <a name="result"></a>Wynik  
 Zamiast przycisku Zamknij proste (jednego kliknięcia) użytkownik będzie zmuszony po prostu zignoruj interfejsu użytkownika w każdym miejscu, które są wyświetlane linki wideo przy użyciu dwóch kliknięć.  
  
#### <a name="alternatives"></a>Alternatywne  
 Poprawny projekt w takiej sytuacji może być zgodne ze wzorcem wspólnej programu Internet Explorer, pakietu Office i programu Visual Studio: przy aktywowaniu, użytkownik może wyświetlić opis etykietki narzędzia i jedno kliknięcie powoduje ukrycie interfejsu użytkownika.  
  
 ![Wyjaśniające tekst anty &#45; wzorzec & 45; poprawne](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Popraw wzorzec Explanatorytextanti")<br />Wzorzec prawidłowe łącze wideo
  
### <a name="using-command-bars-for-settings"></a>Za pomocą pasków poleceń ustawień  
 **Rysunek A** reprezentuje ten układ wzorzec: umieszczanie ustawienie poniżej przycisku polecenia, który dotyczy nie tylko polecenia. W tym szkicu istnieją polecenia oprócz Rozpocznij debugowanie — widok w przeglądarce, uruchom bez debugowania i Step Into, takich jak — która szanuje wybrane ustawienie.  

  ![Rysunek A: pasek przed wzorzec poleceń](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "FigureA-Commandbaranti — wzorzec")<br />Rysunek A: wzorzec Układ paska polecenia
  
 Nieco lepsza, ale nadal niepożądanych, jest umieszczenie ustawienia tego typu w paskach narzędzi, jak pokazano w **B rysunek**. Podczas podziału przycisków zająć mniej miejsca i dlatego poprawy na listach rozwijanych, obu projektów w dalszym ciągu używają paska narzędzi do promowania coś, które nie są naprawdę polecenia.  
 
 ![Rysunek B: lepiej, ale nadal wzorzec Układ paska poleceń](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "FigureB-Commandbaranti — wzorzec")<br />Rysunek B: lepsze, ale nadal wzorzec Układ paska poleceń
 
  W ujęciu poprawne pokazano **C rysunek**, ustawienie jest związany z serii poleceń. Nie ma ustawienia globalne ustawiany a firma Microsoft jest po prostu przełączanie między cztery poleceń. Jest to tylko sytuacji, w którym są dozwolone polecenia na pasku narzędzi. 

 ![Rysunek C: Popraw Użyj wzorca pasek poleceń Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "FigureC-Commandbaranti — wzorzec")<br />Rysunek C: poprawne Użyj wzorca pasek poleceń Visual Studio
   
### <a name="control-anti-patterns"></a>Wzorce układ formantu  
 Niektóre przed wzorce są po prostu niepoprawne użycie lub prezentacja kontroli lub grupy formantów.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podkreślenie używana jako etykieta grupy, nie hiperłącza  
 Tekst podkreślenia należy używać tylko w przypadku hiperłącza.  
  
 **Zły:**    
 ![Podkreślony tekst, który nie jest hiperłącze to wzorzec oprogramowania Visual Studio. ] (../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />Podkreślony tekst, który nie jest hiperłącze to wzorzec oprogramowania Visual Studio.
  
 **Dobrym:**   
 ![Styl poprawnie, z systemem innym niż hyperlink tekst jest wyświetlany unadorned czcionką środowiska. ] (../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />Styl poprawnie, z systemem innym niż hyperlink tekst jest wyświetlany unadorned czcionką środowiska.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Klikając pole skutkuje podręczne okno dialogowe  
 Kliknij pole wyboru "Włącz pulpit zdalny dla wszystkich ról" w kreatorze "Publikuj systemu Windows Azure aplikacji" natychmiast wyświetla okno dialogowe wyskakujących, wzorca oprogramowania Visual Studio. Ponadto, pole wyboru nie wypełniać pola wyboru po wybraniu, inny wzorzec przed interakcji.  
  
 ![Po kliknięciu pola wyboru wzorca oprogramowania Visual Studio wyświetlania okna dialogowego. ] (../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Po kliknięciu pola wyboru wzorca oprogramowania Visual Studio wyświetlania okna dialogowego.
  
### <a name="hyperlink-anti-patterns"></a>Wzorce przed hiperłącza  
 Poniższy przykład zawiera dwa wzorce układ.  
  
1.  Pierwszego planu, red włączenie hover oznacza, że nie jest używany prawidłowy kolor udostępniony przez usługę czcionki.  
  
2.  "Dowiedz się więcej" nie jest odpowiedni tekst łącza do bieżącego tematu. Celem użytkownika jest nie, aby dowiedzieć się więcej, aby zrozumieć zagadnienia siebie.  
  
 ![Ignorowanie usługi kolorów i za pomocą "Dowiedz się więcej" hiperłączy są wzorce oprogramowania Visual Studio. ] (../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />Ignorowanie usługi kolorów i za pomocą "Dowiedz się więcej" hiperłączy są wzorce oprogramowania Visual Studio.  
  
 **Lepsze rozwiązania:** pytanie, użytkownik będzie pytaniem, klikając link.  
  
-   Jak działają usługi Windows Azure  
  
-   Jeśli potrzebujesz projekt usług mobilnych Microsoft Azure?  
  
#### <a name="using-click-here-for-links"></a>Za pomocą "Kliknij tutaj" dla łączy  
 Powinien być self-descriptive hiperłącza. Jest to przed składnię "Kliknij tutaj" ani wszelkie zmiany podobne.  
  
 **Zły:** "Kliknij tutaj, aby uzyskać instrukcje dotyczące sposobu tworzenia nowego projektu."
  
 **Dobra:** "Jak utworzyć nowy projekt?"