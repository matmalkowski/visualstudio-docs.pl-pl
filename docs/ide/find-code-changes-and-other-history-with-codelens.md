---
title: Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21724619a0dd3b89582c716a5df0fdff6041b682
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens

CodeLens temu otrzymasz koncentruje się na pracę podczas znaleźć co się stało z kodu&ndash;bez opuszczania edytora. Można znaleźć odniesienia do fragment kodu, zmiany kodu, połączone usterki, elementów roboczych, przeglądy kodu i testów jednostkowych.

> [!NOTE]
> CodeLens jest dostępna tylko w wersjach programu Visual Studio Enterprise i Visual Studio Professional. Nie jest dostępny w Visual Studio Community edition.

Zobacz, jak i gdzie poszczególnych części kodu są używane w rozwiązaniu:

![Wskaźniki CodeLens w edytorze kodu](../ide/media/codelens-overview.png)

Bez opuszczania edytora, skontaktuj się z zespołem o zmianach w kodzie:

![CodeLens - skontaktuj się z zespołem](../ide/media/codelens-contact-info.png)

Aby wybrać wskaźników, które chcesz wyświetlić lub wyłącz i Włącz CodeLens, przejdź do **narzędzia** > **opcje** > **Edytor tekstu**  >  **Wszystkie języki** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Znajdź odwołania do kodu

Odwołania można znaleźć w C# lub kod Visual Basic.

1. Wybierz **odwołania** wskaźnika lub naciśnij przycisk **Alt**+**2**.

   ![Odwołania do wskaźników CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Jeśli wyświetlany jest wskaźnik **odwołania 0**, możesz nie mają odwołań z kodu C# lub Visual Basic. Jednak może zawierać odwołania do innych elementów takich jak *.xaml* i *.aspx* plików.

2. Aby wyświetlić kod odwołujący się myszą odwołania na liście.

   ![CodeLens — odwołanie do podglądu](../ide/media/codelens-peek-reference.png)

3. Aby otworzyć plik, który zawiera odwołanie, kliknij dwukrotnie odwołanie.

### <a name="code-maps"></a>Mapy kodu

Aby wyświetlić relacje między kodem i ich odwołań [utworzenie mapy kodu](../modeling/map-dependencies-across-your-solutions.md). Wybierz z menu skrótów mapy kodu **Pokaż wszystkie odwołania**.

![CodeLens - odwołania na mapie kodu](../ide/media/codelensmappedreferences.png)

## <a name="a-namefind-code-historyfind-changes-in-your-code"></a><a name="find-code-history"/>Znajdowanie zmian w kodzie

Sprawdź historię swój kod, aby dowiedzieć się, co się stało z kodu. Lub przejrzyj zmiany przed są scalane w kodzie aby lepiej zrozumieć, jak zmiany w inne gałęzie mogą wpłynąć na kodzie.

Potrzebujesz:

- Visual Studio Enterprise lub Professional programu Visual Studio

- Team Foundation Server 2013 or later, Visual Studio Team Services, or Git

- [Skype dla firm](/skypeforbusiness/), lub Lync 2010 lub nowszej, aby skontaktować się z zespołem w edytorze kodu

Kod C# lub Visual Basic, który jest przechowywany z kontroli wersji typu Team Foundation (TFVC) lub Git, otrzymasz CodeLens szczegóły na poziomie klasy i metody (*element kodu na poziomie* wskaźniki). Jeśli repozytorium Git znajduje się w TfGit, możesz również uzyskać linki do elementów roboczych TFS.

![Wskaźniki poziomu element Code](../ide/media/codelens-element-level-indicators.png)

Dla pliku typów innych niż *.cs* lub *.vb*, możesz uzyskać szczegółowe informacje wskaźników CodeLens cały plik w jednym miejscu w dolnej części okna (*poziomu plików* wskaźniki).

![Wskaźniki poziomu plików CodeLens](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Wskaźniki poziomu element Code

Wskaźniki poziomu elementu pozwalają zobaczyć, kto zmienił kodu i jakie zmiany kodu one. Wskaźniki poziomu elementu kodu są dostępne dla kodu C# i Visual Basic.

Jest to, zobacz korzystając z Team Foundation wersji formantu (TFVC) w programie Team Foundation Server i Visual Studio Team Services:

![CodeLens: Historia zmian Get dla kodu w TFVC](../ide/media/codelens-code-changes.png)

Domyślny okres czasu jest ostatnich 12 miesięcy. Jeśli kod jest przechowywany na serwerze Team Foundation Server, można zmienić okres czasu, uruchamiając [polecenia TFSConfig](/vsts/tfs-server/command-line/tfsconfig-cmd) z [CodeIndex — polecenie](../ide/codeindex-command.md) i **/indexHistoryPeriod**flagi.

Aby wyświetlić szczegółowej historii wszystkie zmiany, w tym z więcej niż rok temu, wybierz pozycję **Pokaż wszystkie zmiany w pliku**:

![Pokaż wszystkie zmiany kodu](../ide/media/codelens-show-all-file-changes.png)

**Historii** zostanie otwarte okno:

![Okno historii wszystkich zmian kodu](../ide/media/codelenscodechangeshistory.png)

Jeśli pliki znajdują się w repozytorium Git i wybierz wskaźnika zmiany dotyczące elementu kodu, to zostanie wyświetlony:

![CodeLens: Historia zmian Get dla kodu w usłudze Git](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Wskaźniki poziomu plików

Znajdowanie zmian dla całego pliku wskaźniki poziomu plików w dolnej części okna:

![CodeLens: Pobierz kod szczegółów pliku](../ide/media/codelens-file-level.png)

> [!NOTE]
> Wskaźniki poziomu plików nie są dostępne dla plików C# i Visual Basic.

Aby uzyskać więcej informacji o zmianie, kliknij prawym przyciskiem myszy tego elementu. W zależności od tego, czy używasz programu TFVC lub Git dostępne są opcje Porównaj wersje pliku, wyświetlić szczegóły i śledzenia zmian pobrać wybranej wersji pliku i poczty e-mail autora tej zmiany. Niektóre z tych szczegółów pojawiają się w **Team Explorer**.

Można również sprawdzić, kto zmienił kodu w czasie. Może to ułatwić można znaleźć wzorce zmiany Twojego zespołu i oceny ich wpływu.

![CodeLens: Zobacz historię zmian kodu jako wykresu.](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Znajdowanie zmian w bieżącej gałęzi

Zespół może mieć kilka gałęzi, na przykład gałęzi głównej i rozwoju gałęzi podrzędnej, aby zmniejszyć ryzyko złamanie stabilna kodu.

![CodeLens: Znajdź kiedy został rozgałęzionych kodu](../ide/media/codelensfirstbranchconceptual.png)

Można ustalić, ile osób zmienić swój kod i liczby zmian w gałęzi głównej naciskając **Alt**+**6**:

![CodeLens: Znajdź liczby zmian w gałęzi](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Znajdź, gdy został rozgałęzionych kodu

Aby dowiedzieć się, gdy kod został rozgałęzionych, przejdź do kodu w gałęzi podrzędnej. Następnie wybierz opcję **zmiany** wskaźnika lub naciśnij przycisk**Alt**+**6**:

![CodeLens: Znajdź kiedy został rozgałęzionych kodu](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Znajdowanie zmian przychodzące z innych działów

![CodeLens: Znajdź inne gałęzie zmiany kodu](../ide/media/codelensbranchchangecheckinconceptual.png)

Przychodzące zmiany można wyświetlić. Na poniższym zrzucie ekranu poprawkę została wprowadzona w gałęzi "Dev":

![CodeLens: Zmień wyewidencjonowany do innego oddziału](../ide/media/codelens-branch-changes-dev.png)

Zmiany można przejrzeć bez opuszczania bieżącej gałęzi ("Main"):

![CodeLens: Zobacz przychodzące zmiana z innej gałęzi.](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Znajdź w przypadku zmiany otrzymano scalania

Możesz sprawdzić, gdy otrzymano scalić zmiany, dzięki czemu można określić, które zmiany zostały uwzględnione w gałęzi:

![CodeLens — zmiany scalone między gałęzi](../ide/media/codelensbranchmergedconceptual.png)

Kod w gałęzi Main ma teraz Poprawka usterki w gałęzi "Dev":

![CodeLens — zmiany scalone między gałęzi](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Porównanie przychodzące zmiany z lokalną wersję

Porównanie przychodzące zmiany z lokalną wersję, naciskając klawisz **Shift**+**F10**, lub klikając dwukrotnie zestaw zmian.

![CodeLens: Porównanie przychodzące zmiany lokalnie](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Ikony gałęzi

Ikona w **gałęzi** kolumny informuje, jak jest związane z gałęzi do pracy w gałęzi.

|**Ikona**|**Zmiana pochodzi od:**|
|--------------|-----------------------------------------|
|![CodeLens: Zmiana z bieżącej gałęzi ikona](../ide/media/codelensbranchcurrenticon.png)|Bieżąca gałąź|
|![CodeLens: Zmiana z ikoną gałęzi nadrzędnej](../ide/media/codelensbranchparenticon.png)|Gałęzi nadrzędnej|
|![CodeLens: Zmiana z ikoną gałęzi podrzędnej](../ide/media/codelensbranchchildicon.png)|Gałęzi podrzędnej|
|![CodeLens: Zmiana z elementu równorzędnego gałęzi ikona](../ide/media/codelensbranchpeericon.png)|Gałąź elementów równorzędnych|
|![CodeLens: Zmiana z zadań ikona dalsze gałęzi](../ide/media/codelensbranchfurtherawayicon.png)|Gałąź dalszej optymalizacji niż nadrzędny, podrzędny lub równorzędny|
|![CodeLens: Scalanie z nadrzędnego ikony](../ide/media/codelensbranchmergefromparenticon.png)|Scalanie z gałęzi do gałęzi podrzędnej|
|![CodeLens: Scalanie z ikony gałęzi podrzędnej](../ide/media/codelensbranchmergefromchildicon.png)|Scalanie z gałęzi podrzędnej do gałęzi nadrzędnej|
|![CodeLens: Scal od gałęzi niepowiązanych ikony](../ide/media/codelensbranchmergefromunrelatedicon.png)|Scalanie z niepowiązanych gałęzi (scalanie)|

## <a name="linked-work-items"></a>Połączone elementy robocze

Znajdowanie połączonych elementów roboczych, wybierając **elementy robocze** wskaźnika lub naciskając klawisz **Alt**+**8**.

![CodeLens — Znajdź elementów roboczych dla określonego kodu](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Przeglądy kodu połączonego

Znajdowanie przeglądy kodu połączone przez wybranie **przegląda** wskaźnika. Używanie klawiatury, przytrzymaj **Alt** klucza, a następnie naciśnij klawisz **strzałki w lewo** lub **strzałki w prawo** można przejść, Opcje wskaźnika.

![CodeLens — widok kodu Przeglądanie żądań](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Połączone usterki

Znajdowanie połączonego usterki przez wybranie **usterki** wskaźnika lub naciskając klawisz **Alt**+**7**.

![CodeLens — Znajdź usterki połączone z grupy zmian](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Skontaktuj się z właścicielem elementu

Znajdowanie autor elementu przez wybranie **autorów** wskaźnika lub naciskając klawisz **Alt**+**5**.

![Skontaktuj się z właścicielem elementu](../ide/media/codelens-contact-item-owner.png)

Otwórz menu skrótów dla elementu, aby wyświetlić opcje kontaktu. Jeśli masz Lync lub Skype dla firm zainstalowane widzisz tych opcji:

![Opcje kontaktu dla elementu](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Testów jednostkowych skojarzone

Może odnajdywać testy jednostek, które istnieją dla kodu C# lub Visual Basic bez otwierania **Eksploratora testów**.

1. Przejdź do kodu aplikacji, który został skojarzony [kod testu jednostkowego](../test/unit-test-your-code.md).

2. Przejrzyj testów dla kodu, naciskając klawisz **Alt**+**3**.

     ![Wybierz CodeLens — stan testu w edytorze kodu](../ide/media/codelens-choose-test-indicator.png)

3. Jeśli widzisz ikonę ostrzeżenia ![Ikona ostrzeżenia](../ide/media/codelenstestwarningicon.png), testy nie Uruchom jeszcze, więc ich uruchamiać.

     ![CodeLens — widok testów jednostkowych nie jeszcze uruchomione](../ide/media/codelens-tests-not-yet-run.png)

4. Aby przejrzeć definicji testu, kliknij dwukrotnie element testu w oknie wskaźników CodeLens można otworzyć pliku kodu w edytorze.

     ![CodeLens - przejdź do definicji testów jednostkowych](../ide/media/codelens-unit-test-definition.png)

5. Aby przejrzeć wyniki testu, wybierz pozycję wskaźnika stanu testu (![nie powiodło się ikona testowa](../ide/media/codelenstestfailedicon.png) lub ![ikona pomyślny](../ide/media/codelenstestpassedicon.png)), lub naciśnij klawisz **Alt**+**1**.

     ![CodeLens - wyniku testu jednostkowego zobacz](../ide/media/codelens-unit-test-result.png)

6. Aby sprawdzić, ile osób zmienić ten test, który zmienić ten test lub liczbę zmian do tego testu [Znajdź swój kod historii](#find-code-history) i połączone elementy.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Aby wybrać wskaźników za pomocą klawiatury, naciśnij i przytrzymaj **Alt** klucza do wyświetlenia powiązanych klawiszy numerycznych, a następnie naciśnij klawisz liczba, która odpowiada wskaźnika, która ma zostać wybrana.

![Numery dostępu klawiatury](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Aby wybrać **przegląda** wskaźnik, naciśnij i przytrzymaj klawisz **Alt** podczas używania klawiszy strzałek w lewo i prawo do nawigacji.

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>Pytanie: jak włączanie i wyłączanie funkcji CodeLens, lub wybierz które wskaźników, aby zobaczyć?

**Odpowiedź:** można włączyć wskaźniki lub wyłączyć, z wyjątkiem odwołania do wskaźnika. Przejdź do **narzędzia** > **opcje** > **Edytor tekstu** > **wszystkie języki**  >  **CodeLens**.

Kiedy wskaźniki są włączone, można również otworzyć Opcje CodeLens z wskaźników.

![CodeLens - wskaźniki Włączanie lub wyłączanie](../ide/media/codelensturnoffonindicatorsfromcode.png)

Wskaźniki poziomu plików CodeLens należy włączyć i wyłączyć przy użyciu cudzysłów ostrokątny ikony w dolnej części okna edytora.

![Włączanie wskaźniki poziomu plików i wyłączanie](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>Pytanie: gdzie znajduje się CodeLens?

**Odpowiedź:** CodeLens pojawia się w kodzie C# i Visual Basic na poziomie metody, klasy, indeksatora i właściwości. CodeLens pojawia się na poziomie plików dla wszystkich typów plików.

- Upewnij się, że jest włączona CodeLens. Przejdź do **narzędzia** > **opcje** > **Edytor tekstu** > **wszystkie języki**  >  **CodeLens**.

- Jeśli kod jest przechowywany w programie TFS, upewnij się, że kod indeksowania jest włączona przy użyciu [CodeIndex — polecenie](../ide/codeindex-command.md) z [polecenia konfiguracyjnego TFS](/vsts/tfs-server/command-line/tfsconfig-cmd).

- Wskaźniki związane z TFS pojawiają się tylko wtedy, gdy elementy robocze są połączone z kodem, a użytkownik ma uprawnienia do otwierania połączonych elementów roboczych. Upewnij się, że masz [uprawnienia zabezpieczeń elementów członkowskich zespołu](/vsts/work/scale/multiple-teams).

- Wskaźniki testów jednostkowych nie są wyświetlane, gdy kod aplikacji nie ma testów jednostkowych. Wskaźniki stanu testu są automatycznie wyświetlane w projektach testów. Jeśli wiesz, że kod aplikacji testów jednostkowych, jednak nie są wyświetlane wskaźniki testu, spróbuj skompilować rozwiązanie (**Ctrl**+**Shift**+**B**).

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Pytanie: Dlaczego nie widzę szczegóły elementu pracy zatwierdzania?

**Odpowiedź:** taka sytuacja może wystąpić, ponieważ wskaźników CodeLens nie można odnaleźć elementów roboczych w programie TFS. Sprawdź, czy masz połączenie z projektem zespołowym, który ma te elementów roboczych, i czy masz uprawnienia, aby wyświetlić te elementy robocze. Szczegóły elementu roboczego może również nie są wyświetlane Jeśli opis zatwierdzania zawiera nieprawidłowe informacje o identyfikatorów elementu roboczego w programie TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>Pytanie: Dlaczego nie widzę wskaźniki Skype

**Odpowiedź:** nie są wyświetlane wskaźniki Skype, jeśli użytkownik nie jest zalogowany do usługi Skype dla firm, nie jest zainstalowany lub nie ma obsługiwanej konfiguracji. Jednakże nadal może wysyłać wiadomości e-mail:

![CodeLens - skontaktuj się z właścicielem grupy zmian za pomocą poczty e-mail](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Które Skype i Lync konfiguracje są obsługiwane?**

- Skype dla firm (32-bitowy lub 64-bitowe)

- Lync 2010 lub nowszej wyłącznie (32-bitowy lub 64-bitowy), ale Lync 2013 Basic z Windows 8.1

Zainstalowany Skype lub wskaźników CodeLens nie obsługuje korzystanie z różnych wersji programu Lync. Nie mogą one być zlokalizowane wszystkie zlokalizowane wersje programu Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Pytanie: jak zmienić czcionek i kolorów dla CodeLens?

**Odpowiedź:** przejdź do **narzędzia** > **opcje** > **środowiska** > **czcionki i kolory**.

![CodeLens — Zmień ustawienia czcionek i kolorów](../ide/media/codelensoptionsfontscolorssettings.png)

Aby użyć klawiatury:

1. Naciśnij klawisz **Alt**+**T**+**O** otworzyć **opcje** okno dialogowe.

2. Naciśnij klawisz **Strzałka w górę** lub **Strzałka w dół** można przejść do **środowiska** węzła, naciśnij klawisz **Strzałka w lewo** Aby rozwinąć węzeł.

3. Naciśnij klawisz **Strzałka w dół** można przejść do **czcionki i kolory**.

4. Naciśnij klawisz **kartę** można przejść do **Pokaż ustawienia dla** listy, a następnie naciśnij klawisz **Strzałka w dół** wybierz **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Pyt.: Czy można przesunąć ekran projekcyjny CodeLens?

**A:** tak, wybierz ![ikona dokowania](../ide/media/codelensdockwindow.png) do dock CodeLens jako okno.

![Dock — przycisk w oknie wskaźników CodeLens](../ide/media/codelensselectdockwindow.png)

![Zadokowanych okien odwołania do wskaźników CodeLens](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>Pyt.: Jak odświeżyć wskaźniki?

**Odpowiedź:** zależy to od wskaźnika:

- **Odwołania**: wskaźnik ten aktualizowany automatycznie po zmianie kodu. Jeśli **odwołania** wskaźnika jest zadokowany jako osobne okno, Odśwież wskaźnika, wybierając **Odśwież**:

     ![Odśwież w odwołaniach CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Zespół**: Odśwież wskaźniki wybierając **Odśwież wskaźniki zespołu CodeLens** w menu kontekstowym:

     ![Odśwież wskaźniki zespołu CodeLens elementu menu](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: [znaleźć testy jednostek dla kodu](#Find-unit-tests-for-your-code) odświeżyć **testu** wskaźnika.

### <a name="q-whats-local-version"></a>Pytanie: co to jest "Wersja lokalna"?

**Odpowiedź:** **lokalnej wersji** Strzałka najbardziej aktualnych zmian w lokalnej wersji pliku. Jeśli serwer ma nowszą grupy zmian, pojawią się one powyżej lub poniżej **lokalnej wersji** strzałka, w zależności od kolejności sortowania grupy zmian.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Pytanie: czy można zarządzać w jaki sposób CodeLens przetwarza kod, aby wyświetlić historię i połączone elementy?

**Odpowiedź:** tak. Jeśli kod jest w programie TFS, użyj [CodeIndex — polecenie](../ide/codeindex-command.md) z [polecenia konfiguracyjnego TFS](/vsts/tfs-server/command-line/tfsconfig-cmd).

## <a name="see-also"></a>Zobacz także

- [Pisanie kodu w edytorze](../ide/writing-code-in-the-code-and-text-editor.md)