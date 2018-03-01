---
title: "Przy użyciu zapisywane są dane funkcji IntelliTrace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 37c4c82dc3edb1abcad9dc212040864155deb1a6
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="using-saved-intellitrace-data"></a>Przy użyciu zapisanych danych funkcji IntelliTrace
Przejdź do określonych punktów podczas wykonywania aplikacji po rozpoczęciu debugowania z pliku IntelliTrace (.iTrace) dziennika. Ten plik może zawierać zdarzenia dotyczące wydajności, wyjątki wątków, kroków testu, moduły i inne informacje o systemie, czy rekordów funkcji IntelliTrace podczas sekwencji aplikacji.  
  
 Upewnij się, że masz:  
  
-   Dopasowywanie plików źródłowych i plików symboli (.pdb) dla kodu aplikacji. W przeciwnym razie program Visual Studio nie można rozpoznać lokalizacji źródłowej i zawiera komunikat "Nie odnaleziono symboli". Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) i [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).  
  
-   Visual Studio Enterprise (ale nie Professional lub Community Edition) na komputerze dewelopera lub innym komputerze można otworzyć .iTrace, pliki  
  
-   Plik .iTrace z jednego z tych źródeł:  
  
    |**Źródło**|**Zobacz**|  
    |----------------|-------------|  
    |Sesji funkcji IntelliTrace w Visual Studio Enterprise (ale nie Professional lub Community Edition)|[Funkcje IntelliTrace](../debugger/intellitrace-features.md)|  
    |Sesję testu w programie Microsoft Test Manager. Pliku .iTrace to dołącza do elementu roboczego Team Foundation Server.|[Zbieranie większej ilości danych podczas wykonywania testów ręcznych](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|  
    |Microsoft Monitoring Agent, albo samodzielnie lub z programu System Center 2012 R2 Operations Manager, platformy ASP.NET sieci web aplikacji i systemem we wdrożeniu aplikacji SharePoint|-   [Diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md)<br />-   [Co to jest nowe w programie System Center 2012 R2 Operations Manager](http://technet.microsoft.com/library/dn249700.aspx)|  
  
##  <a name="GetStarted"></a>Co chcesz zrobić?  
  
-   [Otworzyć dziennika funkcji IntelliTrace](#Open)  
  
-   [Zrozumienie dziennika funkcji IntelliTrace](#Understand)  
  
-   [Rozpocznij debugowanie z dziennika funkcji IntelliTrace](#StartDebugging)  
  
##  <a name="Open"></a>Otworzyć dziennika funkcji IntelliTrace  
 Na komputerze przy użyciu programu Visual Studio Enterprise Otwórz plik .iTrace.  
  
-   Kliknij dwukrotnie plik .iTrace poza programem Visual Studio lub Otwórz plik w programie Visual Studio.  
  
     \-lub -  
  
-   Jeśli pliku .iTrace jest dołączony do elementu roboczego Team Foundation Server, wykonaj następujące kroki w elementu roboczego:  
  
    -   W obszarze **wszystkie linki**, odnaleźć pliku .iTrace. Go otworzyć.  
  
         \-lub -  
  
    -   W obszarze **Opisz kroki**, wybierz **IntelliTrace** łącza.  
  
> [!TIP]
>  Jeśli został zamknięty pliku funkcji IntelliTrace podczas debugowania, możesz uruchomić go w prosty sposób. Przejdź do **debugowania** menu, wybierz **IntelliTrace**, **wyświetlić podsumowanie dziennika**. Można również wybrać **wyświetlić podsumowanie dziennika** w **IntelliTrace** okna. To jest dostępna tylko podczas debugowania przy użyciu funkcji IntelliTrace.  
  
##  <a name="Understand"></a>Zrozumienie dziennika funkcji IntelliTrace  
 Niektóre z następujących sekcji w pliku .iTrace są wyświetlane tylko wtedy, gdy użytkownik zbiera dane z określonego źródła, na przykład z programu Test Manager lub z aplikacji programu SharePoint.  
  
|**Sekcja**|**Zawiera**|**Źródło kolekcji**|  
|-----------------|------------------|---------------------------|  
|[Naruszeń wydajności](#Performance)|Zdarzenia wydajności z wywołania funkcji, które przekracza skonfigurowany próg|Microsoft Monitoring Agent, albo autonomiczny moduł zbierający lub za pomocą programu System Center 2012 R2 Operations Manager dla aplikacji sieci web ASP.NET hostowanych w usługach IIS|  
|[Dane wyjątku](#ExceptionData)|Wyjątki, łącznie ze stosu wywołań pełny dla każdego wyjątku|Wszystkie źródła|  
|[Analiza](#Analysis)|SharePoint 2010 oraz SharePoint 2013 tylko dla aplikacji. Diagnozowanie zdarzenia funkcji IntelliTrace i programu SharePoint, na przykład zdarzenia debugera, ULS zdarzeń nieobsługiwanych wyjątków i inne dane, które są zarejestrowane w usłudze Microsoft Monitoring Agent.|Microsoft Monitoring Agent, albo autonomiczny moduł zbierający lub za pomocą programu System Center 2012 R2 Operations Manager|  
|[Informacje o systemie](#SystemInfo)|Ustawienia i specyfikacji systemu hosta|Wszystkie źródła|  
|[Lista wątków](#ThreadsList)|Wątki uruchomione podczas zbierania|Wszystkie źródła|  
|[Dane testowe](#TestData)|Kroki testu i ich wyniki z sesji testowania|Test Manager|  
|[Moduły](#Modules)|Moduły załadowanych w kolejności ich załadować procesu docelowego.|Wszystkie źródła| 
|[Żądanie sieci Web](#Modules)|Dane żądania sieci Web w środowisku produkcyjnym IIS sieci web, aplikacji i programu SharePoint 2010 oraz SharePoint 2013|Microsoft Monitoring Agent i autonomiczny moduł zbierający| 
  
 Oto kilka porad ułatwiających znajdowanie informacji w każdej sekcji:  
  
-   Wybierz nagłówek kolumny, aby posortować dane.  
  
-   Użyj pola wyszukiwania do filtrowania danych. Zwykły tekst wyszukiwania działa we wszystkich kolumnach, z wyjątkiem kolumn czasu. Można również filtrować wyszukiwania do określonej kolumny z jednego filtru dla kolumny. Wpisz nazwę kolumny nie może zawierać spacji, dwukropek (**:**), a wartość wyszukiwania. Wykonaj to średnikiem (**;**), aby dodać inną wartość w kolumnie i wyszukiwania.  
  
     Na przykład można znaleźć zdarzeń wydajności, które mają słowo "powolna" w **opis** kolumny, wpisz:  
  
     `Description:slow`  
  
##  <a name="StartDebugging"></a>Rozpocznij debugowanie z dziennika funkcji IntelliTrace  
  
###  <a name="Performance"></a>Naruszeń wydajności  
 Przejrzyj zdarzenia wydajności, które zostały zarejestrowane dla aplikacji. Te zdarzenia, które nie występują często można ukryć.  
  
##### <a name="to-start-debugging-from-a-performance-event"></a>Aby rozpocząć debugowanie z zdarzeń wydajności  
  
1.  W obszarze **naruszeń wydajności**, przejrzyj zdarzenia zarejestrowane wydajności, łączny czas wykonywania i innych informacji o zdarzeniu. Następnie zagłęb się w metody, które zostały wywołane podczas zdarzenia dotyczącego wydajności.  
  
     ![Wyświetl szczegóły zdarzeń dotyczących wydajności](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Możesz także po prostu dwukrotnie kliknąć zdarzenie.  
  
2.  Na stronie zdarzeń przejrzyj czasy wykonania dla tych wywołań. Odszukaj spowalniające wywołanie w drzewie wykonywania.  
  
     Najwolniejsze wywołania pojawiają się we własnej sekcji w przypadku wielu wywołań, zagnieżdżonych lub innych.  
  
3.  Rozwiń węzeł, że wywołanie wyświetlić zagnieżdżone wywołania i wartości parametrów, które zostały zarejestrowane w danym momencie.  
  
     (Klawiatury: Aby wyświetlić lub ukryć zagnieżdżone wywołania, naciśnij klawisz **Strzałka w prawo** lub **Strzałka w lewo** odpowiednio klucza. Aby pokazać lub ukryć wartości parametrów dla wywołania zagnieżdżonych, naciśnij klawisz **miejsca** klucza.)  
  
     Uruchom profilowanie z wywołania.  
  
     ![Rozpocznij debugowanie z wywołania metody](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Można także po prostu kliknij dwukrotnie połączenie lub naciśnij klawisz **Enter** klucza.  
  
     Jeśli metoda ta jest w kodzie aplikacji, program Visual Studio przechodzi do tej metody.  
  
     ![Przejdź do kodu aplikacji ze zdarzenia wydajności](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Teraz można przeglądać inne zarejestrowane wartości stosu wywołań kroków opisanych w kodzie, lub użyj **IntelliTrace** okna [przechodzenie wstecz lub do przodu "w czasie" między innymi metodami](../debugger/intellitrace.md) które zostały wywołane podczas To zdarzenie wydajności.  
  
###  <a name="ExceptionData"></a>Dane wyjątku  
 Przejrzyj wyjątki, które były generowane i zarejestrowane dla aplikacji. Możesz grupować wyjątki, które mają ten sam typ i stos wywołań, aby zobaczyć najnowsze wyjątek.  
  
##### <a name="to-start-debugging-from-an-exception"></a>Aby rozpocząć debugowanie z Wystąpił wyjątek  
  
1.  W obszarze **wyjątku**, przejrzeć zdarzenia zarejestrowane wyjątków, ich typów, wiadomości, i gdy wystąpiły wyjątki. Aby poznać więcej szczegółów związanych z kodem, rozpocznij debugowanie od ostatniego zdarzenia w grupie wyjątków.  
  
     ![Rozpocznij debugowanie z zdarzenie wyjątku](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Możesz także po prostu dwukrotnie kliknąć zdarzenie. Jeśli nie są grupowane zdarzenia, wybierz **debugowania tego zdarzenia**.  
  
     Jeśli wystąpił wyjątek w kodzie aplikacji, program Visual Studio przechodzi do tego miejsca.  
  
     ![Przejdź do kodu aplikacji z zdarzenie wyjątku](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, lub użyj **IntelliTrace** okna [przechodzenie wstecz lub do przodu "w czasie" między inne zarejestrowane zdarzenia](../debugger/intellitrace.md), kodu powiązanego i rejestrowane w wartości te punkty w czasie.  
  
    |**Kolumny**|**Pokazuje**|  
    |----------------|-------------------|  
    |**Typ**|Typ architektury .NET wyjątku|  
    |**Najnowsze wiadomości** dla grupowane wyjątków lub **komunikat** niezgrupowane wyjątków|Komunikat wyjątku|  
    |**Liczba** dla grupowane wyjątków|Ile razy został zgłoszony wyjątek|  
    |**Identyfikator wątku** niezgrupowane wyjątków|Identyfikator wątku, który zgłosił wyjątek|  
    |**Czas trwania zdarzenia najnowsze** lub **czas trwania zdarzenia**|Sygnatura czasowa rejestrowane, gdy wyjątek został zgłoszony|  
    |**Stos wywołań**|Stos wywołań dla wyjątku.<br /><br /> Aby zobaczyć stos wywołań, wybierz z listy wyjątków. Stos wywołań pojawia się poniżej listy wyjątków.|  
  
###  <a name="Analysis"></a>Analiza  
 Diagnozowanie problemów z aplikacjami programu SharePoint 2010 oraz SharePoint 2013 za pomocą identyfikator korelacji programu SharePoint lub przejrzyj nieobsługiwanych wyjątków, które można odnaleźć programu Microsoft Monitoring Agent.  
  
-   Użyj identyfikator korelacji programu SharePoint można znaleźć jego zgodne żądanie sieci web i zdarzeń. Wybierz zdarzenie, a następnie uruchom debugowanie w punkcie, gdzie i kiedy zdarzenie wystąpiło.  
  
-   Jeśli programu Microsoft Monitoring Agent znaleziono nieobsługiwane wyjątki, wybierz wyjątek, a następnie uruchom debugowanie w punkcie gdzie i kiedy wystąpił wyjątek.  
  
##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Uruchom debugowanie z identyfikatorem korelacji programu SharePoint  
  
1.  Skopiuj identyfikator korelacji programu SharePoint z jej źródła.  
  
     Na przykład:  
  
     ![IntelliTrace &#45; Błąd programu SharePoint &#45; Identyfikator korelacji](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")  
  
2.  Otwórz plik .iTrace, a następnie przejdź do **analizy** i wprowadź identyfikator korelacji programu SharePoint, aby przejrzeć zgodne żądanie sieci web i zarejestrowane zdarzenia.  
  
     ![Dziennika IntelliTrace &#45; Wprowadź identyfikator korelacji programu SharePoint](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")  
  
3.  W obszarze **żądania zdarzenia**, przejrzeć zdarzenia. Począwszy od góry, zdarzenia są wyświetlane w kolejności ich wystąpił.  
  
    1.  Wybierz zdarzenie, aby wyświetlić jego szczegóły.  
  
    2.  Wybierz **Rozpocznij debugowanie** można rozpocząć debugowania w momencie, w którym wystąpiło zdarzenie.  
  
     ![Plik dziennika IntelliTrace &#45; Wyświetl żądania sieci web i 43; zdarzenia](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")  
  
 Możesz zobaczyć te rodzaje zdarzeń programu SharePoint oraz zdarzenia funkcji IntelliTrace:  
  
-   **Zdarzenia profilu użytkownika**  
  
     Tych zdarzeń, SharePoint ładuje profilu użytkownika i właściwości profilu użytkownika są odczytywane lub zmienić.  
  
-   **Ujednolicone zdarzeń systemu rejestrowanie (ULS)**  
  
     Microsoft Monitoring Agent rejestruje podzbiór tych pól i zdarzenia ULS programu SharePoint:  
  
    |**Pole IntelliTrace**|**Pole ULS programu SharePoint**|  
    |----------------------------|------------------------------|  
    |**Identyfikator**|**Identyfikator zdarzenia**|  
    |**Poziom**|**Poziom**|  
    |**Identyfikator kategorii**|**Identyfikator kategorii**|  
    |**Kategoria**|**Kategoria**|  
    |**Obszar**|**Produktu**|  
    |**Output**|**Komunikat**|  
    |**Identyfikator korelacji**|**Identyfikator korelacji**|  
  
##### <a name="start-debugging-from-an-unhandled-exception"></a>Uruchom debugowanie z nieobsłużonego wyjątku  
  
1.  Wybierz identyfikator korelacji programu SharePoint dla wyjątku. Wyjątki są grupowane według typu i stos wywołań.  
  
2.  (Opcjonalnie) Rozwiń węzeł **stos wywołań** aby zobaczyć stos wywołań wyjątków grupy.  
  
3.  Wybierz **debugowania wyjątek** można rozpocząć debugowania w punkcie, gdzie i kiedy wystąpił wyjątek.  
  
     ![Dziennika IntelliTrace &#45; SharePoint nieobsługiwane wyjątki](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")  
  
 Aby uzyskać wskazówki, zobacz [wskazówki: debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md). Dla typów danych, które rekordy agenta, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
###  <a name="ThreadsList"></a>Lista wątków  
 Sprawdź, czy zarejestrowane wątków, które były uruchamiane w procesie docelowym. Można uruchomić debugowania z pierwszego prawidłowy zdarzenia funkcji IntelliTrace w wybranych wątku.  
  
##### <a name="to-start-debugging-from-a-specific-thread"></a>Aby rozpocząć debugowanie z określonego wątku  
  
1.  W obszarze **listy wątków**, wybierz wątku.  
  
2.  W dolnej części **listy wątków**, wybierz **Rozpocznij debugowanie**. Możesz również kliknąć dwukrotnie wątek.  
  
     Aby rozpocząć debugowanie, z którym rozpoczyna się aplikacji, kliknij dwukrotnie **wątku głównego**. Zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
 Użytkownik tworzy dane wątku mogą być przydatne bardziej niż wątków, które serwer tworzy i którymi zarządza dla aplikacji hostowanych przez usługi IIS sieci Web.  
  
|**Kolumny**|**Pokazuje**|  
|----------------|-------------------|  
|**IDENTYFIKATOR**|Identyfikator wątku|  
|**Nazwa**|Nazwa wątku. Nienazwane wątki są wyświetlane jako "\<bez nazwy >".|  
|**Godzina rozpoczęcia**|Godzina utworzenia wątku|  
|**Godzina zakończenia**|Czas zakończenia wątku|  
  
###  <a name="TestData"></a>Dane testowe  
 Przeanalizuj dane funkcji IntelliTrace, który Test Manager zapisane podczas testowania aplikacji.  
  
##### <a name="to-start-debugging-from-a-specific-test-step"></a>Aby rozpocząć debugowanie z kroku specyficznego testu  
  
1.  Rozwiń węzeł **testowania czynności siatki**. Wybierz krok testu.  
  
2.  W dolnej części **siatki kroki testu**, wybierz **Rozpocznij debugowanie**. Możesz również kliknąć dwukrotnie krok testu.  
  
     Spowoduje to uruchomienie debugowania z pierwszego zdarzenia funkcji IntelliTrace prawidłowe po wybrane kroki testu.  
  
     Jeśli istnieje danych testowych, IntelliTrace próbuje rozpoznać skojarzone kompilacji Team Foundation Server, która została użyta do wykonania uruchomienia testu. Jeśli kompilacja zostanie znaleziony, skojarzony symboli dla aplikacji są rozpoznawane automatycznie.  
  
|**Pole**|**Pokazuje**|  
|---------------|-------------------|  
|**Sesja testowa**|Sesje testowania, które zostały zarejestrowane. Zazwyczaj jest tylko jeden. Ta lista jest pusta, jeśli dane testowe został utworzony przy użyciu ręcznego testu eksploracyjnego.|  
|**Przypadek testowy**|Przypadki testowe z sesji wybranego testu. Ta lista jest pusta, jeśli dane testowe został utworzony przy użyciu ręcznego testu eksploracyjnego.|  
|**Siatka kroki testu**|Kroki, które zostały zarejestrowane w wyniku testu przebiegu testu lub zakończyć się niepowodzeniem|  
  
###  <a name="SystemInfo"></a>Informacje o systemie  
 W tej sekcji przedstawia szczegółowe informacje dotyczące systemu, który hostował aplikacji, na przykład, sprzętu, systemu operacyjnego, informacje dotyczące procesu i środowiska.  
  
###  <a name="Modules"></a>Moduły  
 W tej sekcji przedstawiono moduły załadowane procesu docelowego. Moduły są wyświetlane w kolejności ich załadowane.  
  
|**Kolumny**|**Pokazuje**|  
|----------------|-------------------|  
|**Nazwa modułu**|Nazwa pliku modułu|  
|**Ścieżka modułu**|Lokalizacja, w której moduł został załadowany na dysku|  
|**Identyfikator modułu**|Unikatowy identyfikator moduł, który jest przeznaczone do wersji i przyczynia się do pasujących plików symboli (PDB). Zobacz [wyszukiwanie plików symboli (.pdb) i pliki źródłowe](http://msdn.microsoft.com/en-us/05384c85-d264-4e18-abaa-aa482ab25470).|  
  
### <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?  
 [Za pomocą autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
 [Funkcje IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Zbieranie większej ilości danych podczas wykonywania testów ręcznych](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
#### <a name="forums"></a>Fora  
 [Debuger programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
#### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 6: testowanie przybornika](http://go.microsoft.com/fwlink/?LinkID=255203)