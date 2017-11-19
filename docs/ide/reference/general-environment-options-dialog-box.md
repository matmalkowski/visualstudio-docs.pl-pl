---
title: "Ogólne, środowisko, opcje ― Okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72122fdd8f9b78429b90cacd093908e8fccb714d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="general-environment-options-dialog-box"></a>Ogólne, środowisko, opcje — Okno dialogowe
Ta strona służy do zmiany motywy kolorów, ustawienia paska stanu i skojarzenia rozszerzeń plików, wśród innych opcji, zintegrowane środowisko programistyczne (IDE). Można uzyskać dostępu do **opcje** okno dialogowe, otwierając **narzędzia** menu, wybierając **opcje**, otwierając **środowiska** folder, a następnie Wybieranie **ogólne** strony. Jeśli ta strona nie ma na liście, wybierz **Pokaż wszystkie ustawienia** pole wyboru w **opcje** okno dialogowe.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, otwórz **narzędzia** menu, a następnie wybierz pozycję **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="visual-experience"></a>Środowisko Visual  
 **Kolor motywu**  
 Wybierz **Blue**, **światła** lub **ciemny** motywu kolorów dla IDE.  
  
 Można zainstalować dodatkowe wstępnie zdefiniowanych motywów i tworzenie niestandardowych kompozycji przez pobranie i zainstalowanie **programu Visual Studio 2015 kolor motywu edytora** z [galerii programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=RootCategory&f%5B0%5D.Value=tools). Po zainstalowaniu tego narzędzia motywy kolorów dodatkowe są wyświetlane w polu listy Kolor motywu.  
  
 Zastosuj wielkość liter tytułu paska menu  
 Menu znajdują się w **wielkość liter w tytule** domyślnie w programie Visual Studio 2015. Usuń zaznaczenie tej opcji, aby ustawić je **wersaliki**.  
  
 **Automatycznie Dostosuj wyglądu na podstawie wydajności klienta**  
 Określa, czy program Visual Studio dostosowanie środowiska visual automatycznie ustawia lub jawnie ustaw dostosowania. To dopasowanie może zmienić wyświetlanie kolorów z gradienty kolorów ani może ograniczyć stosowanie animacji w menu lub okna podręcznego.  
  
 **Włączanie obsługi wzbogaconego klienta**  
 Włącza pełne visual środowiska Visual Studio, w tym gradienty i animacji. Usuń zaznaczenie tej opcji, gdy za pomocą połączenia pulpitu zdalnego lub starszych kart graficznych, ponieważ te funkcje może mieć pogorszenie wydajności w takich przypadkach. Ta opcja jest dostępna tylko wtedy, gdy zostanie ono wyczyszczone **automatycznie Dostosuj interfejs do klienta możliwości** opcji.  
  
 **Użyj sprzętowego przyspieszania grafiki, jeśli jest dostępne**  
 Używa sprzętowego przyspieszania grafiki, jeśli jest dostępna, a nie przyspieszenie oprogramowania.  
  
## <a name="other"></a>Inne  
 **Elementy(ów) w menu okna**  
 Dostosowuje liczbę systemu windows, które pojawiają się na liście Windows **okna** menu. Wpisz liczbę z zakresu od 1 do 24. Domyślnie liczba wynosi 10.  
  
 **Elementy(ów) na listach ostatnio używanych**  
 Dostosowuje liczbę ostatnio używanych projektów i pliki, które znajdują się w **pliku** menu. Wpisz liczbę z zakresu od 1 do 24. Domyślnie liczba wynosi 10. Jest to prosty sposób na pobranie ostatnio używanych projektów i pliki.  
  
 **Pokaż pasek stanu**  
 Wyświetla pasek stanu. Pasek stanu znajduje się w dolnej części okna IDE i wyświetla informacje o postępie trwających operacji.  
  
 **Przycisk Zamknij dotyczy tylko aktywnego okna narzędzi**  
 Określa, że w przypadku **Zamknij** przycisk zostanie kliknięty tylko aktywnego okna narzędzia został zamknięty i nie wszystkie z okna narzędzi w zestawie dokowanych. Domyślnie ta opcja jest zaznaczona.  
  
 **Przycisk Ukryj automatycznie dotyczy tylko aktywnego okna narzędzi**  
 Określa, że w przypadku **automatyczne ukrywanie** przycisku, okna narzędzia, który ma fokus jest ukrywane automatycznie i nie wszystkie okna narzędzi w zestawie dokowanych. Domyślnie ta opcja nie wybrano żadnych działań.  
  
 **Zarządzanie skojarzenia plików**  
 Wyświetla **ustawiania skojarzeń programu dla systemu Windows** okno dialogowe, w którym można wyświetlać rozszerzeniom plików dla elementów, które są zwykle skojarzone z programem Visual Studio i bieżącego domyślnego programu do otwierania każdego typu pliku. Aby wprowadzić domyślną aplikację dla typów plików, które nie są już skojarzone z nim programu Visual Studio, wybierz rozszerzenie pliku, a następnie wybierz **zapisać**.  
  
 Ta opcja może być przydatna, jeśli dwie wersje programu Visual Studio zainstalowany na tym samym komputerze, a jedna z wersji późniejszej dezinstalacji. Po odinstalowaniu, ikony dla plików programu Visual Studio nie są widoczne w Eksploratorze plików. Ponadto system Windows nie rozpoznaje już Visual Studio jako domyślnej aplikacji do edycji tych plików. Ta opcja przywraca tych skojarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno dialogowe opcji środowiska](../../ide/reference/environment-options-dialog-box.md)   
 [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)