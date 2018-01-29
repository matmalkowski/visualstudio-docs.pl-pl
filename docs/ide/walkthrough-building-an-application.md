---
title: "Wskazówki: Tworzenie aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d24a8b0cfa54b56808e8d283534e03e607fca0c9
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="walkthrough-building-an-application"></a>Wskazówki: kompilowanie aplikacji

Wykonując tego przewodnika, użytkownik będzie zapoznanie się ze kilka opcji, które można skonfigurować podczas tworzenia aplikacji za pomocą programu Visual Studio. Zostanie utworzenie konfiguracji niestandardowej kompilacji, Ukryj niektóre komunikaty ostrzegawcze oraz zwiększyć dane wyjściowe kompilacji dla przykładowej aplikacji.

## <a name="install-the-sample-application"></a>Instalowanie przykładowej aplikacji

Pobierz [wprowadzenie do tworzenia aplikacji WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) próbki. Wybierz opcję C# lub Visual Basic. Po pobraniu pliku zip, wyodrębnij go i Otwórz **ExpenseItIntro.sln** plik za pomocą programu Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Tworzenie konfiguracji niestandardowej kompilacji

Po utworzeniu rozwiązania konfiguracje debug i release kompilacji i ich domyślne elementy docelowe platformy są definiowane dla rozwiązania automatycznie. Następnie można dostosować te konfiguracje lub Utwórz swój własny. Konfiguracje kompilacji, określ typ kompilacji. Platformy kompilacji Określ system operacyjny, przeznaczonego dla aplikacji dla danej konfiguracji. Aby uzyskać więcej informacji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md), [platformy kompilacji opis](../ide/understanding-build-platforms.md), i [porady: Ustaw debugowania i konfiguracje wydania](../debugger/how-to-set-debug-and-release-configurations.md).

Można zmienić lub utworzyć konfiguracje i ustawienia platformy przy użyciu **programu Configuration Manager** okno dialogowe. W tej procedurze utworzysz konfigurację kompilacji do testowania.

### <a name="to-create-a-build-configuration"></a>Aby utworzyć konfigurację kompilacji
  
1. Otwórz **programu Configuration Manager** okno dialogowe.
  
     ![Build menu, Configuration Manager command](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2. w **aktywnej konfiguracji rozwiązania** wybierz  **\<nowy... \>**.
  
3. w **nową konfigurację rozwiązania** okno dialogowe, nazwa nowej konfiguracji `Test`, skopiować ustawienia z istniejącej konfiguracji debugowania, a następnie wybierz **OK** przycisku.
  
     ![New Solution Configuration Dialog Box](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4 w **platformy aktywne rozwiązanie** wybierz  **\<nowy... \>**.
  
5 w **nowa platforma rozwiązania** okno dialogowe Wybierz **x64**, a nie kopiuje ustawień z x86 platformy.
  
     ![New Solution Platform Dialog Box](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6. Wybierz **OK** przycisku.
  
 Konfiguracja aktywnego rozwiązania została zmieniona do testu z platformą aktywne rozwiązanie ustawioną x64.
  
 ![Program Configuration Manager z konfiguracji testu](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
7. Wybierz **Zamknij**.

Można szybko sprawdzić lub zmienić aktywnej konfiguracji rozwiązania przy użyciu **konfiguracje rozwiązania** listy na **standardowe** paska narzędzi.
  
![Opcja konfiguracji rozwiązania standardowym pasku narzędzi](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
## <a name="build-the-application"></a>Tworzenie aplikacji

Następnie zostanie utworzenie rozwiązania z konfiguracji niestandardowej kompilacji.
  
### <a name="to-build-the-solution"></a>Tworzenie rozwiązania
  
-   Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.
  
    **Dane wyjściowe** okno wyświetla wyniki kompilacji. Kompilacja zakończyła się pomyślnie.
  
## <a name="hide-compiler-warnings"></a>Ukryj ostrzeżenia kompilatora

Następnie będzie wprowadzeniu kodu powodujący ostrzeżenie ma zostać wygenerowane przez kompilator.

1. W języku C# projektu, otwórz **ExpenseReportPage.xaml.cs** pliku. W **ExpenseReportPage** metody, Dodaj następujący kod: `int i;`.

    LUB

    W projektach Visual Basic, otwórz **ExpenseReportPage.xaml.vb** pliku. W Konstruktorze niestandardowych **publicznego Sub New...** , Dodaj następujący kod: `Dim i`.

2. Skompiluj rozwiązanie.

**Dane wyjściowe** okno wyświetla wyniki kompilacji. Kompilacja zakończyła się pomyślnie, ale zostały wygenerowane ostrzeżenia:  

 Rysunek 1: ostrzeżenia Visual Basic  
  
 ![Dane wyjściowe okna języka Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
 Rysunek 2: C# ostrzeżenia  
  
 ![Dane wyjściowe okna Visual C & 35; ] (../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
Można tymczasowo ukryć niektóre komunikaty ostrzegawcze podczas kompilacji zamiast je zajmowały miejsca danych wyjściowych kompilacji.

### <a name="to-hide-a-specific-c-warning"></a>Aby ukryć określone ostrzeżenia C#
  
1. w **Eksploratora rozwiązań**, wybierz węzeł projektu najwyższego poziomu.
  
2. na pasku menu wybierz **widoku**, **strony właściwości**.
  
     The **Project Designer** opens.
  
3. Wybierz **kompilacji** strony, a następnie w **tłumienie ostrzeżeń** Określ numer ostrzeżenia **0168**.
  
     ![Build page, Project Designer](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     For more information, see [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).
  
4 Skompiluj rozwiązanie.
  
     The **Output** window displays only summary information for the build.
  
     ![Output Window, Visual C&#35; Build Warnings](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
### <a name="to-suppress-all-visual-basic-build-warnings"></a>Aby pominąć wszystkie ostrzeżenia kompilacji Visual Basic
  
1. w **Eksploratora rozwiązań**, wybierz węzeł projektu najwyższego poziomu.
  
2. na pasku menu wybierz **widoku**, **strony właściwości**.
  
     The **Project Designer** opens.
  
3. na **skompilować** wybierz pozycję **Wyłącz wszystkie ostrzeżenia** pole wyboru.
  
     ![Compile page, Project Designer](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     For more information, see [Configuring Warnings in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).
  
4 Skompiluj rozwiązanie.
  
 **Dane wyjściowe** okno wyświetla tylko informacje podsumowania dla kompilacji.
  
 ![Okno danych wyjściowych, Visual Basic kompilacji ostrzeżenia](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 Aby uzyskać więcej informacji, zobacz [porady: pomijanie ostrzeżeń kompilatora](../ide/how-to-suppress-compiler-warnings.md).
  
## <a name="display-additional-build-details-in-the-output-window"></a>W oknie dane wyjściowe są wyświetlane szczegóły dodatkowe kompilacji

Można zmienić, ile informacji na temat procesu kompilacji jest wyświetlana w **dane wyjściowe** okna. Poziom szczegółowości kompilacji jest zwykle ustawiana do minimalnego, co oznacza, że **dane wyjściowe** okno jest wyświetlane tylko podsumowanie procesu tworzenia wraz z wysokim priorytetem ostrzeżeń i błędów. Więcej informacji na temat kompilacji można wyświetlić przy użyciu [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).
  
> [!IMPORTANT]
>  Jeśli możesz wyświetlić więcej informacji, kompilacja zostanie potrwać dłużej.
  
### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Aby zmienić ilość informacji w oknie danych wyjściowych
  
1. Otwórz **opcje** okno dialogowe.
  
     ![Options command on the Tools menu](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  
  
2. Wybierz **projekty i rozwiązania** kategorii, a następnie wybierz pozycję **skompilować i uruchomić** strony.
  
3. w **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz **normalny**, a następnie wybierz pozycję **OK** przycisku.
  
4 na pasku menu wybierz **kompilacji**, **czystą rozwiązania**.
  
5. Skompiluj rozwiązanie, a następnie przejrzyj informacje w **dane wyjściowe** okna.
  
     The build information includes the time that the build started (located at the beginning) and the order in which files were processed. This information also includes the actual compiler syntax that Visual Studio runs during the build.
  
     For example, in the C# build, the [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) option lists the warning code, 1762, that you specified earlier in this topic, along with three other warnings.
  
     In the Visual Basic build, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) doesn't include specific warnings to exclude, so no warnings appear.
  
    > [!TIP]
    >  You can search the contents of the **Output** window if you display the **Find** dialog box by choosing the Ctrl+F keys.
  
Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="create-a-release-build"></a>Tworzenie kompilacji wydania

Można utworzyć wersję przykładowej aplikacji, która jest zoptymalizowana pod kątem wysyłania go. Dla kompilacji wydania będzie określić, że plik wykonywalny został skopiowany do udziału sieciowego, zanim kompilacji zostało rozpoczęte.

Aby uzyskać więcej informacji, zobacz [porady: Zmień katalog danych wyjściowych kompilacji](../ide/how-to-change-the-build-output-directory.md) i [budynku i czyszczenia projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="to-specify-a-release-build-for-visual-basic"></a>Aby określić kompilacji wydania programu Visual Basic
  
1. Otwórz **Projektant projektu**.
  
     ![View menu, Property Pages command](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Wybierz **skompilować** strony.
  
3. w **konfiguracji** wybierz **wersji**.
  
4 w **platformy** wybierz **x86**.
  
5 w **ścieżki wyjściowej kompilacji** Określ ścieżkę sieciową.
  
     For example, you can specify \\\myserver\builds.
  
    > [!IMPORTANT]
    >  A message box might appear, warning you that the network share that you've specified might not be a trusted location. If you trust the location that you've specified, choose the **OK** button in the message box.
  
6. Tworzenie aplikacji.
  
     ![Build Solution command on the Build menu](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
### <a name="to-specify-a-release-build-for-c"></a>Aby określić kompilację wersji dla C# #
  
1. Otwórz **Projektant projektu**.
  
     ![View menu, Property Pages command](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Wybierz **kompilacji** strony.
  
3. w **konfiguracji** wybierz **wersji**.
  
4 w **platformy** wybierz **x86**.
  
5 w **ścieżka wyjściowa** Określ ścieżkę sieciową.
  
     For example, you could specify \\\myserver\builds.
  
    > [!IMPORTANT]
    >  A message box might appear, warning you that the network share that you've specified might not be a trusted location. If you trust the location that you've specified, choose the **OK** button in the message box.
  
6. na **standardowym pasku narzędzi**, Ustaw konfiguracje rozwiązania **wersji** i platformy rozwiązania **x86**.

7 kompilowania aplikacji.
  
     ![Build Solution command on the Build menu](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
 Plik wykonywalny jest kopiowany do określonej ścieżki sieciowej. Jego ścieżka byłaby \\\myserver\builds\\*FileName*.exe.
  
Gratulacje: zakończyła się pomyślnie w tym przewodniku.
  
## <a name="see-also"></a>Zobacz także

[Przewodnik: tworzenie projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)  
[Omówienie wstępnej kompilacji projektu aplikacji sieci Web ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)  
[Przewodnik: Używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md)
