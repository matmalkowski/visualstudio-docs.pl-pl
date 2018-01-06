---
title: "Wskazówki: Tworzenie podstawowego izolowane powłoki aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e798eb66601d253c180a72b730bb3531e21c11c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Wskazówki: Tworzenie aplikacji podstawowe Isolated Shell
W tym przewodniku pokazano, jak tworzyć rozwiązania programu isolated shell, dostosowywanie okna narzędzia pomocy i utworzyć program instalacyjny, który instaluje programu isolated shell.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../visual-studio-sdk.md). Aby wdrożyć programu isolated shell, należy również użyć pakiet redystrybucyjny programu Visual Studio Shell (izolowany).  
  
## <a name="creating-an-isolated-shell-solution"></a>Tworzenie rozwiązania Isolated Shell  
 W tej sekcji pokazano, jak użyć szablonu projektu programu Visual Studio Shell izolowanego tworzenie rozwiązań programu isolated shell. To rozwiązanie nie zawiera następujących projektów:  
  
-   *Nazwa rozwiązania*. Projekt AboutBoxPackage umożliwia dostosowanie wyglądu Pomoc/informacje pole.  
  
-   Projekt ShellExtensionsVSIX, który zawiera plik Source.Extension.vsixmanifest,a, który definiuje różne składniki aplikacji isolated shell.  
  
-   *Nazwa rozwiązania* projektu, który tworzy plik wykonywalny, który wywołuje aplikacji isolated shell. Ten projekt zawiera folder dostosowywania powłoki, który umożliwia dostsowywanie wygląd i zachowanie aplikacji isolated shell.  
  
-   *Nazwa rozwiązania* projektu interfejsu użytkownika, który tworzy zestaw satelicki definiujący aktywne menu poleceń i ciągi lokalizowalny.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Tworzenie rozwiązań podstawowe programu isolated shell  
  
1.  Otwórz program Visual Studio i utworzyć nowy projekt.  
  
2.  W **nowy projekt** okna, rozwiń węzeł **inne typy projektów** , a następnie **rozszerzalności**. Wybierz **programu Visual Studio Shell izolowanego** szablonu projektu.  
  
3.  Nazwij projekt `MyVSShellStub` i określ lokalizację. Upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     Nowe rozwiązanie jest wyświetlana w **Eksploratora rozwiązań**.  
  
4.  Skompiluj rozwiązanie i Rozpocznij debugowanie aplikacji isolated shell.  
  
     Program Visual Studio, pojawi się programu isolated shell. Na pasku tytułu odczytuje **MyVSShellStub**. Ikonę na pasku tytułu jest generowany na podstawie \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Dostosowywanie ikona i nazwa aplikacji  
 Można oznaczyć aplikacji przy użyciu nazwy i jego logo firmy na pasku tytułu. Poniższe kroki pokazują, jak zmiana nazwy i ikony, które są wyświetlane na pasku tytułu aplikacji niestandardowych, zmieniając pliku definicji pakietu MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Aby dostosować nazwy aplikacji i ikony  
  
1.  W projekcie MyVSShellStub Otwórz \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Zmień `AppName` wartość elementu do **"AppName" = "Fabrikam utworów muzycznych Editor"**  
  
3.  Aby zmienić ikony aplikacji, skopiuj inną ikonę do katalogu \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Zmień nazwę istniejącego pliku ApplicationIcon.ico na ApplicationIcon1.ico. Zmień nowego pliku ApplicationIcon.ico.  
  
4.  Skompiluj rozwiązanie i Rozpocznij debugowanie. Zostanie wyświetlone programu isolated shell IDE. Pasek tytułu zawiera z nową ikonę obok słowa **Edytor utworów muzycznych Fabrikam**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Dostosowywanie strony głównej przeglądarki sieci Web domyślne  
 W tej sekcji pokazano, jak zmienić domyślną stronę główną z **przeglądarki sieci Web** okna, zmieniając pliku definicji pakietu.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Aby dostosować domyślną stronę główną przeglądarki sieci Web  
  
1.  W pliku MyVSShellStub.Application.pkgdef zmienić `DefaultHomePage` wartość elementu "http://www.microsoft.com".  
  
2.  Skompiluj ponownie projekt MyVSShellStub.  
  
3.  Skompiluj rozwiązanie i Rozpocznij debugowanie.  
  
4.  W **Widok > inne okna**, kliknij przycisk **przeglądarki sieci Web**. **Przeglądarki sieci Web** oknie zostanie wyświetlona strona główna firmy Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Usuwanie polecenia Print  
 Zawiera zestaw deklaracji w postaci pliku vsct w projekcie interfejsu użytkownika programu isolated shell `<Define name=No_` *elementu*`>`, gdzie *elementu* jest jednym z standardowe menu programu Visual Studio i polecenia.  
  
 W przypadku uncommented deklarację, że menu lub poleceń został wykluczony z programu isolated shell. Z drugiej strony jeśli jest oznaczone jako deklaracji, menu lub polecenia jest zawarta w programu isolated shell.  
  
 W poniższych krokach Usuń komentarz polecenia drukowania w pliku vsct.  
  
#### <a name="to-remove-the-print-command"></a>Aby usunąć polecenia print  
  
1.  Sprawdź, czy **drukowania** polecenia pojawi się na **pliku** menu w aplikacji isolated shell.  
  
2.  W projekcie MyVSShellStubUI Otwórz \Resource Files\MyVSShellStubUI.vsct do edycji.  
  
3.  Usuń znaczniki komentarza tego wiersza:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Spowoduje to usunięcie polecenia print.  
  
5.  Uruchom profilowanie aplikacji isolated shell. Sprawdź, czy **Plik > Drukuj** polecenia został usunięty.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Usuwanie funkcji z programu Isolated Shell  
 Możesz usunąć niektóre pakiety, które są ładowane z programem Visual Studio, edytując plik .pkgundef, jeśli nie potrzebujesz tych funkcji w aplikacji niestandardowej programu isolated shell. Należy określić pakiet w jeden z podkluczy klucza rejestru \Packages $ $RootKey.  
  
> [!NOTE]
>  Aby znaleźć funkcje identyfikatorów GUID programu Visual Studio, zobacz [pakietu identyfikatorów GUID programu Visual Studio funkcji](package-guids-of-visual-studio-features.md).  
  
 Poniższa procedura pokazuje, jak usunąć XML edytor z programu isolated shell.  
  
#### <a name="to-remove-the-xml-editor"></a>Aby usunąć edytora XML  
  
1.  Otwórz plik MyVSShellStub.pkgundef w folderze projektu MyVSShellStub dostosowywania powłoki.  
  
2.  Usuń znaczniki komentarza następujący wiersz:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Ponownie skompiluj rozwiązanie i Rozpocznij debugowanie programu isolated shell. Otwórz plik XML, na przykład \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Sprawdź, czy słowa kluczowe XML w pliku nie są kolorowane i że wpisując "<" w wierszu nie uaktywnia etykietki narzędzi XML.  
  
## <a name="customizing-the-helpabout-box"></a>Dostosowywanie Pomoc/informacje pole  
 Można dostosować pomoc/dotyczących pola, który jest utworzona w ramach szablonu projektu programu isolated shell.  
  
#### <a name="to-customize-the-company-name"></a>Aby dostosować nazwy firmy  
  
1.  Nazwa firmy, informacje o prawach autorskich, wersja produktu i opis produktu znaleziono w projekcie MyVSShellStub.AboutBoxPackage w pliku \Properties\AssemblyInfo.cs. Otwórz ten plik.  
  
2.  Zmiana `AssemblyCompany` do wartości **Fabrikam**, `AssemblyProduct` i `AssemblyTitle` wartości do **Fabrikam utworów muzycznych edytora**i `AssemblyCopyright` do wartości **Copyright © Firma Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")]  
    ```  
  
3.  Aby dodać opis produktu, należy zmienić `AssemblyDescription` do wartości **opis Edytor muzyka firmy Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.")]  
    ```  
  
4.  Rozpocznij debugowanie i Otwórz w aplikacji isolated shell **Pomoc > o** pola. Zmienione ciągi powinny być widoczne. Tytuł Pomoc/informacje pole jest taka sama jak `AssemblyTitle` wartość AssemblyInfo.cs.  
  
5.  Właściwości **Pomoc/informacje** samo pole znajdują się w pliku MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Aby zmienić szerokość pomocy/pole informacji, przejdź do `AboutDialogStyle` blokować i ustawić `Width` właściwości 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Ponownie skompiluj rozwiązanie i Rozpocznij debugowanie programu isolated shell. Pomoc/dotyczących pola powinna być około kwadratowych.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Przed wdrożeniem aplikacji Isolated Shell  
 Aplikacja programu isolated shell można zainstalować na dowolnym komputerze, który zawiera pakiet redystrybucyjny programu Visual Studio Shell (izolowany). Aby uzyskać więcej informacji na temat pakietu redystrybucyjnego, zobacz [Visual Studio Extensibility pliki do pobrania](http://go.microsoft.com/fwlink/?LinkID=119298) witryny sieci Web.  
  
## <a name="deploying-the-isolated-shell-application"></a>Wdrażanie aplikacji Isolated Shell  
 W przypadku wdrażania aplikacji programu isolated shell do komputera docelowego, tworząc projekt Instalatora. Należy określić następujące elementy:  
  
-   Układ folderów i plików na komputerze docelowym.  
  
-   Warunków uruchamiania, które gwarantują, że programu .NET Framework i Visual Studio powłoki środowiska uruchomieniowego są instalowane na komputerze docelowym.  
  
 W poniższej procedurze należy zainstalować na komputerze InstallShield Limited Edition.  
  
#### <a name="to-create-the-setup-project"></a>Aby utworzyć projekt Instalatora  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, a następnie kliknij przycisk **Dodawanie nowego projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **inne typy projektów** , a następnie wybierz **instalacji i wdrażania**. Wybierz szablon InstallShield. Nazwa nowego projektu `MySetup` , a następnie kliknij przycisk **OK**.  
  
3.  Jeśli InstallShield Limited Edition jest już zainstalowany, przejdź do następnego kroku.  
  
     Jeśli nie zainstalowano jeszcze InstallShield Limited Edition, zostanie wyświetlona strona pobierania InstallShield. Postępuj zgodnie z instrukcjami, aby pobrać i zainstalować produkt, wybór wersji InstallShield, która jest zgodna z wersją programu Visual Studio. Należy określić, czy do zarejestrowania instalacji InstallShield lub użyć go w wersji ewaluacyjnej. Po zakończeniu instalacji należy ponownie uruchomić program Visual Studio.  
  
    > [!IMPORTANT]
    >  Aby utworzyć projekt InstallShield, należy uruchomić Visual Studio jako administrator. Jeśli nie zrobisz, wystąpi błąd podczas kompilowania projektu.  
  
 W następnych krokach przedstawiono sposób konfigurowania ustawień projektu.  
  
> [!IMPORTANT]
>  Upewnij się, skompilować konfiguracji wydanie projektu programu isolated shell co najmniej raz przed skonfigurowaniem projektu Instalatora.  
  
#### <a name="to-configure-the-setup-project"></a>Aby skonfigurować ustawienia projektu  
  
1.  W **Eksploratora rozwiązań**w obszarze **MySetup** projektu, wybierz **Asystentem projektu**. W wierszu dolnej **Asystentem projektu** okna, wybierz **informacje o aplikacji**. Wprowadź **Fabrikam** jako nazwę swojej firmy i **Edytor utworów muzycznych Fabrikam** jako nazwa aplikacji. Wybierz do przodu strzałkę w prawym dolnym rogu **Asystentem projektu**.  
  
2.  Wybierz **tak** w obszarze **aplikacja wymaga oprogramowania do zainstalowania na komputerze?** , a następnie wybierz **programu Microsoft .NET Framework 4.5 pełny pakiet**.  
  
3.  Wybierz **pliki aplikacji** znajdujący się u dołu okna i upewnij się, że **Edytor utworów muzycznych Fabrikam** jest wybrany folder.  
  
4.  Wybierz **Dodaj pliki** przycisku. W **Dodaj pliki** okno dialogowe Dodaj następujące pliki z **MyVSShellStub\Release** folderu:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Kliknij przycisk **dodać danych wyjściowych projektu** przycisk i dodać **MyVSShellStub/podstawowych danych wyjściowych**. Kliknij przycisk **OK**.  
  
6.  W lewym okienku w obszarze **komputera docelowego**, kliknij prawym przyciskiem myszy **Fabrikam utworów muzycznych Edytor [INSTALLDIR]** węzeł i Dodaj **nowy Folder** o nazwie **rozszerzenia** .  
  
7.  Kliknij prawym przyciskiem myszy **rozszerzenia** węzła w okienku po lewej stronie i Dodaj nowy folder o nazwie **aplikacji**.  
  
8.  Wybierz **aplikacji** folder i kliknij przycisk **dodać danych wyjściowych projektu** przycisk, a następnie wybierz główny wynik projektu MyVSShellStub.AboutBoxPackage.  
  
9. Kliknij przycisk **Dodaj pliki** przycisk i w folderze \MyVSShellStub\Release\Extensions\Application\ należy dodać następujące pliki:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Kliknij prawym przyciskiem myszy **Fabrikam utworów muzycznych Edytor [INSTALLDIR]** węzła w okienku po lewej stronie i Dodaj nowy folder o nazwie **1033**.  
  
11. Wybierz 1033 folder, a następnie kliknij przycisk **dodać danych wyjściowych projektu** przycisk i wybierz główny wynik projektu MyVSShellStubUI.  
  
12. Przenieś do **skróty do aplikacji** okna.  
  
13. Kliknij przycisk **nowy** do tworzenia skrótu i wybierz **\Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output [ProgramFilesFolder]**.  
  
14. Przenieś do **rozmowy instalacji** okienka.  
  
15. Ustaw wszystkie elementy **nr**.  
  
16. W **Eksploratora rozwiązań**, otwórz projekt MySetup **zdefiniować wymagania dotyczące konfiguracji i akcji \ wymagania**. **Wymagania** zostanie otwarte okno.  
  
17. Kliknij prawym przyciskiem myszy **wymagania systemowe oprogramowania** i wybierz **utworzyć nowy warunek uruchomienia**. **Kreatora wyszukiwania systemu** pojawi się.  
  
18. W **co chcesz znaleźć?** okienku wybierz **wpis rejestru** listy rozwijanej i kliknij przycisk **dalej**.  
  
19. W **jak chcesz ją wyszukać?** okienku wybierz **HKEY_LOCAL_MACHINE** jako katalogu głównego rejestru. Wprowadź **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** dla systemów 64-bitowych lub **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** dla systemów 32-bitowych, a następnie wprowadź  **Zainstaluj** jako wartości rejestru. Kliknij przycisk **Dalej**.  
  
20. W **co chcesz zrobić z wartością?** okienku, wprowadź **ten produkt wymaga programu Visual Studio 2015 izolowane powłoki pakiet redystrybucyjny programu do zainstalowania.** jako tekst i kliknij przycisk **Zakończ**.  
  
21. Ponownie skompiluj rozwiązanie programu isolated shell do tworzenia projektu Instalatora.  
  
     Plik setup.exe znajduje się w następującym folderze:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testowanie Program instalacyjny  
 Aby przetestować instalację, skopiuj plik setup.exe na inny komputer, a następnie uruchom plik wykonywalny Instalatora. Można uruchomić aplikacji isolated shell.