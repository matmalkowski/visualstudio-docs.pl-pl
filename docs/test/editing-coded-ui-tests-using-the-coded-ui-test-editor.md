---
title: "Edytowanie kodowanych testów interfejsu użytkownika za pomocą edytora testu kodowanego interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codedUItest.testeditor
helpviewer_keywords: coded UI test, Coded UI Test Editor
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 2302c2bbfbd38ff307335b525aa319afb5f07e25
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Edycja zakodowanych testów interfejsu użytkownika za pomocą edytora kodowanych testów interfejsu użytkownika
Edytor kodowanego testu interfejsu użytkownika pozwala łatwo zmodyfikować kodowanych testów interfejsu użytkownika. Za pomocą edytora testu interfejsu użytkownika na stałe, można znaleźć, Wyświetl i Edytuj właściwości metody testowe i działania interfejsu użytkownika. Ponadto można użyć mapy formantów interfejsu użytkownika do wyświetlania i edytowania ich kontroli.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Dlaczego należy to zrobić?  
 Za pomocą edytora testu interfejsu użytkownika na stałe jest szybsza i bardziej wydajna niż Edycja kodu za pomocą edytora kodu metody kodowanego testu interfejsu użytkownika. Z kodowanego interfejsu użytkownika edytora testów, aby szybko znaleźć i zmodyfikować wartości właściwości skojarzonych z akcji interfejsu użytkownika i kontrolek można użyć narzędzi i menu skrótów. Na przykład umożliwia narzędzi kodowanego interfejsu użytkownika testu redaktora wykonaj następujące polecenia:  
  
 ![Interfejs użytkownika testu Edito](../test/media/uitesteditor.png "UITestEditor")  
  
1.  [Znajdź](../ide/finding-and-replacing-text.md) ułatwia wykrywanie, akcji interfejsu użytkownika i kontrolek.  
  
2.  [Usuń](#CodedUITestEditor_DeleteUIActions) usuwa niepożądanych akcji UI.  
  
3.  **Zmień nazwę** zmienia nazwy metody testowe i kontrolek.  
  
4.  **Właściwości** powoduje otwarcie okna właściwości dla wybranego elementu.  
  
5.  [Podziel do nowej metody](#CodedUITestEditor_SplitMethods) umożliwia modularyzacji akcji interfejsu użytkownika.  
  
6.  [Przenieś kod](#CodedUITestEditor_MoveMethods) dodaje niestandardowy kod do metody testu.  
  
7.  [Wstawianie opóźnienia przed](#CodedUITestEditor_InsertDelay) Dodaje pauzę przed akcją UI wyrażona w milisekundach.  
  
8.  [Zlokalizuj formant interfejsu użytkownika](#CodedUITestEditor_LocateUIControl) identyfikuje lokalizację kontroli w interfejsie użytkownika aplikacji w ramach testu.  
  
9. [Znajdź wszystkie](#CodedUITestEditor_LocateDecendants) sprawdzisz pomaga kontrolować właściwości i znaczących zmian do formantów w aplikacji.  
  
## <a name="how-do-i-do-this"></a>Jak to zrobić?  
 W [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], otwieranie pliku UIMap.uitest powiązane z kodowanego testu interfejsu użytkownika, w projekcie kodowanego testu interfejsu użytkownika zostanie automatycznie wyświetlona kodowanego testu interfejsu użytkownika w edytorze testu interfejsu użytkownika na stałe. W poniższych procedurach opisano, jak można zlokalizować i Edytuj metody i właściwości działania interfejsu użytkownika i kontrolek przy użyciu paska narzędzi edytora i menu skrótów.  
  
## <a name="open-a-coded-ui-test"></a>Otwórz kodowanego testu interfejsu użytkownika  
 Można wyświetlać i edytować programu Visual C# i opartych na języku Visual Basic kodowanego testu interfejsu użytkownika za pomocą edytora testu interfejsu użytkownika na stałe.  
  
 ![Menu kontekstowe edycji z interfejsu użytkownika Konstruktor kodowanego testu](../test/media/editcodeduitest.png "EditCodedUITest")  
  
 W Eksploratorze rozwiązań Otwórz menu skrótów **UIMap.uitest** i wybierz polecenie **Otwórz**. Kodowany test interfejsu użytkownika jest wyświetlany w Edytorze kodowanego testu interfejsu użytkownika. Można teraz wyświetlić i edytować zarejestrowane metody, działania i kontroli w kodowanego testu interfejsu użytkownika.  
  
> [!TIP]
>  Po wybraniu akcji interfejsu użytkownika, który znajduje się w metodzie w **akcji UI** okienku odpowiedniego formantu zostanie wyróżniona. Można również zmodyfikować właściwości formantów lub akcji interfejsu użytkownika.  
  
 *Nie widzę* edytora kodowanego testu interfejsu użytkownika.  
 Być może używasz wersji programu Visual Studio Enterprise przed 2012. Edytor kodowanego testu interfejsu użytkownika została ona również dostępna w programie Visual Studio 2010 funkcji dodatkiem Service Pack 2 z subskrypcją MSDN. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Microsoft Visual Studio 2010 funkcji dodatkiem Service Pack 2](http://go.microsoft.com/fwlink/?LinkID=204119).  
  
##  <a name="CodedUITestEditor_EditActionAndControlProperties"></a>Modyfikowanie właściwości akcji UI oraz ich odpowiednich właściwości formantu  
 Za pomocą edytora testu interfejsu użytkownika na stałe, możesz szybko znaleźć i wyświetlić wszystkich akcji interfejsu użytkownika na metody testu. Po wybraniu akcji interfejsu użytkownika w edytorze, automatycznie zostanie wyróżniona odpowiedniego formantu. Podobnie w przypadku wybrania formantu są wyróżnione skojarzonych z nimi działań interfejsu użytkownika. Po wybraniu akcji interfejsu użytkownika lub formantu, następnie jest łatwe w użyciu okna właściwości, aby zmodyfikować właściwości, które odpowiadają z nim.  
  
 ![Właściwości akcji UI](../test/media/codeduiedituiaction.png "CodedUIEditUIAction")  
Edycja właściwości akcji UI  
  
 Aby zmodyfikować właściwości akcji UI w **akcji IU** okienku rozwiń metody testowej, zawierający akcji interfejsu użytkownika, który chcesz edytować właściwości, wybierz akcji interfejsu użytkownika, a następnie zmodyfikuj właściwości, używając okna właściwości.  
  
 Na przykład, jeśli serwer jest niedostępny, i ma akcji interfejsu użytkownika skojarzonego z przeglądarki sieci Web które stany **przejdź do strony sieci Web "http://Contoso1/default.aspx"**, można zmienić adres URL, który `'http://Contoso2/default.aspx'`.  
  
 ![Właściwości formantu](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp")  
Edytowanie właściwości formantu  
  
 Modyfikowanie właściwości kontrolki odbywa się w taki sam sposób jak akcji interfejsu użytkownika. W **mapy formantów interfejsu użytkownika** okienku wybierz formant, który chcesz edytować i zmodyfikować jego właściwości, używając okna właściwości.  
  
 Na przykład deweloper może zmieniono **(ID)** właściwości formantu przycisku w kodzie źródłowym aplikacji testowane z "idSubmit" do "idLogin." Z **(ID)** właściwości została zmieniona w aplikacji, nie będzie można zlokalizować formantu przycisku kodowanego testu interfejsu użytkownika i zakończy się niepowodzeniem. W takim przypadku można otworzyć tester **właściwości wyszukiwania** kolekcji i zmień **identyfikator** właściwość, aby pasowała do nowej wartości używanego przez dewelopera w aplikacji. Tester można również zmienić **przyjazną nazwę** wartość właściwości z "Zatwierdź" do "Logowanie". Przez wprowadzenie tej zmiany, skojarzonej akcji interfejsu użytkownika w kodowanego interfejsu użytkownika edytora testu jest zaktualizowany z "Wybierz"Prześlij"button" do "Wybierz"Logowanie"przycisku."  
  
 Po zakończeniu modyfikacji, zapisać zmiany w pliku UIMap.Designer, wybierając **zapisać** na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paska narzędzi.  
  
 *Co należy wiedzieć?*  
 **Porady**  
  
-   ![Porada](../test/media/tip.png "Porada") , jeśli nie zostanie wyświetlone okno właściwości, naciśnij i przytrzymaj **Alt** podczas używania **Enter**, lub też nacisnąć klawisz **F4** .  
  
-   ![Porada](../test/media/tip.png "Porada") Aby wycofać wprowadzone zmiany właściwości, wybierz **Cofnij** z **Edytuj** menu lub naciśnij klawisze Ctrl + Z.  
  
-   ![Porada](../test/media/tip.png "Porada") można użyć **znaleźć** przycisk paska narzędzi edytora kodowanego testu interfejsu użytkownika, aby otworzyć narzędzie Znajdź i Zamień w programie Visual Studio. Następnie można kontroli Znajdź zlokalizować akcji interfejsu użytkownika w edytorze kodowanego testu interfejsu użytkownika. Na przykład możesz znaleźć "kliknij przycisk"Logowanie"." Może to być przydatne w testach dużych. Należy pamiętać, że nie można użyć funkcji Zamień narzędzia Znajdź i Zamień w kodowanego interfejsu użytkownika edytora testu. Aby uzyskać więcej informacji, zobacz Znajdź kontroli w [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).  
  
-   ![Porada](../test/media/tip.png "Porada") czasami może być trudne do wizualizacji, gdy formanty znajdują się w Interfejsie użytkownika aplikacji w ramach testu. Jest jedną z możliwości edytora kodowanego testu interfejsu użytkownika, można wybrać formant mapy formantów interfejsu użytkownika na liście i wyświetlić jej lokalizacji w testowanej aplikacji. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Lokalizowanie formantu interfejsu użytkownika w testowanej aplikacji](#CodedUITestEditor_LocateUIControl) znajduje się dalsze poniżej w tym temacie.  
  
-   ![Porada](../test/media/tip.png "Porada") może być konieczne rozwinąć formantu kontenera, który zawiera formant, który chcesz edytować. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Lokalizowanie formantu i jego elementy podrzędne](#CodedUITestEditor_LocateDecendants) znajduje się dalsze poniżej w tym temacie.  
  
##  <a name="CodedUITestEditor_DeleteUIActions"></a>Usuwanie niepożądanych akcji UI  
 Można łatwo usunąć niepożądanych akcji UI w kodowanego testu interfejsu użytkownika.  
  
 ![Usuń akcję interfejsu użytkownika](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")  
  
 W **akcji IU** okienku rozwiń metody testowej, zawierający akcji interfejsu użytkownika, który chcesz usunąć. Otwórz menu skrótów, akcji interfejsu użytkownika i wybierz polecenie **usunąć**.  
  
##  <a name="CodedUITestEditor_SplitMethods"></a>Dzielenie metody testu do dwóch oddzielnych metod  
 Można podzielić metody testowej uściślić lub modularyzacji akcji interfejsu użytkownika. Na przykład test może mieć metody pojedynczy test z działania interfejsu użytkownika w dwóch formantów kontenera. Działania interfejsu użytkownika można lepiej modularized w dwóch metod, które odpowiadają jeden kontener.  
  
 ![Metoda testowa Splt](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")  
  
 ![Dwie metody testów](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")  
  
 W **akcji IU** okienku rozwiń metody testowej, który chcesz podzielić na dwa oddzielne metod i wybierz akcję interfejsu użytkownika, w którym ma nowej metody testowej, aby rozpocząć. Albo otwórz menu skrótów, akcji interfejsu użytkownika, a następnie wybierz pozycję **Podziel do nowej metody**, lub wybierz **Podziel do nowej metody** przycisk na pasku narzędzi edytora testu interfejsu użytkownika na stałe. Nowa metoda testu zostanie wyświetlony w okienku akcji interfejsu użytkownika. Zawiera ona akcji interfejsu użytkownika, począwszy od akcji określoną podziału.  
  
 Po ukończeniu dzielenia metody, należy zapisać zmiany w pliku UIMap.Designer, wybierając **zapisać** na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paska narzędzi.  
  
 *Co należy wiedzieć?*  
 **Istotne problemy**  
  
-   ![Ikonę ostrzeżenia](../test/media/caution.gif "ostrożność") **Ostrzeżenie:** Jeśli dzielenie metody, należy zmodyfikować każdy kod wywołujący istniejącą metodę do wywołania również nowej metody, które zostały utworzone, jeśli chcesz nadal tych interfejsu użytkownika akcje uwzględnione. Podczas podziału metody zostanie wyświetlone okno dialogowe programu Microsoft Visual Studio. Go ostrzega, że należy zmodyfikować każdy kod wywołujący istniejącą metodę także wywołać nowej metody, które zostały utworzone. Wybierz **tak**.  
  
 **Porady**  
  
-   ![Porada](../test/media/tip.png "Porada") Aby cofnąć podziału, wybierz polecenie **Cofnij** z **Edytuj** menu lub naciśnij klawisze Ctrl + Z.  
  
-   ![Porada](../test/media/tip.png "Porada") można zmienić nazwę nowej metody. Wybierz go w okienku Akcje interfejsu użytkownika, a następnie wybierz pozycję **zmienić** przycisk paska narzędzi edytora testu interfejsu użytkownika na stałe.  
  
     —lub—  
  
     Otwórz menu skrótów, metoda testowa i wybierz nowy **zmienić**.  
  
     Pojawi się okno dialogowe programu Microsoft Visual Studio. Go ostrzega, że należy zmodyfikować każdy kod odwołujący się do metody. Wybierz **tak**.  
  
##  <a name="CodedUITestEditor_MoveMethods"></a>Przenieś do pliku UIMap w celu ułatwienia dostosowania metody testowej  
 Jeśli okaże się, że jedna z metody testu w Interfejsie użytkownika kodowanego testu wymaga kodu niestandardowego, przenieś go do pliku UIMap.cs albo UIMap.vb. W przeciwnym razie kodu zostaną zastąpione zawsze, gdy jest ponownie kompilowana kodowanego testu interfejsu użytkownika. Jeśli metoda nie są przenoszone niestandardowy kod zostanie zastąpiony zawsze, gdy test jest ponownie kompilowana.  
  
 W **akcji IU** okienku, wybierz metodę testu, który chcesz przenieść plik UIMap.cs lub UIMap.vb ułatwiające funkcji kodu niestandardowego, zostaną zastąpione, gdy kod testu jest ponownie kompilowana. Następnie wybierz **Przenieś kod** znajdującego się na pasku narzędzi edytora testu kodowanego interfejsu użytkownika lub Otwórz menu skrótów metody testowej i wybierz polecenie **Przenieś kod**. Metoda testu jest usuwana z pliku UIMap.uitest i nie jest już wyświetlana w okienku Akcje interfejsu użytkownika. Aby edytować plik testu przeniesiony, otwórz UIMap.cs lub plik UIMap.vb w Eksploratorze rozwiązań.  
  
 Po zakończeniu przenoszenia metody, należy zapisać zmiany w pliku UIMap.Designer, wybierając **zapisać** na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paska narzędzi.  
  
 *Co należy wiedzieć?*  
 **Istotne problemy**  
  
-   ![Ikonę ostrzeżenia](../test/media/caution.gif "ostrożność") **Ostrzeżenie:** po przesunięciu metody można już edytować za pomocą edytora kodowanego testu interfejsu użytkownika. Należy dodać niestandardowy kod i obsługiwać go za pomocą Edytora kodu. Po przeniesieniu metody zostanie wyświetlone okno dialogowe programu Microsoft Visual Studio. Go ostrzega, czy metoda zostanie przeniesiona z pliku UIMap.uitest do UIMap.cs lub UIMap.vb, który nie będzie możliwe edytowanie metody, za pomocą edytora kodowanego testu interfejsu użytkownika. Wybierz **tak**.  
  
 **Porady**  
  
-   ![Porada](../test/media/tip.png "Porada") Aby cofnąć przeniesienie, wybierz **Cofnij** z **Edytuj** menu lub naciśnij klawisze Ctrl + Z. Jednak należy następnie ręcznie usunąć kod z pliku UIMap.cs lub UIMap.vb.  
  
##  <a name="CodedUITestEditor_LocateUIControl"></a>Lokalizowanie formantu interfejsu użytkownika w testowanej aplikacji  
 Czasami może być trudne do wizualizacji, gdy formanty znajdują się w Interfejsie użytkownika aplikacji w ramach testu. Jest jedną z możliwości edytora kodowanego testu interfejsu użytkownika, można wybrać formant mapy formantów interfejsu użytkownika na liście i wyświetlić jej lokalizacji w testowanej aplikacji. Przy użyciu **zlokalizuj formant interfejsu użytkownika** funkcję w testowanej aplikacji można również sprawdzić wyszukiwania właściwości zmiany wprowadzone do formantu.  
  
 ![Zlokalizuj formant interfejsu użytkownika](../test/media/codeduilocatecontrol.png "CodedUILocateControl")  
  
 ![Formant znajduje się w testowanej aplikacji](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")  
  
 W **mapy formantów interfejsu użytkownika** okienku, wybierz kontrolkę, która ma zostać umieszczony w aplikacji skojarzonych z testu. Następnie otwórz menu skrótów dla formantu, a następnie wybierz pozycję **zlokalizuj formant interfejsu użytkownika**. W aplikacji, która jest poddawana testom niebieską linią jest wyznaczony formant.  
  
 *Co należy wiedzieć?*  
 **Istotne problemy**  
  
-   ![Ikonę ostrzeżenia](../test/media/caution.gif "ostrożność") **Ostrzeżenie:** przed zlokalizuj formant interfejsu użytkownika, sprawdź, czy jest uruchomiona aplikacja skojarzona z testu.  
  
 **Porady**  
  
-   ![Porada](../test/media/tip.png "Porada") Alternatywnie można użyć **zlokalizować wszystkie** opcję, aby sprawdzić, czy wszystkie formanty w kontenerze można poprawnie. Ta opcja jest opisany w następnej sekcji.  
  
##  <a name="CodedUITestEditor_LocateDecendants"></a>Lokalizowanie formantu i jego elementy podrzędne  
 Możesz sprawdzić, czy wszystkich kontrolek w kontenerze może poprawnie umieszczone w Interfejsie testowanej aplikacji. Może to być przydatne podczas weryfikowania zmiany właściwości wyszukiwania, które mogły zostać wprowadzone w kontenerze. Ponadto jeżeli dokonano znaczących zmian w Interfejsie użytkownika aplikacji w ramach testu, można sprawdzić czy istniejącej właściwości wyszukiwania są nadal prawidłowe.  
  
 ![Znajdź wszystkie formanty podrzędne](../test/media/codeduilocateall.png "CodedUILocateAll")  
  
 ![Wszystkie formanty, znajduje się](../test/media/codeduilocateall2.png "CodedUILocateAll2")  
  
 W **mapy formantów interfejsu użytkownika** okienku wybierz formantu kontenera, który ma zostać lokalizowanie i wyświetlanie wszystkich elementów podrzędnych dla. Następnie otwórz menu skrótów dla formantu i wybierz **zlokalizować wszystkie**. Formantu kontenera i wszystkich jego elementów podrzędnych kontrolki, są oznaczone w kodowanego interfejsu użytkownika edytora testu z zielonym znacznikiem wyboru lub czerwony symbol "X". Znaczniki informacją o tym, czy formanty pomyślnie znajdowały się w testowanej aplikacji.  
  
 *Co należy wiedzieć?*  
 **Istotne problemy**  
  
-   ![Ikonę ostrzeżenia](../test/media/caution.gif "ostrożność") **Ostrzeżenie:** przed lokalizowanie kontrolki interfejsu użytkownika, należy sprawdzić, czy aplikacja skojarzona z testu jest uruchomiony.  
  
##  <a name="CodedUITestEditor_InsertDelay"></a>Wstawianie opóźnienia przed akcją UI  
 Czasami możesz wykonać próbę poczekaj na niektóre zdarzenia, takie jak okna pojawiają się paska postępu zniknąć i tak dalej. Za pomocą edytora kodowanego testu interfejsu użytkownika, można to zrobić przez wstawianie opóźnienia przed akcją UI. Można można określić liczbę sekund opóźnienia się.  
  
 ![Wstawianie opóźnienia przed akcją UI](../test/media/codeduidelay.png "CodedUIDelay")  
  
 ![Dodaje się 5 sekund opóźnienia](../test/media/codeduidealy2.png "CodedUIDealy2")  
  
 W **akcji IU** okienku rozwiń zawierający akcji interfejsu użytkownika, który ma zostać Wstawianie opóźnienia przed metody testowej. Wybierz akcję interfejsu użytkownika. Następnie otwórz menu skrótów, akcji interfejsu użytkownika i wybierz **Wstawianie opóźnienia przed**. Opóźnienie jest wstawiony i wyróżnione przed wybranej akcji interfejsu użytkownika z następującym tekstem: **poczekaj 1 w sekundach dla opóźnienia użytkownika pomiędzy działaniami**. W oknie Właściwości zmień wartość atrybutu **opóźnienie** właściwości odpowiednią liczbę milisekund.  
  
 Po zakończeniu Wstawianie opóźnienia, zapisać zmiany w pliku UIMap.Designer, wybierając **zapisać** na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paska narzędzi.  
  
 *Co należy wiedzieć?*  
 **Uwagi**  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") Jeśli należy się upewnić, że określonego formantu jest dostępny przed akcją UI, należy rozważyć dodanie niestandardowy kod do metody testu przy użyciu odpowiednich UITestControl.WaitForControlXXX() Metoda. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Tworzenie kodowanego interfejsu użytkownika testów oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
 **Porady**  
  
-   ![Porada](../test/media/tip.png "Porada") Jeśli nie zostanie wyświetlone okno właściwości, naciśnij i przytrzymaj klawisz Alt, naciśnij klawisz Enter, lub też nacisnąć klawisz F4.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testy jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="faq"></a>Najczęściej zadawane pytania  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio automatyzacji testów UI (w tym CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Zobacz także

[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)  
[Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)  
[Tworzenie kodowanego testu interfejsu użytkownika opartego na danych](../test/creating-a-data-driven-coded-ui-test.md)  
[Przewodnik: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
