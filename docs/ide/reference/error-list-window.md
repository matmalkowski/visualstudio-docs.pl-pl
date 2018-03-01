---
title: "Okno listy błędów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 227c23714231c87ba2ecac5fa7f50a632a73b123
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-list-window"></a>Okno listy błędów
> [!NOTE]
>  Lista błędów wyświetla informacje o komunikat o błędzie. Możesz skopiować numeru błędu lub błąd tekst w oknie danych wyjściowych. Aby wyświetlić okno danych wyjściowych, naciśnij kombinację klawiszy Ctrl + Alt + O. Zobacz [okna wyjściowego](../../ide/reference/output-window.md).  
  
 Można programować aplikacje szybsze przy użyciu **listy błędów** okna. Na przykład można wykonywać następujące zadania:  
  
-   Wyświetl błędy, ostrzeżenia i komunikaty, utworzonej podczas pisania kodu.  
  
-   Znajdź błędy składniowe zauważyć przez funkcję IntelliSense.  
  
-   Znajdź błędy wdrożenia, niektórych analizy statycznej błędów i błędów wykrytych podczas stosowania zasad dla szablonu.  
  
-   Kliknij dwukrotnie wpis komunikat błędu można otworzyć pliku, gdzie występuje problem i przejść do lokalizacji błędu.  
  
-   Filtrowanie zapisy, które są wyświetlane, a które kolumny informacji są wyświetlane dla każdego wpisu.  
  
-   Wyszukiwania konkretnych terminów i zawęzić zakres wyszukiwania tylko dla bieżącego projektu lub dokumentu.  
  
Aby wyświetlić **listy błędów**, kliknij przycisk **widoku / List błąd**, lub **CTRL +\\+ E**.  
  
Możesz wybrać **błędy**, **ostrzeżenia**, i **wiadomości** kart, aby wyświetlić różne poziomy informacji.  
  
Aby posortować listę, kliknij nagłówek dowolnej kolumny. Aby ponownie posortować wg dodatkową kolumnę, naciśnij i przytrzymaj klawisz SHIFT i kliknij inny nagłówek kolumny. Aby zaznaczyć kolumny, które są wyświetlane i które są ukryte, wybierz **Pokaż kolumny** z menu skrótów. Aby zmienić kolejność wyświetlania kolumn, przeciągnij nagłówek dowolnej kolumny w lewo lub w prawo.  
  
> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych tutaj, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, kliknij przycisk **narzędzi / Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="error-list-filters"></a>Filtr listy błędów  
 Istnieją dwa typy filtru w dwóch polach listy rozwijanej, jeden po prawej stronie paska narzędzi i jeden do lewego paska narzędzi. Lista rozwijana po lewej stronie paska narzędzi określa zestaw plików kodu do użycia (**całego rozwiązania**, **otwarte dokumenty**, **bieżącego projektu**,  **Bieżący dokument**).  
  
 Można ograniczyć zakres wyszukiwania do analizowania i korzystania z grup błędów. Na przykład można skoncentrować się na podstawowych błędów, które uniemożliwiają Kompilowanie projektu. Opcje zakresu obejmują:  
  
1.  **Otwieranie dokumentów**: Pokaż błędy, ostrzeżenia i komunikaty dla otwartych dokumentów.  
  
2.  **Bieżący projekt**: Pokaż błędy, ostrzeżenia i komunikaty z projektu aktualnie wybrany dokument w **edytor** lub wybranego projektu w **Eksploratora rozwiązań**.  
  
    > [!NOTE]
    >  Filtrowane listy błędy, ostrzeżenia i komunikaty ulegnie zmianie, jeśli projekt obecnie wybrany dokument jest inny niż projekt wybrany w **Eksploratora rozwiązań**.  
  
3.  **Bieżący dokument**: Pokaż błędy, ostrzeżenia i komunikaty, w obecnie wybranym dokumencie w **edytor** lub **Eksploratora rozwiązań**.  
  
Jeśli filtr jest obecnie stosowane do wyników wyszukiwania, nazwę filtru pojawia się w **listy błędów** paska tytułu. **Błędy**, **ostrzeżenia**, i **wiadomości** przycisków, a następnie wyświetla liczbę filtrowane elementy wyświetlane wraz z całkowitą liczbę elementów; na przykład Pokaż przyciski x, y błędów. Jeśli żaden filtr nie zostanie zastosowana, pasek tytułu mówi tylko "Lista błędów".  
  
Lista po prawej stronie paska narzędzi Określa, czy mają być pokazywane błędy kompilacji (błędy wynikające z operacji kompilacji) lub z IntelliSense (błędy wykryte przed uruchomieniem kompilacji) lub obie.  
  
## <a name="search"></a>Wyszukaj  
 Użyj **listy błędów wyszukiwania** pole tekstowe po prawej stronie **listy błędów** narzędzi, aby znaleźć błędy określonych na liście błędów. Można wyszukiwać według dowolnej kolumny widoczny na liście błędów i wyniki wyszukiwania zawsze są sortowane według kolumny, która ma priorytet sortowania zamiast na zapytanie lub zastosowaniu filtra. Jeśli wybierzesz **Esc** klucza, gdy fokus jest w **listy błędów**, można wyczyścić terminu wyszukiwania i filtrowania wyników wyszukiwania. Możesz również kliknąć **X** po prawej stronie pola tekstowego, aby je wyczyścić.  
  
## <a name="save"></a>Zapisanie  
 Można skopiować na liście błędów i zapisać go do pliku. Wybierz błędów, aby skopiować i kliknij prawym przyciskiem myszy zaznaczenie, a następnie w menu kontekstowym wybierz **kopiowania**. Następnie można wkleić błędy do pliku. Po wklejeniu błędy, aby arkusz kalkulacyjny programu Excel, pola są wyświetlane jako różnych kolumn.  
  
## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika  
 Ważność  
 Wyświetla różne typy **listy błędów** wpis (**błąd**, **komunikat**, **ostrzeżenie**, **ostrzeżenie (aktywny)**, **Ostrzeżenie (nieaktywny)**.  
  
 Kod  
 Wyświetla kod błędu.  
  
 Opis  
 Wyświetla tekst wpisu.  
  
 Projekt  
 Wyświetla nazwę bieżącego projektu.  
  
 Plik  
 Wyświetla nazwę pliku.  
  
 Wiersz  
 Wyświetla wiersz, w którym występuje problem.