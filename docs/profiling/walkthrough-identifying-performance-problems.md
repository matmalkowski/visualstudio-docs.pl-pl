---
title: "Wskazówki: Identyfikowanie problemów z wydajnością | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: da961d153713c996c6f057e7bb0366c747c87205
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-identifying-performance-problems"></a>Wskazówki: Identyfikowanie problemów z wydajnością
W tym przewodniku pokazano, jak profile aplikacji do identyfikowania problemów z wydajnością.  
  
 W tym przewodniku będzie kroków procesu profilowania zarządzaną aplikację i za pomocą próbkowania i instrumentacji w celu odizolowania i zidentyfikować problemy z wydajnością w aplikacji.  
  
 W tym przewodniku będzie wykonaj następujące kroki:  
  
-   Profil aplikacji za pomocą metody pobierania próbek.  
  
-   Analizuj próbkowanych wyniki profilowania odszukaj i rozwiąż problem z wydajnością.  
  
-   Profil aplikacji przy użyciu metody instrumentacji.  
  
-   Analiza zinstrumentowanego profilowania wyników odszukaj i rozwiąż problem z wydajnością.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   Pośredni opis języka C#.  
  
-   Kopię [PeopleTrax — przykład](../profiling/peopletrax-sample-profiling-tools.md).  
  
 Aby pracować z informacjami pochodzącymi profilowania, jest najlepszym rozwiązaniem jest dostępne informacje dotyczące symboli debugowania.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody pobierania próbek  
 Próbkowanie to metodę profilowania za pomocą którego proces zagrożona okresowo wysyłane ustalenie active funkcji. Dane wynikowe zapewnia liczenie częstotliwość zagrożona funkcja znajdowała się na szczycie stosu wywołań proces był wtedy próbkowany.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>Profilowanie aplikacji za pomocą metody pobierania próbek  
  
1.  Otwórz [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] z uprawnieniami administratora. Uruchomione z uprawnieniami administratora jest wymagana dla profilowania.  
  
2.  Otwórz rozwiązanie PeopleTrax.  
  
     Rozwiązanie PeopleTrax wypełnia teraz Eksploratora rozwiązań.  
  
3.  Określ dla ustawienia konfiguracji projektu **wersji**.  
  
     Kompilację wersji należy używać do wykrywania problemów z wydajnością w aplikacji. Kompilacji wydania jest zalecane dla profilowania, ponieważ Kompilacja debugowania ma dodatkowe informacje skompilowany do niego, które mogą negatywnie wpłynąć na wydajność i nie ilustrują problemy z wydajnością, dokładnie.  
  
4.  Na **Analizuj** menu, wybierz opcję **wydajności programu profilującego**, a następnie wybierz pozycję **kreatora osiągów**, a następnie wybierz **Start**.  
  
     Zostanie wyświetlony Kreator wydajności.  
  
5.  Upewnij się, że **próbkowania procesora CPU (zalecane)** jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
6.  W **aplikacji, które chcesz docelowe dla profilowania**wybierz PeopleTrax, a następnie kliknij przycisk **dalej**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]tworzy projekt i rozpoczyna się do profilu aplikacji. **PeopleTrax** zostanie wyświetlone okno aplikacji.  
  
7.  Kliknij przycisk **uzyskać osób**.  
  
8.  Kliknij przycisk **ExportData**.  
  
     Notatnik otwiera i wyświetla nowy plik zawierający wyeksportowane dane z **PeopleTrax**.  
  
9. Zamknij Notatnik, a następnie Zamknij **PeopleTrax** aplikacji.  
  
     Profiler generuje dane profilowania (\*Vsp) plików, określa nazwę pliku w sekcji raportów okno Eksploratora wydajności i automatycznie ładuje **Podsumowanie** widoku pliku danych w oknie głównym [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
#### <a name="to-analyze-sampled-profiling-results"></a>Do analizowania próbkowany profilowania wyników  
  
1.  Widok podsumowania przedstawia osi czasu użycia procesora CPU w trakcie przebiegu, profilowania **aktywnej ścieżki** listy, która reprezentuje gałęzi drzewo wywołań aplikacji, który był aktywny najbardziej oraz listę  **Funkcje wykonywania najwięcej indywidualnej pracy** który zawiera funkcje, które zostały poddane próbkowaniu najczęściej podczas wykonywania kodu w ich własnych treści funkcji.  
  
     Sprawdź **aktywnej ścieżki** listy i zwróć uwagę, że metoda PeopleNS.People.GetNames jest funkcja PeopleTrax najbliżej koniec listy. Położenia ułatwia odpowiednimi kandydatami do analizy. Kliknij nazwę funkcji, aby wyświetlić szczegóły GetNames w **szczegółów funkcji** widoku.  
  
2.  **Szczegółów funkcji** widok zawiera dwa okna. Okno podziału kosztów zawiera widoku graficznego elementów pracy przez funkcję, pracy wykonanej przez funkcje, które mu i udziału funkcje, które wywołuje funkcję liczby wystąpień, które zostały poddane próbkowaniu. Funkcja, która jest fokus widoku, klikając nazwę funkcji, można zmienić. Na przykład kliknięcie PeopleNS.People.GetPeople dokonanie GetPeople wybranej funkcji.  
  
     **Widoku kodu funkcji** okno zawiera kod źródłowy dla tej funkcji, jeśli jest dostępny i prezentuje najdroższych wiersze w wybranej funkcji. Po wybraniu GetNames widać, że ta funkcja odczytuje ciągu z zasobów aplikacji, a następnie używa <xref:System.IO.StringReader> można dodać każdego wiersza w ciągu na <xref:System.Collections.ArrayList>. Nie istnieje sposób widocznych w celu zoptymalizowania tej funkcji.  
  
3.  Ponieważ PeopleNS.People.GetPeople tylko wywołującej GetNames, kliknij przycisk GetPeople w oknie dystrybucji kosztów do sprawdzenia kodu. Ta metoda zwraca <xref:System.Collections.ArrayList> PersonInformationNS.PersonInformation obiektów z nazwy osób i firm utworzonego przez GetNames. Jednak GetNames jest wywoływana dwukrotnie każdorazowym tworzony jest obiekt PersonInformation. Widać metody mogą być łatwo optymalizowane przez utworzenie listy tylko raz na początku metody i przeprowadzane jest indeksowanie do tych list podczas tworzenia PersonInformation pętli.  
  
4.  Alternatywnej wersji GetPeople jest dostarczana z przykładowym kodzie aplikacji i można wywołać funkcję zoptymalizowanego przez dodanie do właściwości kompilacji symbol kompilacji warunkowej. W oknie Solution Explorer, kliknij prawym przyciskiem myszy projekt osób, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **kompilacji** w menu strony właściwości, a następnie wpisz **OPTIMIZED_GETPEOPLE** w polu tekstowym symbol kompilacji warunkowej. Zoptymalizowana wersja GetPeople zastępuje oryginalnej metody w następnej kompilacji.  
  
5.  Uruchom ponownie sesję wydajności. Kliknij na pasku narzędzi Eksplorator wydajności **uruchomienie z profilowania**. Kliknij przycisk **uzyskać osób** , a następnie kliknij przycisk **eksportowanie danych**. Zamknij okno programu Notatnik, która pojawia się, a następnie zamknij aplikację Trax osoby.  
  
     Nowy plik danych profilowania jest generowany, a **Podsumowanie** nowe dane są wyświetlane w widoku [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] głównego okna.  
  
6.  Aby porównać dwa przebiegi profilowania, wybierz dwa danych plików w Eksploratorze wydajności, kliknij prawym przyciskiem myszy plik, a następnie kliknij **raporty porównanie wydajności**. Zostanie wyświetlone okno raportu porównawczego w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] głównego okna. **Delta** kolumna zawiera zmiany w wartości wydajności funkcji z wcześniej **linii bazowej** wartość do późniejszej **porównanie** wartość. Można wybrać wartości do porównania z **kolumny** listy rozwijanej. Wybierz **przykłady włącznie %**.  
  
     Zwróć uwagę, że metody GetPeople i GetNames Pokaż wzrost wydajności znaczne.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilowanie przy użyciu metody Instrumentacji  
 Instrumentacja to metodę profilowania, w którym profilera wstawia funkcji badania do specjalnie wbudowanych wersje PROFILOWANEGO plików binarnych. Sondy zbierać informacji wejścia i wyjścia funkcji w modułach instrumentowanych i wszystkie witryny wywołanie w tych funkcji. Proces Instrumentacji jest przydatne w przypadku badania problemów związanych z operacji wejścia/wyjścia, takich jak zapis na dysku i komunikacji za pośrednictwem sieci. Instrumentacja zawiera więcej szczegółowych informacji niż próbkowanie, ale jest bardziej natrętnych w procesie wykonywania i wiąże się z większej liczbie czynności. Instrumentowanych danych binarnych jest większy niż debugowania lub wersji plików binarnych i nie są przeznaczone do wdrożenia.  
  
 W tej sekcji tego przewodnika, aby dowiedzieć się więcej kodu, który firma Microsoft może zoptymalizować w używanej aplikacji PeopleTrax możemy profilowane wcześniej zostanie wykorzystany metody instrumentacji. Przy użyciu filtru widok podsumowania osi czasu, firma Microsoft dotyczą nasze analizy scenariusza danych eksportu w naszej aplikacji PROFILOWANEGO, w którym napisano listy osób do pliku Notatnika.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>Do profilu istniejących aplikacji przy użyciu metody Instrumentacji  
  
1.  Jeśli to konieczne, Otwórz aplikację PeopleTrax w programie Visual Studio.  
  
     Upewnij się, że uruchamiasz jako Administrator i że konfiguracja kompilacji dla rozwiązania jest ustawiona na **wersji**.  
  
2.  W Eksploratorze wydajności kliknij **Instrumentacji**.  
  
3.  Kliknij na pasku narzędzi Eksplorator wydajności **uruchomienie z profilowania**.  
  
     Profiler kompilacji projektu i uruchamia do profilu aplikacji. Zostanie wyświetlone okno aplikacji PeopleTrax.  
  
4.  Kliknij przycisk **uzyskać osób**.  
  
     Siatki danych PeopleTrax wypełnia danych.  
  
5.  Poczekaj około 10 sekund, a następnie kliknij przycisk **eksportowanie danych**.  
  
     **Notatnik** uruchamia i wyświetla nowy plik, który zawiera listę użytkowników z PeopleTrax. Oczekiwanie umożliwia aby łatwiej zidentyfikować dane eksportowania procedury w celu filtrowania.  
  
6.  Zamknij **Notatnik**, a następnie Zamknij **PeopleTrax** aplikacji.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]generuje raport sesji wydajności (*.vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>Do analizowania zinstrumentowanego profilowania wyników  
  
1.  Oś czasu wykresu **Podsumowanie** widok raportu przedstawia wykorzystanie procesora CPU programu w czasie trwania profilowania wykonywania. Operacji eksportowania danych powinien być duża szczytu lub płaska po prawej stronie wykresu. Firma Microsoft można filtrować sesji wydajności, aby wyświetlać i analizować tylko dane zebrane w ramach operacji eksportowania. Kliknij, aby lewej strony punktu na wykresie, w którym rozpoczyna się operacji eksportowania danych. Ponownie kliknij z prawej strony działania. Następnie kliknij przycisk **Filtruj według wyboru** na liście łącza do prawej osi czasu.  
  
     **Aktywnej ścieżki** drzewa pokazują, że <xref:System.String.Concat%2A> metodę, która jest wywoływana przez metodę PeopleTrax.Form1.ExportData zużywa duże procent czasu. Ponieważ **System.String.Concat** jest również w górnej części **funkcji z najbardziej indywidualnej pracy** listy skrócenie czasu potrzebnego do funkcji jest prawdopodobnie punktem optymalizacji.  
  
2.  Kliknij dwukrotnie **System.String.Concat** w podsumowania tabel, aby uzyskać więcej informacji, w widoku szczegółów funkcji.  
  
3.  Widać, że PeopleTrax.Form1.ExportData jest jedyną metodą, która wywołuje Concat. Kliknij przycisk **PeopleTrax.Form1.ExportData** w **podczas wywoływania funkcji** listę, aby wybrać metodę jest jako element docelowy widok szczegółów funkcji.  
  
4.  Sprawdź, czy metoda w oknie funkcji widoku kodu. Zwróć uwagę, że nie istnieją żadne literału wywołań **System.String.Concat**. Zamiast tego, istnieje kilka zastosowań operandu +=, które kompilator zastępuje wywołań **System.String.Concat**. Wszelkie zmiany w ciągu w programie .NET Framework, że nowe parametry do przydzielenia. .NET Framework obejmuje <xref:System.Text.StringBuilder> klasy, która jest zoptymalizowana pod kątem ciągów  
  
5.  Aby zastąpić ten obszar problem zoptymalizowanego kodu, do projektu PeopleTrax należy dodać OPTIMIZED_EXPORTDATA jako symbole kompilacji warunkowej.  
  
6.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt PeopleTrax, a następnie kliknij przycisk **właściwości**.  
  
     Zostanie wyświetlony formularz Właściwości projektu PeopleTrax.  
  
7.  Kliknij przycisk **kompilacji** kartę.  
  
8.  W **symbole kompilacji warunkowej** polu tekstowym **OPTIMIZED_EXPORTDATA**.  
  
9. Zamknij formularz Właściwości projektu i wybierz polecenie **Zapisz wszystkie** po wyświetleniu monitu.  
  
 Uruchom ponownie aplikację, zobaczysz oznaczone poprawę wydajności. Zaleca się uruchomienie sesji profilowania ponownie, nawet jeśli istnieją użytkownika widoczne udoskonalenia w zakresie wydajności. Przeglądania danych po rozwiązaniu problemu jest ważne, ponieważ pierwszy problem mogą przesłaniać inny problem.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [/ Z7, / zi, /ZI (Format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format)