---
title: "Wyświetlanie wartości danych w edytorze kodu etykietek danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 178bd1768474eaaaf760e2ef4feecfe0e1519bee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Podgląd wartości danych w etykietek danych w edytorze kodu
Etykietki danych Podaj wygodny sposób wyświetlania informacji na temat zmiennych w programie podczas debugowania. Etykietki danych działa tylko w trybie przerwania i tylko w przypadku zmiennych, które znajdują się w bieżącym zakresie wykonywania.
  
### <a name="to-display-a-datatip"></a>Aby wyświetlić etykietki danych  
  
1. Ustaw punkt przerwania i Rozpocznij debugowanie (naciśnij klawisz **F5**).

2. W przypadku, gdy wstrzymaniu w debugerze, umieść wskaźnik myszy na dowolnej zmiennej w bieżącym zakresie.
  
     Zostanie wyświetlone etykietek danych.
  
3.  Etykietek danych zniknie po usunięciu wskaźnik myszy. Aby przypiąć etykietek danych pozostaje otwarty, kliknij przycisk **numeru Pin do źródła** ikony lub kliknij prawym przyciskiem myszy w zmiennej, następnie kliknij przycisk **numeru Pin do źródła**.

    ![Przypinanie etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > W przypadku, gdy wykonanie jest wstrzymana, a nie w przypadku, gdy kursor znajduje się etykietki danych są zawsze obliczane w kontekście. Jeśli Aktywuj zmiennej w innej funkcji o takiej samej nazwie jako zmiennej, która znajduje się w bieżącym kontekście, wartość zmiennej w innych funkcji jest wyświetlana jako wartość zmiennej w bieżącym kontekście.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Aby odpiąć etykietki danych i zapewnić ich float  
  
-   W etykietki danych przypięte, kliknij przycisk **Odepnij ze źródła** ikony.  
  
     Ikona zmiany kodu pin odpiąć pozycji. Etykietek danych jest teraz wyświetlany powyżej wszystkie otwarte okna. Przestawne etykietek danych zamyka podczas kończenia sesji debugowania.  
  
### <a name="to-repin-a-floating-datatip"></a>Aby repin przestawne etykietek danych  
  
-   Etykietki danych kliknij ikonę numeru pin.  
  
     Ikona zmiany kodu pin przypiętych pozycji. W przypadku etykietek danych poza oknem źródła, ikonę pinezki jest wyłączona i nie może zostać unieruchomiony etykietek danych.  
  
### <a name="to-close-a-datatip"></a>Aby zamknąć etykietki danych  
  
-   Umieść wskaźnik myszy nad etykietki danych, a następnie kliknij przycisk **Zamknij** ikony.  
  
### <a name="to-close-all-datatips"></a>Aby zamknąć wszystkie etykietki danych  
  
-   Na **debugowania** menu, kliknij przycisk **wyczyść wszystkie etykietki danych**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Aby zamknąć wszystkie etykietki danych dla określonego pliku  
  
-   Na **debugowania** menu, kliknij przycisk **wyczyść wszystkie etykietki danych przypięte do** *pliku*.  
  
## <a name="expand-and-edit-information"></a>Rozwiń węzeł i edytować informacje o  
 Etykietki danych umożliwia rozwijanie tablicy, struktury lub obiekt, aby wyświetlić jego elementy członkowskie. Można również edytować wartość zmiennej z etykietek danych.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Aby rozwinąć zmiennej, aby zobaczyć jego elementy  
  
-   W etykietki danych, należy umieścić wskaźnik myszy  **+**  znak poprzedzający nazwę zmiennej.  
  
    Zmienna rozwijany, aby wyświetlić jego elementy w formie drzewa.

    ![Wyświetl etykietki danych](../debugger/media/dbg-tour-data-tips.gif "wyświetlenia etykietki danych")
  
    Po rozwinięciu zmiennej można użyj klawiszy strzałek na klawiaturze, aby przenieść w górę i w dół. Alternatywnie można użyć myszy.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Aby edytować wartość zmiennej przy użyciu etykietki danych  
  
1.  W etykietki danych kliknij wartość. To jest wyłączone dla wartości tylko do odczytu.  
  
2.  Wpisz nową wartość, a następnie naciśnij klawisz ENTER.  
  
## <a name="making-a-datatip-transparent"></a>Tworzenie etykietki danych przezroczyste  
 Jeśli chcesz wyświetlić kod, który znajduje się za etykietki danych, możesz wprowadzić etykietek danych tymczasowo przezroczysty. Dotyczy to etykietki danych przypięte lub zmiennoprzecinkową.  
  
#### <a name="to-make-a-datatip-transparent"></a>Aby etykietki danych przezroczyste  
  
-   Etykietki danych naciśnij klawisz CTRL.  
  
     Etykietek danych pozostanie przezroczysty pod warunkiem, przytrzymując klawisz CTRL.  
  
## <a name="visualize-complex-data-types"></a>Wizualizuj złożone typy danych  
 Ikonę lupy widoczna obok nazwy zmiennej w etykietek danych, co najmniej jeden [wizualizatorów](../debugger/create-custom-visualizers-of-data.md), takich jak [ciągu wizualizatorów](../debugger/string-visualizer-dialog-box.md), są dostępne dla zmiennych tego typu danych. Wizualizatora służy do wyświetlania informacji w sposób bardziej zrozumiałe, zwykle graficznego.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Aby wyświetlić zawartość zmienną przy użyciu wizualizatora  
  
-   Kliknij ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikona wizualizatora") aby wybrać domyślny Wizualizator dla typu danych.  
  
     —lub—  
  
     Kliknij strzałkę wyskakującego obok wizualizatora, aby wybrać z listy odpowiednią wizualizatorach typu danych.  
  
     Informacje wyświetlane wizualizatora.  
  
## <a name="add-information-to-a-watch-window"></a>Dodawanie informacji do okna czujki  
 Jeśli chcesz nadal oglądać zmiennej w widoku listy można dodać zmienną **czujki** etykietki danych w oknie.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Aby dodać zmienną do okna czujki  
  
-   Kliknij prawym przyciskiem myszy etykietki danych, a następnie kliknij przycisk **Dodaj wyrażenie kontrolne**.  
  
     Zmienna zostanie dodany do **czujki** okna. Jeśli używasz wersji, która obsługuje wiele **czujki** systemu windows, zmienna jest dodawany do **czujki 1.**  
  
## <a name="import-and-export-datatips"></a>Importowanie i eksportowanie etykietek danych  
 Możesz wyeksportować etykietek danych do pliku XML, który można udostępniać współpracownikom lub edytować za pomocą edytora tekstu.  
  
#### <a name="to-export-datatips"></a>Aby wyeksportować etykietek danych  
  
1.  Polecenie menu debugowania **wyeksportować etykietek danych**.  
  
     **Wyeksportować etykietek danych** zostanie wyświetlone okno dialogowe.  
  
2.  Przejdź do lokalizacji, w której chcesz zapisać plik XML, wpisz nazwę pliku w przy użyciu technik standardowego pliku **nazwę pliku** , a następnie kliknij przycisk **OK**.  
  
#### <a name="to-import-datatips"></a>Aby zaimportować etykietek danych  
  
1.  Polecenie menu debugowania **etykietek danych importu**.  
  
     **Etykietek danych importu** zostanie wyświetlone okno dialogowe.  
  
2.  Użyj okna dialogowego, aby znaleźć plik XML, który chcesz otworzyć, a następnie kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Oglądanie i QuickWatch systemu Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Utwórz niestandardowe Wizualizatory](../debugger/create-custom-visualizers-of-data.md)   