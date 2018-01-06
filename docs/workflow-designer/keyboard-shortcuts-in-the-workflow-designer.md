---
title: "Skróty klawiaturowe w Projektancie przepływów pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 5fe712caf9e76905dee8307998ea0854a469a71d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Skróty klawiaturowe w Projektancie przepływów pracy
Wszystkie podstawowe funkcje [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] można uzyskać, sprawdzając klawiatury.  
  
## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Nawigowanie po projektanta przepływów pracy za pomocą klawiatury  
 Wewnątrz [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], skróty globalne i debugowania skróty dotyczą [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Ponadto szereg [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] określonych skróty klawiaturowe zostały utworzone. W [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], wszystkie skróty klawiaturowe można ponownie zamapować. Jednak w aplikacji rehosted te skróty klawiaturowe są zapisane na stałe.  
  
### <a name="workflow-designer-keyboard-shortcuts"></a>Skróty klawiaturowe projektanta przepływów pracy  
 W poniższej tabeli przedstawiono domyślne skróty klawiaturowe przypisane do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] poleceń.  
  
|Skrót|Cel|  
|--------------|-------------|  
|CTRL + E, A|Pokazuje lub ukrywa projektanta argumentów.|  
|CTRL + E, C|Zwija wybrane działanie w miejscu.|  
|CTRL + E, E|Rozwija wybrane działanie w miejscu.|  
|CTRL + E, F|Łączy wybrane działania w elemencie Schemat blokowy.|  
|CTRL + E, I|Pokazuje lub ukrywa projektanta importów.|  
|CTRL + E, M|Przenosi fokus klawiatury do następnego elementu w kolejności tabulacji.|  
|CTRL + E,|Tworzy nową zmienną zakresu wybranego działania (lub najbardziej).|  
|CTRL + E, O|Pokazuje lub ukrywa mapowanie przeglądów.|  
|CTRL + E, P|Przechodzi do nadrzędnej wybranego działania. Przechodzi na wyższy poziom w nadrzędnych, a zmiany działania głównego na powierzchnię projektanta.|  
|CTRL + E, S|Dodaje element z fokusem klawiatury do bieżącego zaznaczenia.|  
|CTRL + E, V|Pokazuje lub ukrywa projektanta zmiennych.|  
|CTRL + E, X|Rozwija wszystkie działania w przepływie pracy.|  
|CTRL + ALT + F6|Przenosi fokus klawiatury z bieżącego obszaru interfejsu użytkownika do obszaru dalej w sekwencji. Kolejność jest następująca:<br /><br /> 1.  Pasek nawigacyjny stron nadrzędnych.<br />2.  Powierzchnię projektanta<br />3.  Projektanta argumentów/zmienne/importów, jeśli otwarte<br />4.  Powłoka|  
  
### <a name="flowchart"></a>Schemat blokowy  
 Na poniższej liście przedstawiono gestów użyty do utworzenia schematu blokowego przez klawiatury. W pozostałej części [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], działania są dodawane do powierzchni projektanta przy użyciu skrótów globalne przybornika wyposażone w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
-   Aby przenieść działanie, wybierz działanie, a następnie użyj klawiszy strzałek, aby zmienić jego położenie.  
  
-   Aby zmienić rozmiar schematu blokowego, Przenieś działanie poza granicą bieżącego schematu blokowego za pomocą klawiszy strzałek. Schemat blokowy zmieniany jest automatycznie.  
  
-   Aby ustawić działanie jako węzeł początkowy, użyj **ustawić jako parametr StartNode** polecenia w menu kontekstowym.  
  
-   Aby połączyć działania:  
  
    1.  Wybierz działania źródłowego za pomocą klawisza TAB do działania.  
  
    2.  Naciśnij klawisze CTRL + E, M wiele razy, aby przenieść fokus klawiatury do działania docelowego.  
  
    3.  Naciśnij klawisze CTRL + E, S, aby dodać działanie docelowe do zaznaczenia.  
  
    4.  Naciśnij klawisze CTRL + E, F, aby dodać łącznika ze źródła do miejsca docelowego.  
  
 Uwagi dotyczące łączenia działań przez klawiatury:  
  
-   Możesz wprowadzić wiele połączeń w tym samym czasie, dodając więcej działań do zaznaczenia przed kliknięciem przycisku CTRL + E, F. Połączenia są nawiązywane w kolejności, że działania nie zostały dodane do zaznaczenia.  
  
-   Jeśli dwa działania nie można połączyć, na przykład jeśli działania źródłowego ma już połączenia wychodzącego innych połączeń między działaniami w zaznaczeniu nadal zostały wprowadzone, jeśli to możliwe.  
  
-   Gdy **elementu FlowDecision** jest dołączony do zaznaczenia i **elementu FlowDecision** ma nie łączniki wychodzących, łącznik jest umieszczona na **True** gałęzi.  
  
### <a name="expression-editing"></a>Edytowanie wyrażeń  
 Domyślnie domyślne skróty klawiaturowe dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zastosować edycji tekstu w edytorze wyrażenie w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], zastosowanie mają poniższe ograniczenia:  
  
-   Ponowne mapowanie skróty klawiaturowe dla poniższych poleceń nie ma znaczenia. Domyślne skróty klawiaturowe można używać tylko dostępu do tych poleceń podczas edycji wyrażenia.  
  
    1.  Wytnij  
  
    2.  Kopiuj  
  
    3.  Wklej  
  
    4.  Zaznacz wszystko  
  
    5.  Cofnij  
  
    6.  Wykonaj ponownie  
  
-   Aby ponownie zamapować skróty klawiaturowe dla polecenia wewnątrz edycji wyrażenia [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], Edytuj skróty w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] zakresu. Zmiany wprowadzone w zakresie edytora tekstów nie automatycznie dotyczą [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Jeśli chcesz ponownie zamapować skróty w obu miejscach, należy zastosować zmiany dwukrotnie (raz dla każdego zakresu).