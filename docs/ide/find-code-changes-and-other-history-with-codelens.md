---
title: "Znajdowanie zmian w kodzie i innych elementów historii za pomocą funkcji CodeLens | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b454893c2d68b23d130d6ff38be493d988dfb1fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens

Pozostać koncentruje się na pracę podczas znaleźć co się stało z twoim kodzie — bez opuszczania edytora. Znajdowanie odwołań i zmiany kodu, połączone usterki, elementów roboczych, przeglądy kodu i testów jednostkowych.

> [!NOTE]
> CodeLens jest dostępna tylko w wersjach programu Visual Studio Enterprise i Visual Studio Professional. Nie jest dostępny w Visual Studio Community edition.  

Zobacz, jak i gdzie poszczególnych części kodu są używane w rozwiązaniu:  

![Wskaźniki CodeLens w edytorze kodu](../ide/media/codelensoverview.png "CodeLensOverview")  

Bez opuszczania edytora, skontaktuj się z zespołem o zmianach w kodzie:  

![CodeLens &#45; Skontaktuj się z zespołem](../ide/media/codelensovervew2.png "CodeLensOvervew2")  

Aby wybrać wskaźników, które chcesz wyświetlić lub wyłącz i Włącz CodeLens, przejdź do **narzędzia**, **opcje**, **Edytor tekstu**, **wszystkie języki** , **CodeLens**.  

## <a name="FindReferences"></a>Znajdź odwołania do kodu

Potrzebne są:

-  Visual Studio Enterprise lub Professional programu Visual Studio

-  Kodu języka Visual C# .NET i Visual Basic .NET

Wybierz **odwołania** wskaźnika (**Alt + 2**). Jeśli widzisz **odwołania 0**, możesz nie mają odwołań z kodu Visual C# lub Visual Basic. To nie zawiera odwołania do innych elementów, takich jak pliki XAML i ASPX.

![CodeLens &#45; Wybierz odwołania do wskaźnika](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  

Aby wyświetlić kod odwołujący się, przenieś wskaźnik myszy na górze odwołania.  

![CodeLens &#45; Podgląd odwołanie](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  

Aby otworzyć plik zawierający odwołanie, kliknij dwukrotnie odwołanie.  

Aby wyświetlić relacje między ten kod i ich odwołań [utworzenie mapy kodu](../modeling/map-dependencies-across-your-solutions.md) i wybierz polecenie **Pokaż wszystkie odwołania** w menu skrótów mapy kodu.

![CodeLens &#45; Odwołania na mapie kodu](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  

## <a name="FindCodeHistory"></a>Znajdź swój kod historii i połączone elementy

Przejrzyj historię swój kod, aby dowiedzieć się, co się stało z kodu. Lub przejrzyj zmiany przed są scalane w kodzie aby lepiej zrozumieć, jak zmiany w inne gałęzie mogą wpłynąć na kodzie.

Potrzebne są:

- Visual Studio Enterprise lub Professional programu Visual Studio

- Team Foundation Server 2013 lub nowszy, Visual Studio Team Services lub Git

- [Lync 2010 lub nowszej lub Skype dla firm](http://technet.microsoft.com/en-us/lync), skontaktuj się z zespołem w edytorze kodu  

Kod Visual C# .NET i Visual Basic .NET, który jest przechowywany z kontroli wersji Team Foundation (TFVC) lub Git, otrzymasz CodeLens szczegóły na poziomie klasy i metody (*poziomie element kodu* wskaźniki). Jeśli repozytorium Git znajduje się w TfGit, możesz również uzyskać linki do elementów roboczych TFS.  

![Element kodu &#45; wskaźniki poziomu](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  

Dla wszystkich innych typów plików, które można otworzyć w edytorze programu Visual Studio, możesz uzyskać szczegółowe informacje wskaźników CodeLens cały plik w jednym miejscu w dolnej części okna (*poziomu plików* wskaźniki).

![Plik &#45; poziomu wskaźniki CodeLens](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  

Aby wybrać wskaźników za pomocą klawiatury, naciśnij i przytrzymaj **ALT** klawisz, aby wyświetlić powiązane klawiszy numerycznych.  

![Naciśnij klawisz ALT, aby wyświetlić numery dostępu do klawiatury](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  

### <a name="find-changes-in-your-code"></a>Znajdowanie zmian w kodzie

Znajdź który zmieniono C# lub kod Visual Basic, a wprowadzone zmiany ich, wskaźników na poziomie elementu kodu. Jest to, zobacz używania kontroli wersji Team Foundation (TFVC) w programie Team Foundation Server i Visual Studio Team Services.  

![CodeLens: Get historię zmian przez kod w TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  

Domyślny okres czasu jest ostatnich 12 miesięcy. Jeśli kod jest przechowywany na serwerze Team Foundation Server, można to zmienić, uruchamiając [polecenia TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62) z [CodeIndex — polecenie](../ide/codeindex-command.md) i **/indexHistoryPeriod** flagi.  

Aby wyświetlić szczegółowej historii wszystkie zmiany, w tym z więcej niż rok temu, wybierz pozycję **Pokaż wszystkie zmiany w pliku**.  

![Pokaż wszystkie zmiany kodu](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  

Spowoduje to otwarcie okna historii dla grupy zmian.  

![Okno historii dla wszystkich zmian w kodzie](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  

Jeśli pliki znajdują się w repozytorium Git i wybierz wskaźnika zmiany na poziomie elementu kodu, to zostanie wyświetlony.  

![CodeLens: Get historię zmian przez kod w usłudze Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  

Znajdowanie zmian dla całego pliku (z wyjątkiem plików języka C# i Visual Basic) w wskaźniki poziomu plików w dolnej części okna.  

![CodeLens: Pobierz kod szczegółów pliku](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  

Aby uzyskać więcej informacji o zmianie, kliknij prawym przyciskiem myszy tego elementu. W zależności od tego, czy używasz programu TFVC lub Git otrzymasz szereg opcji Porównaj wersje pliku, wyświetlić szczegóły i śledzenia zmian, Pobierz wybranej wersji pliku i poczty e-mail autora tej zmiany. Niektóre z tych szczegółów pojawiają się w programie Team Explorer.  

Można również sprawdzić, kto zmienił kodu w czasie. Może to ułatwić można znaleźć wzorce zmiany Twojego zespołu i oceny ich wpływu.  

![CodeLens: Zobacz kod zmienia historii jako wykres](../ide/media/codelens.png "CodeLens")  

#### <a name="find-changes-in-your-current-branch"></a>Znajdowanie zmian w bieżącej gałęzi

Załóżmy, że zespół ma kilka gałęzi — gałęzi głównej i rozwoju podrzędne — Aby zmniejszyć ryzyko złamanie stabilna kodu:  

![CodeLens: Znajdź po kodzie został rozgałęzionych](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  

Ile osób zmienić swój kod i liczbę zmian (**Alt + 6**) w gałęzi głównej:  

![CodeLens: Znajdź liczbę zmian w gałęzi](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  

#### <a name="find-when-your-code-was-branched"></a>Znajdź, gdy został rozgałęzionych kodu

Przejdź do kodu w gałęzi podrzędnej, na przykład, w gałęzi deweloperów. Wybierz wskaźnik zmian (**Alt + 6**):  

![CodeLens: Znajdź po kodzie został rozgałęzionych](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  

#### <a name="find-incoming-changes-from-other-branches"></a>Znajdowanie zmian przychodzące z innych działów

![CodeLens: Znajdowanie zmian w kodzie w inne gałęzie](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  

.. .tak jak ta poprawka usterki w deweloperów gałęzi w tym miejscu:

![CodeLens: Zmiana wyewidencjonowany do innego oddziału](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  

Ta zmiana można przejrzeć bez opuszczania bieżącej gałęzi (głównego):  

![CodeLens: Zobacz przychodzące zmian z gałęzi innej](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  

#### <a name="find-when-changes-got-merged"></a>Znajdź w przypadku zmiany otrzymano scalania

Pozwala zobaczyć, jakie zmiany znajdują się w gałęzi:  

![CodeLens &#45; Scalić zmiany między gałęziami](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  

Kod w gałęzi Main ma teraz Poprawka usterki w gałęzi Dev:  

![CodeLens &#45; Scalone chagnes między gałęziami](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Porównanie przychodzące zmiany z lokalną wersję (Shift + F10)

![CodeLens: Porównanie przychodzące zmiany z lokalnych](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  

Możesz również kliknąć dwukrotnie zestaw zmian.

#### <a name="what-do-the-icons-mean"></a>Co oznaczają ikony

|**Ikona**|**Zmiana skąd?**|  
|--------------|-----------------------------------------|  
|![CodeLens: Zmienić z bieżącej gałęzi ikona](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Bieżąca gałąź|  
|![CodeLens &#45; Zmień z ikony gałęzi nadrzędnej](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Gałęzi nadrzędnej|  
|![CodeLens: Zmień z ikony gałęzi podrzędnej](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Gałęzi podrzędnej|  
|![CodeLens &#45; Zmień z elementu równorzędnego gałęzi ikona](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Gałąź elementów równorzędnych|  
|![CodeLens &#45; Zmień z zadań ikony dalsze gałęzi](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Gałąź dalszej optymalizacji niż nadrzędny, podrzędny lub równorzędny|  
|![CodeLens: Scalanie z nadrzędnego ikony](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Scalanie z gałęzi do gałęzi podrzędnej|
|![CodeLens: Scalanie z ikony gałęzi podrzędnej](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Scalanie z gałęzi podrzędnej do gałęzi nadrzędnej|  
|![CodeLens: Scal od gałęzi niepowiązanych ikona](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Scalanie z niepowiązanych gałęzi (scalanie)|  

### <a name="find-linked-work-items"></a>Znajdowanie połączonych elementów roboczych

![CodeLens &#45; Wyszukiwanie elementów pracy dla określonego kodu](../ide/media/codelensworkitems.png "CodeLensWorkItems")  

### <a name="find-linked-code-reviews"></a>Znajdź przeglądy kodu połączonego

![CodeLens &#45; Wyświetl żądania przeglądu kodu](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  

### <a name="find-linked-bugs"></a>Znajdź połączonego usterki

![CodeLens &#45; Znajdź usterki połączone z grupy zmian](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  

### <a name="contact-the-owner-of-an-item"></a>Skontaktuj się z właścicielem elementu

![Skontaktuj się z właścicielem elementu](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  

Otwórz menu skrótów dla elementu, aby wyświetlić opcje kontaktu. Jeśli masz Lync lub Skype dla firm zainstalowane widzisz tych opcji:  

![Opcje kontaktu dla elementu](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  

##  <a name="FindRunUnitTests"></a>Znajdź testy jednostek dla kodu

Dowiedz się więcej o testy jednostek, które istnieją dla kodu bez konieczności otwierania Eksploratora testów. Potrzebne są:  

-   Visual Studio Enterprise lub Professional programu Visual Studio  
  
-   Kodu języka Visual C# .NET i Visual Basic .NET  
  
-   A [jednostkowy projekt testowy](../test/unit-test-your-code.md) mający testy jednostek dla kodu aplikacji  
  
1.  Przejdź do kodu aplikacji, który ma testy jednostkowe.  
  
2.  Przejrzyj testów dla tego kodu (**Alt + 3**).  
  
     ![CodeLens &#45; Wybierz stan testu w edytorze kodu](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3.  Jeśli widzisz ikonę ostrzeżenia ![CodeLens &#45; Testy jednostkowe nie został jeszcze uruchomiony ostrzeżenie](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), uruchom testy.  
  
     ![CodeLens &#45; Wyświetl testy jednostkowe nie jest jeszcze uruchomione](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4.  Aby przejrzeć definicji testu, kliknij dwukrotnie element testu w oknie wskaźników CodeLens można otworzyć pliku kodu w edytorze.  
  
     ![CodeLens &#45; Przejdź do definicji testów jednostkowych](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5.  Przejrzyj wyniki testu. Wybierz wskaźnik stanu testu (![CodeLens &#45; Testu jednostkowego nie powiodło się ikona](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") lub ![CodeLens &#45; Ikona przekazany testu jednostkowego](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")), lub naciśnij klawisz **Alt + 1**.  
  
     ![CodeLens &#45; Zobacz wyniku testu jednostkowego](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6.  Aby sprawdzić, ile osób zmienić ten test, który zmienić ten test lub liczbę zmian do tego testu [Znajdź swój kod historii i połączone elementy](#FindCodeHistory).

##  <a name="QA"></a>FUNKCJA PYTANIA I ODPOWIEDZI

###  <a name="ChangeOrTurnOff"></a>Pytanie: jak włączanie lub wyłączanie funkcji CodeLens? Lub wybierz które wskaźników, aby zobaczyć?

**Odpowiedź:** można włączyć wskaźniki lub wyłączyć, z wyjątkiem odwołania do wskaźnika. Przejdź do **narzędzia**, **opcje**, **Edytor tekstu**, **wszystkie języki**, **CodeLens**.  
  
 Kiedy wskaźniki są włączone, można również otworzyć Opcje CodeLens z wskaźników.  
  
 ![CodeLens &#45; Włączanie i wyłączanie wskaźniki](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Wskaźniki poziomu plików CodeLens należy włączyć i wyłączyć przy użyciu cudzysłów ostrokątny ikony w dolnej części okna edytora.  
  
 ![Włącz plik &#45; wskaźniki poziomu włączać i wyłączać](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
###  <a name="NoIndicators"></a>Pytanie: gdzie znajduje się CodeLens?

**Odpowiedź:** CodeLens pojawia się w kodzie Visual C# .NET i Visual Basic .NET na poziomie metody, klasy, indeksatora i właściwości. CodeLens pojawia się na poziomie plików dla wszystkich typów plików.

- Upewnij się, że jest włączona CodeLens. Przejdź do **narzędzia**, **opcje**, **Edytor tekstu**, **wszystkie języki**, **CodeLens**.  
  
- Jeśli kod jest przechowywany w programie TFS, upewnij się, że kod indeksowania jest włączona przy użyciu [CodeIndex — polecenie](../ide/codeindex-command.md) z [polecenia konfiguracyjnego TFS](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).  

- Wskaźniki związane z TFS pojawiają się tylko wtedy, gdy elementy robocze są połączone z kodem, a użytkownik ma uprawnienia do otwierania połączonych elementów roboczych. [Upewnij się, że masz uprawnienia zabezpieczeń elementów członkowskich zespołu.](http://msdn.microsoft.com/en-us/f58805de-ba61-4d09-8f2d-d3ab9662ecfd)  

- Wskaźniki testów jednostkowych nie są wyświetlane, gdy kod aplikacji nie ma testów jednostkowych. Wskaźniki stanu testu są automatycznie wyświetlane w projektach testów. Jeśli wiesz, że kod aplikacji testów jednostkowych, jednak nie są wyświetlane wskaźniki testu, spróbuj skompilować rozwiązanie (**Ctrl + Shift + B**).  

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Pytanie: Dlaczego nie widzę szczegóły elementu pracy zatwierdzania?

**Odpowiedź:** taka sytuacja może wystąpić, ponieważ wskaźników CodeLens nie można odnaleźć elementów roboczych w programie TFS. Sprawdź, czy masz połączenie z projektem zespołowym, który ma te elementów roboczych i czy masz uprawnienia, aby wyświetlić te elementy robocze. Może to również nastąpić, jeśli opis zatwierdzania zawiera nieprawidłowe informacje o identyfikatorów elementu roboczego w programie TFS.  

###  <a name="NoLync"></a>Pytanie: Dlaczego nie widzę wskaźniki Lync lub Skype

**Odpowiedź:** nie są one wyświetlane, jeśli użytkownik nie jest zarejestrowany w Lync lub Skype dla firm, nie ma jeden z nich zainstalowane lub nie ma obsługiwanej konfiguracji. Jednak nadal może wysyłać poczty:  

![CodeLens &#45; Właściciel grupy zmian kontaktu za pomocą poczty e-mail](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  

 **Które Lync i Skype konfiguracje są obsługiwane?**

-   Skype dla firm (32-bitowy lub 64-bitowe)  

-   Lync 2010 lub nowszej wyłącznie (32-bitowy lub 64-bitowy), ale Lync 2013 Basic z Windows 8.1  

Zainstalowany Skype lub wskaźników CodeLens nie obsługuje korzystanie z różnych wersji programu Lync. Nie mogą one być zlokalizowane wszystkie zlokalizowane wersje programu Visual Studio.  

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Pytanie: jak zmienić czcionek i kolorów dla CodeLens?

**Odpowiedź:** przejdź do **narzędzia**, **opcje**, **środowiska**, **czcionki i kolory**.  

![CodeLens &#45; Zmień ustawienia czcionek i kolorów](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  

Aby użyć klawiatury:

1.  Naciśnij klawisz **Alt T + O** otworzyć **opcje** pole.  

2.  Naciśnij klawisz **Strzałka w górę** lub **Strzałka w dół** można przejść do **środowiska** węzła, naciśnij klawisz **Strzałka w lewo** Aby rozwinąć węzeł.  

3.  Naciśnij klawisz **Strzałka w dół** można przejść do **czcionki i kolory**.  

4.  Naciśnij klawisz **kartę** można przejść do **Pokaż ustawienia dla** listy, a następnie naciśnij klawisz **Strzałka w dół** wybierz **CodeLens**.  

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Pyt.: Czy można przesunąć ekran projekcyjny CodeLens?

**Odpowiedź:** tak, wybierz ![CodeLens &#45; Dokowanie jako okno](../ide/media/codelensdockwindow.png "CodeLensDockWindow") do dock CodeLens jako okno.  

![Dokowanie okna wskaźników CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  

![Zadokowane okna odwołania do wskaźników CodeLens](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  

### <a name="q-how-do-i-refresh-the-indicators"></a>Pyt.: Jak odświeżyć wskaźniki?

**Odpowiedź:** zależy to od wskaźnika:  

-   **Odwołania**: wskaźnik ten aktualizowany automatycznie po zmianie kodu. Jeśli ten wskaźnik zadokowane jako osobne okno, Odśwież wskaźnika ręcznie w tym miejscu:  

     ![CodeLens &#45; Dock jako okno](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  

-   **Zespół**: Odśwież wskaźniki ręcznie w tym miejscu:  

     ![CodeLens &#45; Odśwież wskaźniki](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  

-   **Test**: [znaleźć testy jednostek dla kodu](#FindRunUnitTests) odświeżyć ten wskaźnik.  

###  <a name="LocalVersion"></a>Pytanie: co to jest "Wersja lokalna"?

**Odpowiedź:** **lokalnej wersji** Strzałka najbardziej aktualnych zmian w lokalnej wersji tego pliku. Jeśli serwer ma nowszą grupy zmian, pojawią się one powyżej lub poniżej **lokalnej wersji** strzałka, w zależności od kolejności sortowania grupy zmian.  

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Pytanie: czy można zarządzać w jaki sposób CodeLens przetwarza kod, aby wyświetlić historię i połączone elementy?

**Odpowiedź:** tak, jeśli kod jest w programie TFS, użyj [CodeIndex — polecenie](../ide/codeindex-command.md) z [polecenia konfiguracyjnego TFS](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).

## <a name="see-also"></a>Zobacz także

[Pisanie kodu w edytorze](../ide/writing-code-in-the-code-and-text-editor.md)