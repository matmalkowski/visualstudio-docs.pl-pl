---
title: Projektant przepływu pracy — skróty klawiaturowe w Projektancie przepływów pracy
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83664d6402c23da89adf332bc9cd34eac89384bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Skróty klawiaturowe w Projektancie przepływów pracy

Wszystkie podstawowe funkcje projektanta przepływów pracy systemu Windows mogą uzyskiwać klawiatury.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Nawigowanie po projektanta przepływów pracy za pomocą klawiatury

Visual Studio 2010 skróty globalne i debugowania skróty dotyczą projektanta przepływów pracy. Ponadto liczba projektanta przepływów pracy określonych skróty klawiaturowe zostały utworzone. W programie Visual Studio 2010 wszystkie skróty klawiaturowe mogą być mapowane ponownie. Jednak w aplikacji rehosted te skróty klawiaturowe są zapisane na stałe.

### <a name="workflow-designer-keyboard-shortcuts"></a>Skróty klawiaturowe projektanta przepływów pracy

W poniższej tabeli przedstawiono domyślne skróty klawiaturowe przypisane do poleceń projektanta przepływów pracy.

|Skrót|Cel|
|--------------|-------------|
|CTRL+E, A|Pokazuje lub ukrywa projektanta argumentów.|
|CTRL+E, C|Zwija wybrane działanie w miejscu.|
|CTRL+E, E|Rozwija wybrane działanie w miejscu.|
|CTRL+E, F|Łączy wybrane działania w elemencie Schemat blokowy.|
|CTRL+E, I|Pokazuje lub ukrywa projektanta importów.|
|CTRL+E, M|Przenosi fokus klawiatury do następnego elementu w kolejności tabulacji.|
|CTRL+E, N|Tworzy nową zmienną zakresu wybranego działania (lub najbardziej).|
|CTRL+E, O|Pokazuje lub ukrywa mapowanie przeglądów.|
|CTRL+E, P|Przechodzi do nadrzędnej wybranego działania. Przechodzi na wyższy poziom w nadrzędnych, a zmiany działania głównego na powierzchnię projektanta.|
|CTRL+E, S|Dodaje element z fokusem klawiatury do bieżącego zaznaczenia.|
|CTRL+E, V|Pokazuje lub ukrywa projektanta zmiennych.|
|CTRL+E, X|Rozwija wszystkie działania w przepływie pracy.|
|CTRL+ALT+F6|Przenosi fokus klawiatury z bieżącego obszaru interfejsu użytkownika do obszaru dalej w sekwencji. Kolejność jest następująca:<br /><br /> 1.  Pasek nawigacyjny stron nadrzędnych.<br />2.  Powierzchnię projektanta<br />3.  Projektanta argumentów/zmienne/importów, jeśli otwarte<br />4.  Powłoka|

### <a name="flowchart"></a>Schemat blokowy

Na poniższej liście przedstawiono gestów użyty do utworzenia schematu blokowego przez klawiatury. Tak jak pozostałe projektanta przepływów pracy działania są dodawane do powierzchni projektanta przy użyciu skrótów globalne przybornika wyposażone w Visual Studio 2010.

- Aby przenieść działanie, wybierz działanie, a następnie użyj klawiszy strzałek, aby zmienić jego położenie.

- Aby zmienić rozmiar schematu blokowego, Przenieś działanie poza granicą bieżącego schematu blokowego za pomocą klawiszy strzałek. Schemat blokowy zmieniany jest automatycznie.

- Aby ustawić działanie jako węzeł początkowy, użyj **ustawić jako parametr StartNode** polecenia w menu kontekstowym.

- Aby połączyć działania:

    1.  Wybierz działania źródłowego za pomocą klawisza TAB do działania.

    2.  Naciśnij klawisze CTRL + E, M wiele razy, aby przenieść fokus klawiatury do działania docelowego.

    3.  Naciśnij klawisze CTRL + E, S, aby dodać działanie docelowe do zaznaczenia.

    4.  Naciśnij klawisze CTRL + E, F, aby dodać łącznika ze źródła do miejsca docelowego.

Uwagi dotyczące łączenia działań przez klawiatury:

- Możesz wprowadzić wiele połączeń w tym samym czasie, dodając więcej działań do zaznaczenia przed kliknięciem przycisku CTRL + E, F. Połączenia są nawiązywane w kolejności, że działania nie zostały dodane do zaznaczenia.

- Jeśli dwa działania nie można połączyć, na przykład jeśli działania źródłowego ma już połączenia wychodzącego innych połączeń między działaniami w zaznaczeniu nadal zostały wprowadzone, jeśli to możliwe.

- Gdy **elementu FlowDecision** jest dołączony do zaznaczenia i **elementu FlowDecision** ma nie łączniki wychodzących, łącznik jest umieszczona na **True** gałęzi.

### <a name="expression-editing"></a>Edytowanie wyrażeń

Domyślnie domyślne skróty klawiaturowe do edycji tekstu w języku Visual Basic stosowane w edytorze wyrażenie w Projektancie przepływów pracy, z następującymi ograniczeniami:

- Ponowne mapowanie skróty klawiaturowe dla poniższych poleceń nie ma znaczenia. Domyślne skróty klawiaturowe można używać tylko dostępu do tych poleceń podczas edycji wyrażenia.

   - Wytnij
   - Kopiuj
   - Wklej
   - Zaznacz wszystko
   - Cofnij
   - Wykonaj ponownie

- Aby ponownie zamapować skróty klawiaturowe dla wyrażenia poleceń edycji w Projektancie przepływów pracy w Visual Studio 2010, należy edytować skróty w zakresie projektanta przepływów pracy. Zmiany wprowadzone w zakresie edytora tekstów nie automatycznie dotyczą projektanta przepływów pracy. Jeśli chcesz ponownie zamapować skróty w obu miejscach, należy zastosować zmiany dwukrotnie (raz dla każdego zakresu).