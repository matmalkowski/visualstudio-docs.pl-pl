---
title: "Wskazówki: Tworzenie SDK przy użyciu języka C# lub Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5f944dad46225a70192bbfb0dbd0d1dc6dc861a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Wskazówki: Tworzenie SDK przy użyciu języka C# lub Visual Basic
W tym przewodniku dowiesz się, jak utworzyć prosty SDK biblioteki matematyczne za pomocą Visual C# i następnie pakietu SDK jako Visual Studio rozszerzenia (VSIX). Będzie wykonaj następujące procedury:  
  
-   [Można utworzyć składnika środowiska wykonawczego systemu Windows SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Aby utworzyć projekt rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Aby utworzyć przykładową aplikację używającą biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a>Można utworzyć składnika środowiska wykonawczego systemu Windows SimpleMath  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **nowy projekt**.  
  
2.  Na liście szablonów, rozwiń węzeł **Visual C#** lub **Visual Basic**, wybierz **Sklepu Windows** węzeł, a następnie wybierz pozycję **składnika środowiska wykonawczego systemu Windows** szablonu.  
  
3.  W **nazwa** określ **SimpleMath**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **SimpleMath** węzła projektu, a następnie wybierz **właściwości**.  
  
5.  Zmień nazwę **Class1.cs** do **Arithmetic.cs** i zaktualizować ją do dopasowania następujący kod:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  W **Eksploratora rozwiązań**, otwórz menu skrótów **rozwiązania "SimpleMath"** węzeł, a następnie wybierz pozycję **programu Configuration Manager**.  
  
     **Programu Configuration Manager** zostanie otwarte okno dialogowe.  
  
7.  W **aktywnej konfiguracji rozwiązania** wybierz **wersji**.  
  
8.  W **konfiguracji** kolumny, upewnij się, że **SimpleMath** wiersza **wersji**, a następnie wybierz pozycję **Zamknij** przycisk, aby zaakceptować Zmiana.  
  
    > [!IMPORTANT]
    >  Zestaw SDK dla składnika SimpleMath zawiera tylko jedną konfigurację. Ta konfiguracja musi być kompilacji wydania lub aplikacje, które używają składnika nie przekaże certyfikacji[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].  
  
9. W **Eksploratora rozwiązań**, otwórz menu skrótów **SimpleMath** węzła projektu, a następnie wybierz **kompilacji**.  
  
##  <a name="createVSIX"></a>Aby utworzyć projekt rozszerzenia SimpleMathVSIX  
  
1.  Menu skrótów dla **rozwiązania "SimpleMath"** węzła, wybierz **Dodaj**, **nowy projekt**.  
  
2.  Na liście szablonów, rozwiń węzeł **Visual C#** lub **Visual Basic**, wybierz **rozszerzalności** węzeł, a następnie wybierz pozycję **projektu VSIX** szablon.  
  
3.  W **nazwa** określ **SimpleMathVSIX**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **Eksploratora rozwiązań**, wybierz **source.extension.vsixmanifest** elementu.  
  
5.  Na pasku menu wybierz **widoku**, **kod**.  
  
6.  Zastąp istniejący plik XML następujący kod XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  W **Eksploratora rozwiązań**, wybierz **SimpleMathVSIX** projektu.  
  
8.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
9. Na liście **wspólne elementy**, rozwiń węzeł **danych**, a następnie wybierz pozycję **pliku XML**.  
  
10. W **nazwa** określ `SDKManifest.xml`, a następnie wybierz pozycję **Dodaj** przycisku.  
  
11. W **Eksploratora rozwiązań**, otwórz menu skrótów `SDKManifest.xml`, wybierz **właściwości**, a następnie zmień wartość **Include w pliku VSIX** właściwości **True**.  
  
12. Zastąp zawartość pliku XML następujące:  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. W **Eksploratora rozwiązań**, otwórz menu skrótów **SimpleMathVSIX** projektu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy Folder**.  
  
14. Zmień nazwę folderu do `references`.  
  
15. Otwórz menu skrótów **odwołania** folderu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy Folder**.  
  
16. Zmień nazwę podfolderu, aby `commonconfiguration`, utwórz podfolder, a nazwa podfolderu `neutral`.  
  
17. Powtórz poprzednie cztery kroki tego czasu zmiany nazwy pierwszego folderu do `redist`.  
  
     Projekt obecnie zawiera następującą strukturę folderów:  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. W **Eksploratora rozwiązań**, otwórz menu skrótów **SimpleMath** projektu, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików**.  
  
19. W **Eksploratora plików**, przejdź do folderu bin\Release, otwórz menu skrótów dla pliku SimpleMath.winmd, a następnie wybierz **kopiowania**.  
  
20. W **Eksploratora rozwiązań**, wklej go do folderu references\commonconfiguration\neutral w **SimpleMathVSIX** projektu.  
  
21. Powtórz poprzedni krok, wklejania pliku SimpleMath.pri w folderze redist\commonconfiguration\neutral w **SimpleMathVSIX** projektu.  
  
22. W **Eksploratora rozwiązań**, wybierz **SimpleMath.winmd**.  
  
23. Na pasku menu wybierz **widoku**, **właściwości** (klawiatury: Wybierz klucz F4).  
  
24. W **właściwości** Zmień **Akcja kompilacji** właściwości **zawartości**, a następnie zmień **Include w pliku VSIX** właściwości  **Wartość true,**.  
  
25. W **Eksploratora rozwiązań**, powtórz ten proces dla **SimpleMath.pri**.  
  
26. W **Eksploratora rozwiązań**, wybierz **SimpleMathVSIX** projektu.  
  
27. Na pasku menu wybierz **kompilacji**, **kompilacji SimpleMathVSIX**.  
  
28. W **Eksploratora rozwiązań**, otwórz menu skrótów **SimpleMathVSIX** projektu, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików**.  
  
29. W **Eksploratora plików**, przejdź do folderu \bin\Release, a następnie uruchom SimpleMathVSIX.vsix go zainstalować.  
  
30. Wybierz **zainstalować** przycisku, poczekaj na zakończenie instalacji i ponownym uruchomieniu programu Visual Studio.  
  
##  <a name="createSample"></a>Aby utworzyć przykładową aplikację używającą biblioteki klas  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **nowy projekt**.  
  
2.  Na liście szablonów, rozwiń węzeł **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **Sklepu Windows** węzła.  
  
3.  Wybierz **pusta aplikacja** szablonu, nazwy projektu **ArithmeticUI**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ArithmeticUI** projektu, a następnie wybierz pozycję **Dodaj**, **odwołania**.  
  
5.  Na liście typów referencyjnych, rozwiń węzeł **Windows**, a następnie wybierz pozycję **rozszerzenia**.  
  
6.  W okienku szczegółów wybierz **proste SDK matematyczne** rozszerzenia.  
  
     Pojawi się dodatkowe informacje na temat zestawu SDK. Możesz wybrać **więcej informacji o** łącze, aby otworzyć http://www.msdn.microsoft.com, jak określono w pliku SDKManifest.xml we wcześniejszej części tego przewodnika.  
  
7.  W **Menedżera odwołań** okno dialogowe, wybierz opcję **proste SDK matematyczne** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
8.  Na pasku menu wybierz **widoku**, **przeglądarki obiektów**.  
  
9. W **Przeglądaj** wybierz **proste matematyczne**.  
  
     Można teraz Poznaj nowości w zestawie SDK.  
  
10. W **Eksploratora rozwiązań**, otwórz MainPage.xaml i zastąpić jej zawartość XAML następujące:  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
    
    **Visual Basic**
    ```xml
    <Page
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
  
11. Aktualizacja MainPage.xaml.cs odpowiadające następujący kod:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. Wybierz klawisz F5, aby uruchomić aplikację.  
  
13. W aplikacji, wprowadź wszelkie dwóch liczb, wybierz operację, a następnie wybierz  **=**  przycisku.  
  
     Zostanie wyświetlone prawidłowego wyniku.  
  
 Pomyślnie utworzono i użyć zestawu SDK rozszerzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie zestawu SDK, w języku C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Wskazówki: Tworzenie SDK przy użyciu języka JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md)