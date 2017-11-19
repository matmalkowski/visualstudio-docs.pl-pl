---
title: "Skróty klawiaturowe i myszy w oknie Diagram klas i okno Szczegóły klasy (Projektant klas) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c5db2487d9cabbcb440fce00f6cce82310aba5e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer"></a>Skróty przy użyciu klawiatury i myszy w oknie Diagram klas i Szczegóły klasy (Projektant klas)
Klawiatury oprócz myszy można użyć do wykonania akcji nawigacji w Projektancie klas i w **szczegółów klasy** okna.  
  
 **W tym temacie**  
  
-   [Za pomocą myszy w Projektancie klas](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDesigner)  
  
-   [Za pomocą myszy w oknie Szczegóły klasy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#MouseClassDetails)  
  
-   [Korzystanie z klawiatury w Projektancie klas](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDesigner)  
  
-   [Korzystanie z klawiatury w okno Szczegóły klasy](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md#KeyboardClassDetails)  
  
##  <a name="MouseClassDesigner"></a>Za pomocą myszy w Projektancie klas  
 Obsługiwane są następujące akcje myszy w diagramach klas:  
  
|Kombinacja myszy|Kontekst|Opis|  
|-----------------------|-------------|-----------------|  
|Kliknij dwukrotnie|elementy kształtu|Otwiera edytora kodu.|  
||Interfejs typu lizak łącznika|Interfejs typu lizak Rozwiń/Zwiń.|  
||Interfejs typu lizak łącznika etykiety|Wywołuje **Pokaż interfejs** polecenia.|  
|Kółka myszy|Diagram klas|Przewiń w pionie.|  
|SHIFT + kółka myszy|Diagram klas|Przewijane w poziomie.|  
|CTRL + kółka myszy|Diagram klas|Powiększenia.|  
|CTRL + Shift + kliknięcie|Diagram klas|Powiększenia.|  
  
##  <a name="MouseClassDetails"></a>Za pomocą myszy w oknie Szczegóły klasy  
 Za pomocą myszy, można zmienić wygląd okno Szczegóły klasy i danych, które są wyświetlane, w następujący sposób:  
  
-   Kliknij dowolną komórkę można edytować pozwala edytować zawartość tej komórki. Zmiany są odzwierciedlane we wszystkich miejscach, że dane są przechowywane lub wyświetlane, w tym w oknie właściwości i w kodzie źródłowym.  
  
-   Kliknij dowolną komórkę wiersza powoduje, że okno właściwości, aby wyświetlić właściwości dla elementu reprezentowanego przez ten wiersz.  
  
-   Aby zmienić szerokość kolumny, przeciągnij granicę po prawej stronie nagłówka kolumny jest szerokości, który ma.  
  
-   Można rozwinąć lub zwinąć przedziału lub właściwość węzłów klikając symbole Strzałka w lewo wiersza.  
  
-   Okno Szczegóły klasy oferuje kilka przycisków przy tworzeniu nowych elementów członkowskich w bieżącej klasie oraz przechodzenia między przedziałów członków w siatce okno Szczegóły klasy. Aby uzyskać więcej informacji zobacz przyciski okno Szczegóły klasy.  
  
##  <a name="KeyboardClassDesigner"></a>Korzystanie z klawiatury w Projektancie klas  
 Obsługiwane są następujące akcje klawiatury w diagramach klas:  
  
|Key|Kontekst|Opis|  
|---------|-------------|-----------------|  
|Klawisze strzałek|Kształty typów wewnątrz|Style drzewa nawigacji na zawartość kształtu (otaczania kształt jest obsługiwane). Lewy i prawy klucze Rozwiń/Zwiń bieżący element Jeśli rozwijania i przejdź do elementu nadrzędnego Jeśli nie (zobacz nawigacji w widoku drzewa szczegółowe zachowania).|  
||Kształty najwyższego poziomu|Przenoszenie kształtów na diagramie.|  
|SHIFT + Strzałka w klawisze|Kształty typów wewnątrz|Kompilowanie składające się z elementów kształtu, takich jak elementy członkowskie, typy zagnieżdżone lub przedziałów ciągłego zaznaczenia. Te skróty nie obsługują otaczania.|  
|STRONA GŁÓWNA|Kształty typów wewnątrz|Przejdź do tytułu kształtu najwyższego poziomu.|  
||Kształty najwyższego poziomu|Przejdź do pierwszego kształtu na diagramie.|  
|END|Kształty typów wewnątrz|Przejdź do ostatniego elementu widoczne wewnątrz kształtu.|  
||Kształty najwyższego poziomu|Przejdź do ostatniego kształt na diagramie.|  
|SHIFT + HOME|Typ wewnątrz kształtu|Wybiera elementów wewnątrz kształtu, począwszy od bieżącego elementu, a kończąc kształtu tego samego elementu najwyższy.|  
|SHIFT + END|Typ wewnątrz kształtu|Taka sama jak SHIFT + HOME, ale w kierunku do góry do dołu.|  
|ENTER|Wszystkie konteksty|Wywołuje domyślną akcję kształtu, który jest również dostępny za pośrednictwem kliknij dwukrotnie. W większości przypadków jest to widok Kod, ale niektóre elementy definiować go inaczej (lizaki, nagłówki przedziału, etykiet interfejsów typu lizak).|  
|+/-|Wszystkie konteksty|W przypadku rozwijania elementem mającym aktualnie fokus, te klucze Rozwiń/Zwiń element.|  
|>|Wszystkie konteksty|W przypadku elementów z elementami podrzędnymi rozszerza elementu, gdy jest zwinięty i przechodzi do pierwszego elementu podrzędnego.|  
|<|Wszystkie konteksty|Przechodzi do elementu nadrzędnego.|  
|ALT + SHIFT + L|Wewnątrz kształty typów + kształtów typu.|Przechodzi do interfejs typu lizak aktualnie wybranego kształtu, jeśli jest obecny.|  
|ALT + SHIFT + B|Wewnątrz kształty typów + kształtów typu.|Jeśli listę typów podstawowych jest wyświetlany dla kształtu typu i ma więcej niż jeden element, to Przełącza stan rozszerzenia listy (Zwiń/Rozwiń).|  
|DELETE|Typ i komentarza kształtów|Wywołuje **usunąć z diagramu** polecenia.|  
||Na wszystkich innych urządzeń.|Wywołuje **usunąć z kodu** polecenia (elementy członkowskie, parametry, skojarzenia, dziedziczenia, etykiet interfejsów typu lizak).|  
|CTRL + DELETE|Wszystkie konteksty|Wywołuje **usunąć z kodu** polecenia wyboru.|  
|TAB|Wszystkie konteksty|Przechodzi do następnego podrzędnych w tym samym elemencie nadrzędnym (obsługuje zawijania).|  
|SHIFT+TAB|Wszystkie konteksty|Powoduje przejście do poprzedniego podrzędnych w tym samym elemencie nadrzędnym (obsługuje zawijania).|  
|MIEJSCA|Wszystkie konteksty|Włącza/wyłącza wybór dla bieżącego elementu.|  
  
##  <a name="KeyboardClassDetails"></a>Korzystanie z klawiatury w okno Szczegóły klasy  
  
> [!NOTE]
>  Następujące powiązań klucza zostały wybrane do specjalnie, aby używane środowisko przypominało środowisko wpisywanie kodu.  
  
 Za pomocą następujących klawiszy Przejdź okno Szczegóły klasy:  
  
|||  
|-|-|  
|Key|Wynik|  
|, (przecinek)|Jeśli kursor znajduje się w wierszu parametru, wpisz przecinek przenosi kursor do pola nazwy parametru dalej. Jeśli kursor znajduje się w ostatnim wierszu parametru metody, powoduje przeniesienie kursora prowadzącego do \<Dodaj parametr > pola, które umożliwia utworzenie nowego parametru.<br /><br /> Jeśli kursor znajduje się w innym miejscu w okno Szczegóły klasy, wpisz przecinek dodaje przecinek dosłownie tego pola.|  
|; (średnikami)<br /><br /> lub<br /><br /> ) (nawiasu zamykającego)|Przesuń kursor do następnego wiersza elementu członkowskiego w siatce okno Szczegóły klasy pole Nazwa.|  
|Tab|Przesuwa kursor do następnego pola, najpierw przenoszenie od lewej do prawej, a następnie góry do dołu. Jeśli kursor jest przenoszona z pola, w którym został wpisany tekst, okno Szczegóły klasy przetwarza tekst i zapisuje go, jeśli nie generuje błędu.<br /><br /> Czy kursor znajduje się na puste pole takich jak \<Dodaj parametr >, Tab przenosi je do pierwszego pola następnego wiersza.|  
|\<miejsce >|Przesuwa kursor do następnego pola, najpierw przenoszenie od lewej do prawej, a następnie góry do dołu. Czy kursor znajduje się na puste pole takich jak \<Dodaj parametr >, powoduje przeniesienie do pierwszego pola następnego wiersza. Należy pamiętać, że \<miejsca > wpisane natychmiast po przecinek jest ignorowana.<br /><br /> Jeśli kursor znajduje się w polu podsumowania Summary, miejsce na wpisanie dodaje znak odstępu.<br /><br /> Jeśli kursor znajduje się w kolumnie Ukryj danego wiersza, miejsce na wpisanie przełącza wartość wyboru Ukryj.|  
|CTRL + Tab|Przełącz na inne okno dokumentu. Na przykład przełącznika okno Szczegóły klasy można otworzyć pliku kodu.|  
|ESC (ucieczki)|Jeśli rozpoczęto wpisać tekst w polu, naciskając klawisz ESC działa jako klucz cofania, przywrócenie zawartość pola jego poprzednią wartość. Jeśli okno Szczegóły klasy ogólne fokus, ale nie określonej komórki ma fokus, naciskając klawisz ESC przenosi fokus poza okno Szczegóły klasy.|  
|Strzałka w górę i Strzałka w dół|Te klucze kursor jest wiersz po wierszu w pionie w siatce okno Szczegóły klasy.|  
|Strzałka w lewo|Jeśli kursor znajduje się w kolumnie Nazwa, naciskając klawisz strzałki w lewo Zwija bieżący węzeł w hierarchii (jeśli jest on otwarty).|  
|Strzałka w prawo|Jeśli kursor znajduje się w kolumnie Nazwa, naciskając klawisz strzałki w prawo rozwija bieżący węzeł w hierarchii (jeśli jest zwinięte).|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i konfigurowanie typów członków (Projektant klas)](../ide/creating-and-configuring-type-members-class-designer.md)