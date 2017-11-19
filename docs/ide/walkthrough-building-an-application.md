---
title: "Wskazówki: Tworzenie aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a06bd1eb1ced8305425a9e3698e66f0d19438463
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-building-an-application"></a>Wskazówki: kompilowanie aplikacji
Wykonując tego przewodnika, użytkownik będzie zapoznanie się ze kilka opcji, które można skonfigurować podczas tworzenia aplikacji za pomocą programu Visual Studio. Zostanie utworzenie konfiguracji niestandardowej kompilacji, Ukryj niektóre komunikaty ostrzegawcze oraz zwiększyć dane wyjściowe kompilacji dla przykładowej aplikacji.  
  
 Ten temat zawiera następujące sekcje:  
  
 [Instalowanie przykładowej aplikacji](../ide/walkthrough-building-an-application.md#BKMK_installapp)  
  
 [Tworzenie konfiguracji niestandardowej kompilacji](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)  
  
 [Tworzenie aplikacji](../ide/walkthrough-building-an-application.md#BKMK_building)  
  
 [Ukryj ostrzeżenia kompilatora](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)  
  
 [W oknie dane wyjściowe są wyświetlane szczegóły dodatkowe kompilacji](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)  
  
 [Tworzenie kompilacji wydania](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)  
  
##  <a name="BKMK_installapp"></a>Instalowanie przykładowej aplikacji  
Pobierz [wprowadzenie do tworzenia aplikacji WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) próbki. Wybierz opcję C# lub Visual Basic. Po pobraniu pliku zip, wyodrębnij go i Otwórz **ExpenseItIntro.sln** plik za pomocą programu Visual Studio.  
  
##  <a name="BKMK_CreateBuildConfig"></a>Tworzenie konfiguracji niestandardowej kompilacji  
 Po utworzeniu rozwiązania konfiguracje debug i release kompilacji i ich domyślne elementy docelowe platformy są definiowane dla rozwiązania automatycznie. Następnie można dostosować te konfiguracje lub Utwórz swój własny. Konfiguracje kompilacji, określ typ kompilacji. Platformy kompilacji Określ system operacyjny, przeznaczonego dla aplikacji dla danej konfiguracji. Aby uzyskać więcej informacji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md), [platformy kompilacji opis](../ide/understanding-build-platforms.md), i [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Można zmienić lub utworzyć konfiguracje i ustawienia platformy przy użyciu **programu Configuration Manager** okno dialogowe. W tej procedurze utworzysz konfigurację kompilacji do testowania.  
  
#### <a name="to-create-a-build-configuration"></a>Aby utworzyć konfigurację kompilacji  
  
1.  Otwórz **programu Configuration Manager** okno dialogowe.  
  
     ![Tworzenie menu programu Configuration Manager polecenie](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2.  W **aktywnej konfiguracji rozwiązania** wybierz  **\<nowy... \>**.  
  
3.  W **nową konfigurację rozwiązania** okno dialogowe, nazwa nowej konfiguracji `Test`, skopiować ustawienia z istniejącej konfiguracji debugowania, a następnie wybierz **OK** przycisku.  
  
     ![Nowe okno dialogowe konfiguracji rozwiązania](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4.  W **platformy aktywne rozwiązanie** wybierz  **\<nowy... \>**.  
  
5.  W **nowa platforma rozwiązania** oknie dialogowym wybierz **x64**, a nie kopiuje ustawień z x86 platformy.  
  
     ![Okno dialogowe Nowy platformy rozwiązania](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6.  Wybierz **OK** przycisku.  
  
 Konfiguracja aktywnego rozwiązania została zmieniona do testu z platformą aktywne rozwiązanie ustawioną x64.  
  
 ![Program Configuration Manager z konfiguracji testu](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
7. Wybierz **Zamknij**.  

Można szybko sprawdzić lub zmienić aktywnej konfiguracji rozwiązania przy użyciu **konfiguracje rozwiązania** listy na **standardowe** paska narzędzi.  
  
![Opcja konfiguracji rozwiązania standardowym pasku narzędzi](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
##  <a name="BKMK_building"></a>Tworzenie aplikacji  
 Następnie zostanie utworzenie rozwiązania z konfiguracji niestandardowej kompilacji.  
  
#### <a name="to-build-the-solution"></a>Tworzenie rozwiązania  
  
-   Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
    **Dane wyjściowe** okno wyświetla wyniki kompilacji. Kompilacja zakończyła się pomyślnie.  
  
##  <a name="BKMK_hidewarning"></a>Ukryj ostrzeżenia kompilatora  
Następnie będzie wprowadzeniu kodu powodujący ostrzeżenie ma zostać wygenerowane przez kompilator.  

1. W języku C# projektu, otwórz **ExpenseReportPage.xaml.cs** pliku. W **ExpenseReportPage** metody, Dodaj następujący kod: `int i;`.  

    LUB

    W projektach Visual Basic, otwórz **ExpenseReportPage.xaml.vb** pliku. W Konstruktorze niestandardowych **publicznego Sub New...** , Dodaj następujący kod: `Dim i`.  

2. Skompiluj rozwiązanie.  

**Dane wyjściowe** okno wyświetla wyniki kompilacji. Kompilacja zakończyła się pomyślnie, ale zostały wygenerowane ostrzeżenia:  

 Rysunek 1: ostrzeżenia Visual Basic  
  
 ![Dane wyjściowe okna języka Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
 Rysunek 2: Visual C# ostrzeżenia  
  
 ![Dane wyjściowe okna Visual C & 35; ] (../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
Można tymczasowo ukryć niektóre komunikaty ostrzegawcze podczas kompilacji zamiast je zajmowały miejsca danych wyjściowych kompilacji.  

#### <a name="to-hide-a-specific-visual-c-warning"></a>Aby ukryć określone ostrzeżenia Visual C#  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu najwyższego poziomu.  
  
2.  Na pasku menu wybierz **widoku**, **strony właściwości**.  
  
     **Projektanta projektu** otwiera.  
  
3.  Wybierz **kompilacji** strony, a następnie w **tłumienie ostrzeżeń** Określ numer ostrzeżenia **0168**.  
  
     ![Strona, Projektant projektu kompilacji](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     Aby uzyskać więcej informacji, zobacz [strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
4.  Skompiluj rozwiązanie.  
  
     **Dane wyjściowe** okno wyświetla tylko informacje podsumowania dla kompilacji.  
  
     ![Okno danych wyjściowych, Visual C & 35; Tworzenie ostrzeżenia](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Aby pominąć wszystkie ostrzeżenia kompilacji Visual Basic  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu najwyższego poziomu.  
  
2.  Na pasku menu wybierz **widoku**, **strony właściwości**.  
  
     **Projektanta projektu** otwiera.  
  
3.  Na **skompilować** wybierz pozycję **Wyłącz wszystkie ostrzeżenia** pole wyboru.  
  
     ![Strona kompilowania, Projektant projektu](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
4.  Skompiluj rozwiązanie.  
  
 **Dane wyjściowe** okno wyświetla tylko informacje podsumowania dla kompilacji.  
  
 ![Okno danych wyjściowych, Visual Basic kompilacji ostrzeżenia](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 Aby uzyskać więcej informacji, zobacz [porady: pomijanie ostrzeżeń kompilatora](../ide/how-to-suppress-compiler-warnings.md).  
  
##  <a name="BKMK_outputdetails"></a>W oknie dane wyjściowe są wyświetlane szczegóły dodatkowe kompilacji  
 Można zmienić, ile informacji na temat procesu kompilacji jest wyświetlana w **dane wyjściowe** okna. Poziom szczegółowości kompilacji jest zwykle ustawiana do minimalnego, co oznacza, że **dane wyjściowe** okno jest wyświetlane tylko podsumowanie procesu tworzenia wraz z wysokim priorytetem ostrzeżeń i błędów. Więcej informacji na temat kompilacji można wyświetlić przy użyciu [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).  
  
> [!IMPORTANT]
>  Jeśli możesz wyświetlić więcej informacji, kompilacja zostanie potrwać dłużej.  
  
#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Aby zmienić ilość informacji w oknie danych wyjściowych  
  
1.  Otwórz **opcje** okno dialogowe.  
  
     ![Opcje polecenia w menu narzędzia](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE ToolsOptionsmenu")  
  
2.  Wybierz **projekty i rozwiązania** kategorii, a następnie wybierz pozycję **skompilować i uruchomić** strony.  
  
3.  W **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz **normalny**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  Na pasku menu wybierz **kompilacji**, **czystą rozwiązania**.  
  
5.  Skompiluj rozwiązanie, a następnie przejrzyj informacje w **dane wyjściowe** okna.  
  
     Informacje o kompilacji obejmuje przy uruchomieniu kompilacji (znajdujący się na początku) i kolejność, w jakiej były przetwarzane pliki. Informacje te obejmują również składnię rzeczywiste kompilatora Visual Studio jest uruchamiany podczas kompilacji.  
  
     Na przykład w programie Visual C# kompilacji [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) opcja list kod ostrzeżenia 1762, który określony wcześniej w tym temacie, wraz z trzech inne ostrzeżenia.  
  
     W kompilacji Visual Basic [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) nie zawiera określone ostrzeżenia do wykluczenia, aby były wyświetlane nie ostrzeżenia.  
  
    > [!TIP]
    >  Umożliwia wyszukiwanie zawartości **dane wyjściowe** okno podczas wyświetlania **znaleźć** okno dialogowe, wybierając klawiszy Ctrl + F.  
  
Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
##  <a name="BKMK_releasebuild"></a>Tworzenie kompilacji wydania  
 Można utworzyć wersję przykładowej aplikacji, która jest zoptymalizowana pod kątem wysyłania go. Dla kompilacji wydania będzie określić, że plik wykonywalny został skopiowany do udziału sieciowego, zanim kompilacji zostało rozpoczęte.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Zmień katalog danych wyjściowych kompilacji](../ide/how-to-change-the-build-output-directory.md) i [budynku i czyszczenia projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).  
  
#### <a name="to-specify-a-release-build-for-visual-basic"></a>Aby określić kompilacji wydania programu Visual Basic  
  
1.  Otwórz **Projektant projektu**.  
  
     ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.  Wybierz **skompilować** strony.  
  
3.  W **konfiguracji** wybierz **wersji**.  
  
4.  W **platformy** wybierz **x86**.  
  
5.  W **ścieżki wyjściowej kompilacji** Określ ścieżkę sieciową.  
  
     Na przykład można określić \\\myserver\builds.  
  
    > [!IMPORTANT]
    >  Okno komunikatu może wystąpić ostrzeżenie, że udział sieciowy, który został określony, może nie być zaufanej lokalizacji. Jeśli ufasz lokalizacji, która została określona, wybierz **OK** przycisk w oknie komunikatu.  
  
6.  Tworzenie aplikacji.  
  
     ![Kompiluj rozwiązanie, polecenie menu kompilacji](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
#### <a name="to-specify-a-release-build-for-visual-c"></a>Aby określić kompilację wersji Visual C# #
  
1.  Otwórz **Projektant projektu**.  
  
     ![Menu Widok, polecenie strony właściwości](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.  Wybierz **kompilacji** strony.  
  
3.  W **konfiguracji** wybierz **wersji**.  
  
4.  W **platformy** wybierz **x86**.  
  
5.  W **ścieżka wyjściowa** Określ ścieżkę sieciową.  
  
     Na przykład można określić \\\myserver\builds.  
  
    > [!IMPORTANT]
    >  Okno komunikatu może wystąpić ostrzeżenie, że udział sieciowy, który został określony, może nie być zaufanej lokalizacji. Jeśli ufasz lokalizacji, która została określona, wybierz **OK** przycisk w oknie komunikatu.  
  
6.  Na **standardowym pasku narzędzi**, Ustaw konfiguracje rozwiązania **wersji** i platformy rozwiązania **x86**.  

7.  Tworzenie aplikacji.  
  
     ![Kompiluj rozwiązanie, polecenie menu kompilacji](../ide/media/exploreide-buildsolution.png "ExploreIDE BuildSolution")  
  
 Plik wykonywalny jest kopiowany do określonej ścieżki sieciowej. Jego ścieżka byłaby \\\myserver\builds\\*FileName*.exe.  
  
Gratulacje: zakończyła się pomyślnie w tym przewodniku.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie projektu (C++)](/cpp/ide/walkthrough-building-a-project-cpp)   
 [Omówienie wstępnej kompilacji projektu aplikacji sieci Web ASP.NET](http://msdn.microsoft.com/en-us/b940abbd-178d-4570-b441-52914fa7b887)   
 [Wskazówki: Korzystanie z MSBuild](../msbuild/walkthrough-using-msbuild.md)
