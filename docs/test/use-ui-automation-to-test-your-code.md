---
title: "Używanie automatyzacji interfejsu użytkownika do testowania kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: fafb9bc38aca51db6baf6cace6dc887db60ed8c8
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="use-ui-automation-to-test-your-code"></a>Używanie automatyzacji interfejsu użytkownika do testowania kodu

Testy automatyczne, którzy sterują aplikacji za pośrednictwem jej interfejsu użytkownika (UI) są określane jako *kodowanych testów interfejsu użytkownika* (CUITs). Te testy obejmują testowanie funkcjonalności kontrolek interfejsu użytkownika. Umożliwiają one Sprawdź, czy całej aplikacji, w tym interfejs użytkownika działa poprawnie. Kodowane testy interfejsu użytkownika są szczególnie użyteczne w przypadku weryfikacji lub innych logikę w interfejsie użytkownika, na przykład na stronie sieci web. Są one również często używane do automatyzowania istniejącego testu ręcznego.  

Jak pokazano na poniższej ilustracji, środowisko rozwoju typowe może być where, początkowo, wystarczy skompilować aplikację (F5) i kliknij przycisk za pomocą formantów interfejsu użytkownika, aby sprawdzić, czy elementy są poprawne. Następnie możesz utworzyć kodowanego testu, tak aby nie trzeba ręcznie przetestować aplikację w dalszym ciągu. W zależności od konkretnej funkcji testowane w aplikacji można napisać kod funkcjonalności testu lub test integracji, który może lub nie może zawierać testowania na poziomie interfejsu użytkownika. Jeśli po prostu chcesz uzyskać bezpośredni dostęp do niektórych logiki biznesowej, może być kod testu jednostkowego. Jednak w pewnych okolicznościach może być korzystne obejmują przetestowanie różnych kontrolek interfejsu użytkownika w aplikacji. Kodowanego testu interfejsu użytkownika można zautomatyzować początkowej scenariuszu (F5) zweryfikowaniu, że ten postęp dokonany w kodzie nie ma wpływu na funkcjonalność aplikacji.  

![Testowanie podczas tworzenia aplikacji](../test/media/cuit_overview.png "CUIT_Overview")  

Tworzenie kodowanego testu interfejsu użytkownika jest bardzo proste. Możesz po prostu wykonać test ręcznie podczas konstruktora testu CUIT działa w tle. Można również określić, jakie wartości powinny być wyświetlane w określonych pól. Konstruktor testu CUIT rejestruje czynności użytkownika i generuje kod z nich. Po utworzeniu testu można edytować go w edytorze specjalne, która umożliwia modyfikowanie sekwencję akcji.

Specjalne konstruktora testu CUIT i Edytor ułatwiają tworzenie i edytowanie kodowane testy interfejsu użytkownika, nawet jeśli swoje umiejętności głównego jest skoncentrowana testowania zamiast kodowania. Jednak jeśli jesteś deweloperem i chcesz rozszerzyć test w sposób bardziej zaawansowanych, struktura kodu tak, aby proste do skopiowania i dostosowania. Na przykład możesz zarejestrować test, aby kupić coś w witrynie sieci Web, a następnie edytuj wygenerowany kod w celu dodania pętli kupuje wiele elementów.  

**Wymagania**

- Visual Studio Enterprise

Aby uzyskać więcej informacji o platformach i konfiguracjach obsługiwanych przez kodowane testy interfejsu użytkownika, zobacz [obsługiwane konfiguracje oraz platformy kodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  

**W tym temacie**
  
-   [Tworzenie kodowanych testów interfejsu użytkownika](#VerifyingCodeUsingCUITCreate)  
  
    -   [Main-procedura](#VerifyingCodeUsingCUITCreate)  
  
    -   [Uruchamianie i zatrzymywanie aplikacji](#starting)  
  
    -   [Sprawdzanie poprawności właściwości formantów interfejsu użytkownika](#VerifyingCodeUsingCUITGenerateAssertions)  
  
-   [Dostosowywanie kodowanego testu interfejsu użytkownika](#VerifyingCodeCUITModify)  
  
    -   [Wygenerowany kod](#generatedCode)  
  
    -   [Kodowanie właściwości i akcje formantu interfejsu użytkownika](#actions)  
  
    -   [Debugowanie](#debugging)  
  
-   [Co to jest dalej](#VerifyCodeUsingCUITWhatsNext)  
  
##  <a name="VerifyingCodeUsingCUITCreate"></a>Tworzenie kodowanych testów interfejsu użytkownika  
  
1.  **Utwórz projekt kodowanego testu interfejsu użytkownika.**  
  
     Kodowane testy interfejsu użytkownika muszą być zawarte w projekcie kodowanego testu interfejsu użytkownika. Jeśli nie masz już projekt kodowanego testu interfejsu użytkownika, utwórz je. W **Eksploratora rozwiązań**, w menu skrótów rozwiązanie, wybierz **Dodaj**, **nowy projekt** , a następnie wybierz pozycję **Visual Basic** lub **Visual C#**. Następnie wybierz **testu**, **kodowanego testu interfejsu użytkownika**.  
  
    -   *Nie widzę **kodowanego testu interfejsu użytkownika** szablony projektu.*  
  
         Być może korzystasz wersji programu Visual Studio, która nie obsługuje kodowane testy interfejsu użytkownika. Aby utworzyć kodowane testy interfejsu użytkownika, należy użyć programu Visual Studio Enterprise.  
  
2.  **Dodaj plik kodowanego testu interfejsu użytkownika.**  
  
     Jeśli utworzony projekt kodowanego interfejsu użytkownika jest automatycznie dodawany pierwszy plik CUIT. Aby dodać inny plik test, otwórz menu skrótów na projekt kodowanego testu interfejsu użytkownika, wskaż pozycję **Dodaj**, a następnie wybierz pozycję **kodowanego testu interfejsu użytkownika**.  
  
     ![Tworzenie kodowanego testu interfejsu użytkownika](../test/media/codedui_create.png "CodedUI_Create")  
  
     W **Generuj kod dla kodowanego testu interfejsu użytkownika** oknie dialogowym wybierz **Rejestruj akcje, Edytuj mapę interfejsu użytkownika lub Dodaj asercje**.  
  
     ![Wybierz akcje rekordów](../test/media/codedui_codegendialogb.png "CodedUI_CodeGenDialogB")  
  
     Prawdopodobnie konstruktora kodowanego testu interfejsu użytkownika i programu Visual Studio jest zminimalizowany.  
  
     ![Kodowanego testu interfejsu użytkownika](../test/media/codedui_testbuilder.png "CodedUI_TestBuilder")  
  
3.  **Zarejestruj sekwencję akcji**.  
  
     **Aby rozpocząć nagrywanie**, wybierz **rekordu** ikony. Wykonywanie akcji, które mają zostać przetestowane w aplikacji, łącznie z uruchomieniem aplikacji, w razie potrzeby.  
  
     Na przykład w przypadku testowania aplikacji sieci web, użytkownik może Uruchom przeglądarkę, przejdź do witryny sieci web i zaloguj się do aplikacji.  
  
     **Aby Wstrzymaj rejestrowanie**, na przykład jeśli masz radzenia sobie z poczty przychodzącej, wybierz **wstrzymać**.  
  
    > [!WARNING]
    >  Wszystkie akcje wykonywane na pulpicie będą rejestrowane. Wstrzymanie nagrywania, wykonywania działań, które mogą prowadzić do włączenia rejestrowania danych poufnych.  
  
     **Aby usunąć akcje** zapisane przez pomyłkę, wybierz **edytować akcje**.  
  
     **Aby wygenerować kod** który będą replikowane czynności użytkownika, wybierz **Generuj kod** ikony, jak i typ metoda testowa nazwę i opis dla kodowanego interfejsu użytkownika.  
  
4.  **Sprawdź wartości w polach interfejsu użytkownika, np. pola tekstowe**.  
  
     Wybierz **dodawania potwierdzeń** w Konstruktorze kodowanego testu interfejsu użytkownika, a następnie wybierz formantu interfejsu użytkownika w uruchomionej aplikacji. Na liście właściwości zostanie wyświetlony, wybierz właściwość, na przykład **tekst** w polu tekstowym. W menu skrótów wybierz **Dodaj potwierdzenie**. W oknie dialogowym Wybierz operator porównania wartości porównania i komunikat o błędzie.  
  
     Zamknij okno potwierdzenia i wybierz **Generuj kod**.  
  
     ![Docelowy element kodowanego testu interfejsu użytkownika](../test/media/codedui_1.png "CodedUI_1")  
  
    > [!TIP]
    >  Przełącza między rejestrowanie akcji i sprawdzania poprawności wartości. Generowanie kodu na końcu każdej sekwencji działań lub weryfikacji. Jeśli chcesz, można później wstawiać nowe akcje i weryfikacji.  
  
     Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności właściwości kontrolki](#VerifyingCodeUsingCUITGenerateAssertions).  
  
5.  **Wyświetl kod wygenerowany test**.  
  
     Aby wyświetlić wygenerowany kod, zamknij okno konstruktora testu interfejsu użytkownika. W kodzie widać nazwy, które należy nadać do każdego kroku. Kod znajduje się w pliku CUIT, który został utworzony:  
  
    ```csharp  
    [CodedUITest]  
    public class CodedUITest1  
    { ...  
      [TestMethod]  
      public void CodedUITestMethod1()  
      {  
          this.UIMap.AddTwoNumbers();  
          this.UIMap.VerifyResultValue();  
          // To generate more code for this test, select   
          // "Generate Code" from the shortcut menu.  
      }  
    }  
    ```  
  
6.  **Dodaj więcej działań i potwierdzeń**.  
  
     Umieść kursor we właściwym momencie w metodzie testowej, a następnie w menu skrótów wybierz **Generuj kod dla kodowanego testu interfejsu użytkownika**. Nowy kod zostanie wstawiony do tego punktu.  
  
7.  **Edytuj szczegóły działań testów i potwierdzenia**.  
  
     Otwórz UIMap.uitest. Ten plik zostanie otwarty w kodowanego interfejsu użytkownika edytora testów, którym można edytować żadnych sekwencję akcji zapisanych oraz jak edytować potwierdzenia Twojej.  
  
     ![Kodowanego interfejsu użytkownika edytora testów](../test/media/cuit_editor_edit.png "CUIT_Editor_edit")  
  
     Aby uzyskać więcej informacji, zobacz [testów interfejsu użytkownika kodowany edycji za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
8.  **Uruchom test**.  
  
     Użyj Eksploratora testów, lub Otwórz menu skrótów w metodzie testowej, a następnie wybierz **Uruchom testy**. Aby uzyskać więcej informacji na temat uruchamiania testów, zobacz [uruchamiania testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md) i *dodatkowe opcje do uruchomienia kodowanych testów interfejsu użytkownika* w [kolejnych?](#VerifyCodeUsingCUITWhatsNext) sekcji w końcu tego tematu.  
  
 Pozostałe części tego tematu podać więcej szczegółów na temat kroków tej procedury.  
  
 Aby uzyskać bardziej szczegółowy przykład zobacz [wskazówki: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). W tym przewodnikiem utworzysz prostą aplikację systemu Windows Presentation Foundation (WPF) w celu zademonstrowania sposobu tworzenia, edytowania i obsługa kodowanego testu interfejsu użytkownika. Dostarcza on rozwiązania do korekcji testów, które zostały uszkodzone przez różne problemy związane z czasem i refaktoryzacją kontroli.
  
###  <a name="starting"></a>Uruchamianie i zatrzymywanie testowanej aplikacji  
 *Nie chcę uruchomić i zatrzymać mojej aplikacji, przeglądarki lub bazy danych osobno dla każdego z testów. Jak uniknąć, który?*  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") , jeśli nie chcesz zarejestrować akcje, aby uruchomić aplikację w ramach testu, należy uruchomić aplikację przed wybraniem **rekordu** ikony.  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym")na końcu testu zakończenia procesu, w której jest uruchamiana testu. Jeśli aplikacja jest uruchomiona w teście, zwykle powoduje zamknięcie aplikacji.  Jeśli nie chcesz, aby zamknąć aplikację po wydaniu testu, należy dodać pliku runsettings do rozwiązania i użyj `KeepExecutorAliveAfterLegacyRun` opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") można dodać metoda inicjowania testów, określone przez atrybut [TestInitialize], która uruchamia kod na początku każdej metody. Na przykład można uruchomić aplikacji z metody TestInitialize.  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") można dodać metoda czyszcząca testu, zidentyfikowane przez atrybut [TestCleanup], która uruchamia kod na końcu każdej metody. Na przykład metodę, aby zamknąć aplikację można można wywołać metody TestCleanup.  
  
###  <a name="VerifyingCodeUsingCUITGenerateAssertions"></a>Sprawdzanie poprawności właściwości formantów interfejsu użytkownika  
 Można użyć **konstruktora testu kodowanego interfejsu użytkownika** można dodać kontrolki interfejsu użytkownika do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> dla testu lub aby wygenerować kod dla metody weryfikacji, która używa potwierdzenia dla formantu interfejsu użytkownika.  
  
 Aby wygenerować potwierdzenia dla formantów interfejsu użytkownika, wybierz **dodawania potwierdzeń** narzędzia w konstruktora testu kodowanego interfejsu użytkownika i przeciągnij go do kontroli aplikacji w ramach testu, który chcesz zweryfikować jest poprawna. Gdy pole zawiera opis formantu, zwolnij przycisk myszy. Kod klasy formantu natychmiast jest tworzony w `UIMap.Designer.cs` pliku.  
  
 ![Docelowy element kodowanego testu interfejsu użytkownika](../test/media/codedui_1.png "CodedUI_1")  
  
 Właściwości dla tego formantu są wyświetlane w **dodawania potwierdzeń** okno dialogowe.  
  
 Innym sposobem nawigowania do określonego formantu jest wybierz strzałkę **(<<)** aby rozwinąć widok **mapy formantów interfejsu użytkownika**. Aby znaleźć nadrzędnego, element równorzędny lub formant podrzędny, możesz kliknij w dowolnym miejscu na mapie i użyj klawiszy strzałek do przenoszenia drzewa.  
  
 ![Właściwości testu kodowanego interfejsu użytkownika](../test/media/codedui_2.png "CodedUI_2")  
  
-   *Nie ma żadnych właściwości formantu I wybierz w mojej aplikacji lub nie widzę formantu w formancie mapy interfejsu użytkownika.*  
  
     W kodzie aplikacji formant, który chcesz zweryfikować musi mieć unikatowy identyfikator, takie jak atrybutu HTML Identyfikatora lub WPF UId. Może być konieczna aktualizacja kod aplikacji, aby dodać tych identyfikatorów.  
  
 Następnie otwórz menu skrótów we właściwości formantu interfejsu użytkownika, który chcesz sprawdzić, a następnie wskaż **Dodaj potwierdzenie**. W **Dodaj potwierdzenie** okno dialogowe, wybierz opcję **Komparatora** do potwierdzenia, na przykład <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>i wpisz wartość dla Twojego potwierdzenia w **wartości porównania**.  
  
 ![Potwierdzenia testu kodowanego interfejsu użytkownika](../test/media/codedui_3.png "CodedUI_3")  
  
 Gdy zostaną dodane wszystkie Twoje potwierdzenia dla testu, wybierz **OK**.  
  
 Aby wygenerować kod dla Twojego potwierdzenia i Dodaj formant do mapy interfejsu użytkownika, wybierz **Generuj kod** ikony. Wpisz nazwę metodę kodowanego testu interfejsu użytkownika i opis metody, która zostanie dodany jako komentarze w metodzie. Wybierz **Dodaj i generowanie**. Następnie wybierz **zamknąć** ikonę, aby zamknąć **konstruktora kodowanego testu interfejsu użytkownika**. Spowoduje to wygenerowanie kodu podobne do następującego kodu. Na przykład, jeśli wprowadzona nazwa jest `AssertForAddTwoNumbers`, kod będzie wyglądać następująco:  

-   Dodaje wywołanie do metody assert AssertForAddTwoNumbers do metody w pliku kodowanego testu interfejsu użytkownika:

    ```csharp
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        this.UIMap.AddTwoNumbers();  
        this.UIMap.AssertForAddTwoNumbers();  
    }  
    ```
  
     Możesz edytować ten plik, aby zmienić kolejność kroków i potwierdzeń lub utworzyć nowe metody testowe. Aby dodać więcej kodu, umieść kursor w metodzie testowej i w menu skrótów wybierz **Generuj kod dla kodowanego testu interfejsu użytkownika**.  
  
-   Dodaje metodę o nazwie `AssertForAddTwoNumbers` do mapy interfejsu użytkownika (UIMap.uitest). Ten plik zostanie otwarty w kodowanego interfejsu użytkownika edytora testów, którym można edytować potwierdzenia.  
  
     ![Edytuj assert za pomocą edytora testu interfejsu użytkownika na stałe](../test/media/cuit_editor_assert.png "CUIT_Editor_assert")  
  
     Aby uzyskać więcej informacji, zobacz [testów interfejsu użytkownika kodowany edycji za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
     Można również wyświetlić wygenerowany kod metody potwierdzenia w UIMap.Designer.cs. Jednak nie należy edytować ten plik. Aby dostosowaną wersją kodu kopiowanie metod do innego pliku, takie jak UIMap.cs, Zmień nazwę metody i tam je edytować.  
  
    ```csharp
    public void AssertForAddTwoNumbers()  
    {  
        ...  
    }  
    ```  
  
 *Formant, który Zaznaczanie traci fokus i znika przy próbie wybierz narzędzie dodawania potwierdzeń z konstruktora kodowanego testu interfejsu użytkownika. Jak wybrać formant?*  
 **Wybieranie ukrytą kontrolkę za pomocą klawiatury**  
  
 Czasami, gdy [dodawanie formantów i weryfikacji ich właściwości](#VerifyingCodeUsingCUITGenerateAssertions), może być konieczne użycie klawiatury. Na przykład podczas rejestrowania kodowanego testu interfejsu użytkownika, która używa kontrolki menu kontekstowego na liście elementów menu w formancie utracić fokus i znikają w przypadku próby wybierz narzędzie dodawania potwierdzeń z konstruktora kodowanego interfejsu użytkownika testu. Zostało to przedstawione na poniższej ilustracji, gdy menu kontekstowego w programie Internet Explorer będzie tracić fokus i znikają próba zaznacz go za pomocą narzędzia dodawania potwierdzeń.  
  
 ![CodedUITest &#95; SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")  
  
 Używanie klawiatury, aby wybrać formant interfejsu użytkownika, umieść kursor nad formantem przy użyciu myszy. Wciśnij klawisz **Ctrl** klucza i **I** klucza w tym samym czasie. Zwolnij kluczy. Kontrolka jest rejestrowane przez konstruktora kodowanego testu UT.  
  
> [!WARNING]
>  Jeśli używasz programu Microsoft Lync, należy zamknąć Lync przed uruchomieniem Konstruktora kodowanego testu interfejsu użytkownika. Microsoft Lync zakłóca **Ctrl + I** skrót klawiaturowy.  
  
 *Nie można zarejestrować przesuwania myszy na kontrolce. Czy istnieje rozwiązanie tego problemu?*  
 **Ręczne rejestrowanie przesuwania wskaźnika myszy**  
  
 W pewnych okolicznościach określonego formantu, który jest używany w kodowanego interfejsu użytkownika testu może wymagać użycia klawiatury do zdarzeń przesuwania myszy ręcznie rekordów. Na przykład podczas testowania formularza systemu Windows lub aplikacji Windows Presentation Foundation (WPF), może być kodu niestandardowego. Lub może być specjalnego zachowania zdefiniowane dla kursora myszy nad formantem, takich jak rozszerzanie, gdy użytkownik znajduje się nad jego węzła drzewa. Aby przetestować okoliczności, takich jak te, należy ręcznie powiadomienia Konstruktor kodowanego interfejsu użytkownika testu który kursora myszy nad formantem naciskając wstępnie zdefiniowane klawisze.  
  
 Podczas wykonywania kodowanego testu interfejsu użytkownika, umieść kursor nad formantem. Naciśnij i przytrzymaj klawisz Ctrl, naciśnij i przytrzymaj klawisze Shift i R na klawiaturze. Zwolnij kluczy. Zdarzenie przesuwania myszy jest rejestrowane przez konstruktora kodowanego testu UT.  
  
 ![CodedUI &#95; Umieść kursor](../test/media/codedui_hover.png "CodedUI_Hover")  
  
 Po wygenerowaniu metody testowej kod podobny do poniższego przykładu zostaną dodane do pliku UIMap.Desinger.cs:  
  
```csharp  
// Mouse hover '1' label at (87, 9)  
Mouse.Hover(uIItem1Text, new Point(87, 9));  
  
```  
  
 *Przypisanie klucza dla przechwytywania zdarzeń przesuwania myszy jest używany w innym miejscu w mojej środowiska. Czy można zmienić przypisanie klucza domyślny?*  
 **Konfigurowanie przypisania klawiatury przesuwania myszy**  
  
 W razie potrzeby przypisanie klawiatury domyślne Ctrl + Shift + R, który służy do stosowania aktywowania zdarzenia myszy w kodowanych testów interfejsu użytkownika można skonfigurować do używania różnych kluczy.  
  
> [!WARNING]
>  Nie powinna mieć zmienić przypisania klawiatury dla zdarzenia przesuwania myszy w normalnych okolicznościach. Ponowne przypisywanie przypisania klawiatury, należy zachować ostrożność. Wybór mogą być już używany w innym miejscu w Visual Studio lub testowana aplikacja.  
  
 Aby zmienić przypisania klawiatury, należy zmodyfikować następującego pliku konfiguracji:  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 W pliku konfiguracji, zmień wartości `HoverKeyModifier` i `HoverKey` klucze do modyfikowania przydziałów klawiatury:  
  
```
<!-- Begin : Background Recorder Settings -->  
<!-- HoverKey to use. -->  
<add key="HoverKeyModifier" value="Control, Shift"/>  
<add key="HoverKey" value="R"/>  
```
  
 *Mam problemy z rejestrowanie ruchów myszy w witrynie sieci Web. Istnieje już poprawka w tym celu za?*  
 **Ustawienie niejawne przesuwania wskaźnika myszy przeglądarki sieci web**  
  
 W wielu witryn sieci Web po umieszczeniu na określonego formantu rozszerza aby pokazać dodatkowe szczegóły. Ogólnie rzecz biorąc te wyglądać menu w aplikacjach komputerowych. Kodowane testy interfejsu użytkownika, ponieważ jest to wspólnego wzorca, Włącz niejawne ruchów do przeglądania sieci Web. Na przykład jeśli rekord użytkownik znajduje się w programie Internet Explorer, zdarzenie jest wywoływane. Te zdarzenia może prowadzić do nadmiarowego ruchów pobierania rejestrowane. W związku z tym ruchów niejawne są rejestrowane z `ContinueOnError` ustawioną `true` w pliku konfiguracji testu interfejsu użytkownika. Dzięki temu odtwarzania kontynuować, jeśli zdarzenie aktywacji nie powiedzie się.  
  
 Aby włączyć rejestrowanie ruchów niejawne w przeglądarce sieci Web, otwórz plik konfiguracji:  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 Sprawdź, czy plik konfiguracji, ma klucz `RecordImplicitiHovers` ustawioną na wartość `true` jak pokazano w poniższym przykładzie:  
  
```  
<!--Use this to enable/disable recording of implicit hovers.-->  
<add key="RecordImplicitHover" value="true"/>  
  
```  
  
##  <a name="VerifyingCodeCUITModify"></a>Dostosowywanie kodowanego testu interfejsu użytkownika  
 Po utworzeniu kodowanego testu interfejsu użytkownika można edytować go za pomocą dowolnej z następujących narzędzi w programie Visual Studio:  
  
-   **Kodowany konstruktora testu interfejsu użytkownika:** Użyj konstruktora kodowanego testu interfejsu użytkownika można dodać dodatkowe funkcje kontroli i walidacji do testów. Zobacz sekcję [dodawanie formantów i weryfikacji ich właściwości](#VerifyingCodeUsingCUITGenerateAssertions) w tym temacie.  
  
-   **Kodowany interfejs użytkownika edytora testów:** edytora kodowanego testu interfejsu użytkownika umożliwia łatwe modyfikowanie kodowanych testów interfejsu użytkownika. Za pomocą edytora testu interfejsu użytkownika na stałe, można znaleźć, Wyświetl i Edytuj metody testu. Można również edytować działania interfejsu użytkownika i ich skojarzonych formantów w formancie mapy interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [testów interfejsu użytkownika kodowany edycji za pomocą edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
-   **Edytor kodu:**  
  
    -   Ręcznie Dodaj kod dla formantów w teście sieci, zgodnie z opisem w [akcji kontrolki UI kodowania i właściwości](#VerifyingCodeCUITActionsandProperties) w tym temacie.  
  
    -   Po utworzeniu kodowanego testu interfejsu użytkownika, należy ją zmodyfikować, aby być oparte na danych. Aby uzyskać więcej informacji, zobacz [tworzenie Data-driven kodowanego testu interfejsu użytkownika](../test/creating-a-data-driven-coded-ui-test.md).  
  
    -   Podczas odtwarzania testu kodowanego interfejsu użytkownika można nakazać testu czekać na niektóre zdarzenia, takie jak okna pojawia się paska postępu zniknąć i tak dalej. Aby to zrobić, należy dodać odpowiednią metodę UITestControl.WaitForControlXXX(). Aby uzyskać pełną listę dostępnych metod, zobacz [tworzenie kodowanego interfejsu użytkownika testy oczekiwania dla określonych zdarzeń podczas odtwarzania](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Na przykład kodowanego testu interfejsu użytkownika, który oczekuje na formantu można włączyć za pomocą metody WaitForControlEnabled zobacz [wskazówki: tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
    -   Kodowane testy interfejsu użytkownika obejmuje obsługę, niektóre z formantów HTML5, które są dołączone do programu Internet Explorer 9 i programu Internet Explorer 10. Aby uzyskać więcej informacji, zobacz [za pomocą formantów HTML5 w kodowanych testów interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md).  
  
    -   **Kodowanie wskazówki kodowanego testu interfejsu użytkownika:**  
  
        -   [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)  
  
        -   [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)  
  
        -   [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)  
  
        -   [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)  
  
###  <a name="generatedCode"></a>Wygenerowany kod  
 Po wybraniu **Generuj kod**, tworzonych jest kilka fragmentów kodu:  
  
-   **Wiersz w metodzie testowej.**  
  
    ```csharp  
    [CodedUITest]  
    public class CodedUITest1  
    { ...  
      [TestMethod]  
      public void CodedUITestMethod1()  
      {  
          this.UIMap.AddTwoNumbers();  
          // To generate more code for this test, select   
          // "Generate Code" from the shortcut menu.      }  
    }  
    ```  
  
     Możesz kliknąć prawym przyciskiem myszy w ramach tej metody, aby dodać więcej zarejestrowane akcje i weryfikacji. Można również edytować je ręcznie, aby rozszerzyć lub zmodyfikować kod. Na przykład można części kodu ująć w pętli.  
  
     Można również dodać nowych metod testu i Dodaj kod, aby je w taki sam sposób. Każda metoda testu musi mieć `[TestMethod]` atrybutu.  
  
-   **Metody w UIMap.uitest**  
  
     Ta metoda obejmuje szczegółów zarejestrowane akcje lub wartości, którą można zweryfikować. Ten kod można edytować, otwierając UIMap.uitest. Zostanie otwarty w edytorze specjalne można usunąć lub zrefaktoryzuj zarejestrowane akcje.  
  
     Youcan również wyświetlić metodę wygenerowanego w UIMap.Designer.cs. Ta metoda wykonuje akcje rejestrowane po uruchomieniu testu.  
  
    ```csharp  
    // File: UIMap.Designer.cs  
    public partial class UIMap  
    {  
      /// <summary>  
      /// Add two numbers  
      /// </summary>  
      public void AddTwoNumbers()  
      { ...   }  
    }  
    ```  
  
    > [!WARNING]
    >  Nie należy edytować ten plik, ponieważ zostaną wygenerowane, podczas tworzenia większej liczby testów.  
  
     Możesz wprowadzić dostosowane wersji tych metod, kopiując je do UIMap.cs. Na przykład można wprowadzić sparametryzowane wersji, który można wywołać z metody testowej:  
  
    ```csharp  
    // File: UIMap.cs  
    public partial class UIMap // Same partial class  
    {  
      /// <summary>  
      /// Add two numbers - parameterized version  
      /// </summary>  
      public void AddTwoNumbers(int firstNumber, int secondNumber)  
      { ...   // Code modified to use parameters.  
      }  
    }  
    ```  
  
-   **Deklaracje w UIMap.uitest**  
  
     Deklaracje te stanowią kontrolek interfejsu użytkownika aplikacji, które są używane przez test. Są one używane przez wygenerowanego kodu do obsługi formantów i ich właściwości.  
  
     Umożliwia także je Jeśli napisać własny kod. Na przykład można mieć metodę testu wybierz hiperłącze w aplikacji sieci Web, wpisz wartość w polu tekstowym, lub gałęzie i wykonać różne operacje testowych na podstawie wartości w polu.  
  
     Można dodać wiele kodowane testy interfejsu użytkownika i wiele obiektów mapy interfejsu użytkownika i pliki, aby ułatwić testowanie dużej aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
 Aby uzyskać więcej informacji na temat wygenerowany kod, zobacz [anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md).  
  
###  <a name="actions"></a>Kodowanie właściwości i akcje formantu interfejsu użytkownika  
 Podczas pracy z formantami testu interfejsu użytkownika w kodowanych testów interfejsu użytkownika, są one podzielone na dwie części: właściwości i akcje.  
  
-   Pierwsza część składa się z akcjami, które można wykonywać na formanty testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika można symulować kliknięcia w formancie testu interfejsu użytkownika lub symulować klucze wpisany na klawiaturze wpływa na formantu testu interfejsu użytkownika.  
  
-   Druga część obejmuje umożliwia pobieranie i ustawianie właściwości formantu testu interfejsu użytkownika. Na przykład kodowane testy interfejsu użytkownika można pobrać liczbę elementów w `ListBox`, lub ustaw `CheckBox` do wybranego stanu.  
  
 **Uzyskiwanie dostępu do akcji formantu testu interfejsu użytkownika**  
  
 Do wykonania akcji w formantach testu interfejsu użytkownika, takie jak kliknięcie myszą lub akcje klawiatury, użyj metody w <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> i <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> klasy:  
  
-   Aby wykonać akcję zorientowane na myszy, np. Kliknij przycisk myszy w formancie testu interfejsu użytkownika należy użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.  
  
     `Mouse.Click(buttonCancel);`  
  
-   Do wykonania akcji zorientowane na klawiaturze, takich jak pisać w formancie edycyjnym użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.  
  
     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`  
  
 **Uzyskiwanie dostępu do właściwości formantu testu interfejsu użytkownika**  
  
 Pobieranie i ustawianie wartości właściwości określonego formantu interfejsu użytkownika, możesz bezpośrednio pobrać lub ustawić wartości właściwości formantu, lub można użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> metod o tej nazwie konkretnej właściwości, które chcesz pobrać lub ustawić.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>Zwraca obiekt, który następnie mogą być rzutowane na odpowiednie <xref:System.Type>. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>akceptuje obiekt do wartości właściwości.  
  
##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Można pobrać lub ustawić właściwości bezpośrednio z kontrolek testu interfejsu użytkownika  
  
-   Z formantami, które pochodzą z T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl, takie jak T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList lub T: Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox, należy pobrać lub ustawić wartości właściwości bezpośrednio w następujący sposób:  
  
    ```csharp
    int i = myHtmlList.ItemCount;  
    myWinCheckBox.Checked = true;  
    ```  
  
##### <a name="to-get-properties-from-ui-test-controls"></a>Aby uzyskać właściwości z kontrolek testu interfejsu użytkownika  
  
-   Aby uzyskać wartość właściwości z formantu, należy użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.  
  
-   Aby określić właściwości formantu, aby pobrać, użyj na odpowiedni ciąg z `PropertyNames` klasy w każdej kontrolki jako parametr do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>zwraca odpowiedni typ danych, ale zwraca wartość jest rzutowany jako <xref:System.Object>. Zwracany <xref:System.Object> następnie musi być rzutowane jako odpowiedniego typu.  
  
     Przykład:  
  
     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`  
  
##### <a name="to-set-properties-for-ui-test-controls"></a>Aby ustawić właściwości formantów testu interfejsu użytkownika  
  
-   Aby ustawić właściwości formantu, użyj <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.  
  
-   Aby określić właściwości formantu można ustawić, użyj na odpowiedni ciąg z `PropertyNames` klasę jako pierwszy parametr <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, o wartości właściwości jako drugiego parametru.  
  
     Przykład:  
  
     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`  
  
###  <a name="debugging"></a>Debugowanie  
 Można analizować kodowanych testów interfejsu użytkownika za pomocą kodowanych dzienników testu interfejsu użytkownika. Zakodowanych filtru dzienników testu interfejsu użytkownika i rekord, który uruchamia ważne informacje o kodowanego testu interfejsu użytkownika. Format dzienniki pozwala szybko debugowanie problemów. Aby uzyskać więcej informacji, zobacz [analizowanie kodowanych testów przy użyciu kodowanego interfejsu użytkownika dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
##  <a name="VerifyCodeUsingCUITWhatsNext"></a>Co to jest dalej?  
 **Dodatkowe opcje do uruchomienia kodowanych testów interfejsu użytkownika:** kodowane testy interfejsu użytkownika można uruchomić bezpośrednio z programu Visual Studio, zgodnie z opisem we wcześniejszej części tego tematu. Ponadto można uruchomić zautomatyzowanych testów interfejsu użytkownika z [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], lub z [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]. Kodowane testy interfejsu użytkownika są automatyzowane, mają wchodzić w interakcje z pulpitem, po uruchomieniu, w przeciwieństwie do innych testów automatycznych.  
  
-   [Porady: Uruchamianie testów za pomocą programu Microsoft Visual Studio](http://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)  
  
-   [Uruchamianie testów w programie Microsoft Test Manager automatycznych](http://msdn.microsoft.com/en-us/0632f265-63fe-4859-a413-9bb934c66835)  
  
-   [Porady: Konfigurowanie i uruchomienie zaplanowanych testów po skompilowaniu aplikacji](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)  
  
-   [Uruchom testy w procesie kompilacji](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)
  
-   [Porady: Konfigurowanie agenta testowego do uruchamiania testów w interakcji z pulpitem](http://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)
  
 **Dodawanie obsługi w przypadku kontrolek niestandardowych:** framework testowanie kodowanego interfejsu użytkownika nie obsługuje co możliwy interfejs użytkownika i może nie obsługiwać interfejsu użytkownika ma zostać przetestowana. Na przykład nie można od razu utworzyć interfejsu użytkownika dla kodowanego testu interfejsu użytkownika [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]. Można jednak utworzyć rozszerzenie kodowanego interfejsu użytkownika framework testowania, obsługujące kontrolkę niestandardową.  
  
-   [Włączanie testowania kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md)  
  
-   [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)  
  
 Kodowane testy interfejsu użytkownika są często używane w celu zautomatyzowania testów ręcznych. Aby uzyskać dodatkowe wskazówki, zobacz [testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196). Aby uzyskać więcej informacji o testach ręcznych, zobacz [uruchomić testy ręczne z Microsoft Test Manager](/vsts/manual-test/mtm/run-manual-tests-with-microsoft-test-manager). Aby uzyskać więcej informacji o automatycznych testów systemowych, zobacz [tworzenie zautomatyzowanych testów przy użyciu programu Microsoft Test Manager](http://msdn.microsoft.com/en-us/7b5075ee-ddfe-411d-b1d4-94283550a5d0).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testy jednostkowe: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>Najczęściej zadawane pytania  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio automatyzacji testów UI (w tym CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Podnoszenie jakości kodu](../test/improve-code-quality.md)   
 [Wskazówki: Tworzenie, edytowanie i obsługa kodowanego testu interfejsu użytkownika](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Anatomia kodowanego testu interfejsu użytkownika](../test/anatomy-of-a-coded-ui-test.md)   
 [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)   
 [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Edycja zakodowanych testów interfejsu użytkownika za pomocą edytora testu kodowanego interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Uaktualnianie kodowanych testów interfejsu użytkownika programu Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
