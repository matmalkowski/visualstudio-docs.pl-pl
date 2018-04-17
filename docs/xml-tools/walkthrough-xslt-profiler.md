---
title: 'Wskazówki: Profilera XSLT | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3338360e0acbcd9d4caea256074b892575c7bc6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-xslt-profiler"></a>Wskazówki: Profilera XSLT
Profilera XSLT tworzy szczegółowe raporty wydajności XSLT, które pomagają miary, oceny i docelowa problemów związanych z wydajnością w kodzie XSLT. Profilera XSLT zawiera wskazówki przydatne dla optymalizacji arkusza stylów XSL i XSLT. Dla aplikacji XSLT tego żądanie maksymalnej wydajności to narzędzie może być istotne.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
Procedury przedstawione w następujących wskazówki wymagają programu Visual Studio i .NET Framework w wersji 4.0 lub nowszej.
  
### <a name="create-the-performance-report"></a>Tworzenie raportu wydajności  
  
1.  Otwórz dokument XSLT w programie Visual Studio.  
  
2.  Polecenie **XSLT profilu** opcji, które są dostępne w XML menu.  
  
3.  Podaj wejściowy dokument XML. Jeśli dokument XML nie jest jeszcze otwarty, pojawi się monit dla pliku.  
  
4.  Analiza zostanie uruchomiony, oraz pasek postępu Wyświetla postęp w edytorze.  
  
5.  Dane wyjściowe XSLT jest widoczny w okienku danych wyjściowych.  
  
6.  Po zakończeniu sesji wydajności, sprawdź raportu wydajności. Dane zapisane w raport dotyczący wydajności służy do wyświetlania i analizowania wydajności XSLT.  
  
### <a name="get-all-the-available-views"></a>Pobierz wszystkie dostępne widoki  
  
1.  Polecenie **bieżący widok** listy rozwijanej, aby uzyskać wszystkie dostępne widoki.  
  
2.  Wybierz **widoku podsumowania** opcji **bieżący widok** listy rozwijanej. Domyślnie raport dotyczący wydajności jest wyświetlany w **widoku podsumowania**. Ten widok stanowi punkt wyjścia do określenia problemy z wydajnością z dokumentami XSLT. **Widoku podsumowania** wymieniono następujących punktów danych:  
  
    -   Większość funkcji o nazwie  
  
    -   Funkcje z największą ilością indywidualnej pracy  
  
    -   Funkcje najdłuższy czas poświęcony na wykonywanie  
  
3.  Domyślnie są trzy kolumny dla każdego punktu danych: nazwę funkcji, liczba wywołań w wartościach bezwzględnych i wartość procentową nazwanego funkcji do wywołania funkcji całkowitej. Z każdym danych punktu w **widoku podsumowania**, można przejść do bardziej szczegółowych widoków, klikając prawym przyciskiem myszy na punkty danych funkcji.  
  
4.  Wybierz **widoku funkcji** opcji **bieżący widok** listy rozwijanej. **Widoku funkcji** wymieniono funkcje wywoływane podczas profilowania. Dane można sortować, klikając nazwę kolumny. Kolumny domyślnie wyświetlane są:  
  
    -   **Nazwa funkcji**  
  
    -   **Całkowity czas, który upłynął**  
  
    -   **Czas, który upłynął wyłączności**  
  
    -   **Całkowity czas aplikacji**  
  
    -   **Własny czas aplikacji**  
  
    -   **Liczba wywołań**  
  
5.  Wszystkie kolumny czasu są wyświetlane w wartości bezwzględne i wartości procentowe. Termin **wyłącznego** odwołuje się do całkowitego czasu funkcji zużyte wykonywania z wyłączeniem czasu poświęconego przez inne funkcje wywoływane podczas wykonywania tej funkcji.  
  
6.  Termin **łącznie** odwołuje się do całkowity czas funkcję wykonywania, tym czas wykonywania wszystkich funkcji o nazwie i czy któregoś z powyższych wywołać funkcji o nazwie innych funkcji.  
  
### <a name="select-callercallee-view"></a>Wybierz widok wywołujący/wywoływany  
  
1.  Wybierz **wywołujący/wywoływany** wyświetlić w **bieżący widok** listy rozwijanej.  
  
2.  **Wywołujący/wywoływany** widok ma trzy osobne części:  
  
    -   **Funkcje, które wywołuje**: wszystkie funkcje, które wywołuje określonej funkcji znajduje się w górnej części widoku.  
  
    -   **Bieżąca funkcja**: konkretną funkcję, która została wywołana znajduje się w środkowej części widoku.  
  
    -   **Funkcje, które zostały wywołane przez** : wszystkie funkcje, które zostały wywołane przez konkretną funkcję znajduje się w dolnej części widoku.  
  
3.  Jeśli funkcja o nazwie `SyncToNavigator` pojawia się w środkowej części widoku wszystkie funkcje, które wywołuje `SyncToNavigator` funkcji są wyświetlane w górnej części widoku, a wszystkie funkcje, które zostały wywołane przez `SyncToNavigator` są wyświetlane w dolnej części widoku.  
  
4.  Funkcja w środkowej części widoku można zmienić, klikając dwukrotnie dowolne funkcje wymienione w dwóch częściach widoku. Widok jest następnie aktualizowany automatycznie zgodnie ze zmianami.  
  
5.  Można również posortować dane, kliknij nazwy kolumn.  
  
### <a name="select-calltree-view"></a>Wybierz widok widokach drzewa wywołań  
  
1.  Wybierz **widok drzewa wywołań** w **bieżący widok** listy rozwijanej. Ten widok jest widok drzewa wykonania programu.  
  
2.  **Widok drzewa wywołań** pokazuje korzeń drzewa jako nazwa procesu. Funkcje są węzłami drzewa. Ten widok służy do wejść śledzenia wywołań i analizować, które ślady ma największy wpływ na wydajność. Widok przypomina **widoku stosu wywołań** dostępne podczas debugowania. Oprócz kolumn w **widoku funkcji**w **widok drzewa wywołań**, brak dodatkową kolumnę do wyświetlenia **nazwy modułu**.  
  
3.  Wybierz **znaczniki** w **bieżący widok** listy rozwijanej.  
  
4.  SLT Profiler istnieją znaczniki widoczne w strumieniu zbierania danych z komentarzem skojarzone. Znaczniki są miejsca w kodzie, które mają liczników. Po przekazaniu profilera XSLT można zebrać liczników wydajności XSLT liczniki uzyskać zbierane za każdym razem, gdy jeden z tych znaków jest wykonywany. Dane są wyświetlane w tabeli zawierających **Identyfikator znacznika**, **Nazwa znacznika** (**uruchomić Program**, **Program zakończenia**) i  **Sygnatury czasu**. Znaki nie są zagregowane i wyświetlane w kolejności chronologicznej w **widoku znaczniki** raportu wydajności.  
  
### <a name="select-modules-in-the-current-view"></a>Wybierz moduł w bieżącym widoku  
  
1.  Wybierz **modułów** w **bieżący widok** listy rozwijanej.  
  
2.  Widok modułów jest płaska lista wszystkich funkcji agregować na poziomie modułu. Rozwiń lub Zwiń Nazwa modułu do wyświetlania lub zamknąć widok danych wydajności modułu. Dane można sortować, klikając nazwę kolumny. Domyślnie są zarówno wartości bezwzględne i numerów procent **upłynął całkowity czas**, **Upłynęło czasu wyłącznego**, **całkowity czas aplikacji**, **Własny czas aplikacji**, i **liczba wywołań**.  
  
3.  Wybierz **procesu** w **bieżący widok** listy rozwijanej.  
  
4.  Widok procesu zawiera tabelę, która zawiera **identyfikator procesu**, **nazwa procesu**, **czas rozpoczęcia**i **czas zakończenia**. Dane można sortować, klikając nazw kolumn.  
  
## <a name="see-also"></a>Zobacz też  
[Przewodnik: Korzystanie z hierarchii XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)