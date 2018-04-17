---
title: 'Wskazówki: Tworzenie pliku projektu MSBuild od początku | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b01e917d0e46c6e5a5d91473332062a75ff1e33d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-msbuild-project-file-from-scratch"></a>Wskazówki: tworzenie pliku projektu MSBuild od zera
Języki programowania, które odnoszą się do programu .NET Framework Użyj pliki projektu MSBuild do opisu i kontrolować proces kompilacji aplikacji. Podczas tworzenia pliku projektu MSBuild za pomocą programu Visual Studio odpowiedniego pliku XML jest automatycznie dodawane do pliku. Jednak może być dobrze zrozumieć sposób organizowania XML i jak można zmienić do kontrolowania kompilacji.  
  
 Informacje o tworzeniu pliku projektu dla projektów C++, zobacz [MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp).  
  
 W tym przewodniku przedstawiono sposób tworzenia pliku podstawowego projektu przyrostowo, za pomocą edytora tekstu. Instruktaż obejmuje następujące kroki:  
  
-   Tworzenie źródłowego pliku minimalnego aplikacji.  
  
-   Tworzenie pliku projektu MSBuild minimalny.  
  
-   Rozszerzanie zmiennej środowiskowej PATH, aby uwzględnić MSBuild.  
  
-   Tworzenie aplikacji przy użyciu pliku projektu.  
  
-   Dodaj właściwości, aby kontrolować kompilacji.  
  
-   Formant kompilacji, zmieniając wartości właściwości.  
  
-   Dodawanie elementów docelowych do kompilacji.  
  
-   Formant kompilacji, określając elementów docelowych.  
  
-   Kompilacja przyrostowa.  
  
 W tym przewodniku przedstawiono sposób kompilowania projektu w wierszu polecenia i sprawdź, czy wyniki. Aby uzyskać więcej informacji na temat MSBuild i uruchamiania programu MSBuild w wierszu polecenia, zobacz [wskazówki: przy użyciu programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 Aby ukończyć przewodnika, musi mieć .NET Framework (wersja 2.0, 3.5, 4.0 i 4.5) zainstalować, ponieważ zawiera on MSBuild i kompilator Visual C#, które są wymagane do przewodnika.  
  
## <a name="creating-a-minimal-application"></a>Tworzenie aplikacji minimalnego  
 W tej sekcji przedstawiono sposób tworzenia minimalnego Visual C# aplikacji pliku źródłowego przy użyciu tekstu Edytor.  
  
#### <a name="to-create-the-minimal-application"></a>Aby utworzyć aplikację minimalnego  
  
1.  W wierszu polecenia przejdź do folderu, w którym chcesz utworzyć aplikację, na przykład \My Documents\ lub \Desktop\\.  
  
2.  Typ **md HelloWorld** do utworzenia podfolderu o nazwie \HelloWorld\\.  
  
3.  Typ **cd HelloWorld** zmiany do nowego folderu.  
  
4.  Uruchom Notatnik lub innego edytora tekstu, a następnie wpisz poniższy kod.  
  
    ```csharp
    using System;  
  
    class HelloWorld  
    {  
        static void Main()  
        {  
    #if DebugConfig  
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");  
    #endif  
  
            Console.WriteLine("Hello, world!");  
        }  
    }  
    ```  
  
5.  Zapisz ten plik kodu źródłowego i nadaj mu nazwę Helloworld.cs.  
  
6.  Tworzenie aplikacji, wpisując **csc helloworld.cs** w wierszu polecenia.  
  
7.  Testowanie aplikacji, wpisując **helloworld** w wierszu polecenia.  
  
     **Hello, world!** powinien zostać wyświetlony komunikat.  
  
8.  Usuń aplikację, wpisując **del helloworld.exe** w wierszu polecenia.  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>Tworzenie pliku projektu MSBuild minimalnego  
 Teraz, gdy masz plik źródłowy minimalnego aplikacji można utworzyć pliku minimalnego projektu do skompilowania aplikacji. Ten plik projektu zawiera następujące elementy:  
  
-   Wymaganego głównego `Project` węzła.  
  
-   `ItemGroup` Węzła zawiera elementy elementu.  
  
-   Element elementu, który odwołuje się do pliku źródłowego aplikacji.  
  
-   A `Target` węzła zawiera zadania, które są wymagane do utworzenia aplikacji.  
  
-   A `Task` elementu, aby uruchomić kompilatora Visual C# do tworzenia aplikacji.  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>Aby utworzyć minimalnego plik projektu programu MSBuild  
  
1.  W edytorze tekstu należy zastąpić istniejący tekst przy użyciu tych dwóch wierszy:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  Wstaw to `ItemGroup` węzeł jako element podrzędny elementu `Project` węzła:  
  
    ```xml  
    <ItemGroup>  
      <Compile Include="helloworld.cs" />  
    </ItemGroup>  
    ```  
  
     Powiadomienie tego `ItemGroup` już zawiera element elementu.  
  
3.  Dodaj `Target` węzeł jako element podrzędny elementu `Project` węzła. Nazwa węzła `Build`.  
  
    ```xml  
    <Target Name="Build">  
    </Target>  
    ```  
  
4.  Wstaw ten element zadania jako elementu podrzędnego `Target` węzła:  
  
    ```xml  
    <Csc Sources="@(Compile)"/>  
    ```  
  
5.  Zapisz ten plik projektu i nadaj mu nazwę Helloworld.csproj.  
  
 Plik projektu minimalnego powinien przypominać następujący kod:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  
  
 Zadania w celu kompilacji są wykonywane sekwencyjnie. W tym przypadku kompilator Visual C# `Csc` zadanie jest tylko zadania. Oczekuje, że lista plików źródłowych do kompilowania i jest określony przez wartość `Compile` elementu. `Compile` Tylko jeden plik źródłowy, Helloworld.cs odwołuje się do elementu.  
  
> [!NOTE]
>  W elemencie elementu znaku wieloznacznego gwiazdki (*) służy do odwołania wszystkich plików mających rozszerzenie nazwy pliku .cs w następujący sposób:  
>   
>  `<Compile Include="*.cs" />`  
>   
>  Jednak nie zaleca się używanie symboli wieloznacznych ponieważ pozwala debugowania i selektywnego celem trudniejsze, jeśli pliki źródłowe zostały dodane lub usunięte.  
  
## <a name="extending-the-path-to-include-msbuild"></a>Rozszerzanie ścieżkę do dołączenia MSBuild  
 Aby korzystać z programu MSBuild, muszą być rozszerzane zmiennej środowiskowej PATH, aby uwzględnić folderu .NET Framework.  
  
#### <a name="to-add-msbuild-to-your-path"></a>Aby dodać do ścieżki programu MSBuild  
  
-   Począwszy od programu Visual Studio 2013, możesz znaleźć MSBuild.exe w folderze MSBuild (`%ProgramFiles%\MSBuild` na 32-bitowym systemie operacyjnym lub `%ProgramFiles(x86)%\MSBuild` na 64-bitowym systemie operacyjnym).  
  
     W wierszu polecenia wpisz **ustawić PATH=%PATH%;%ProgramFiles%\MSBuild** lub **ustawić ŚCIEŻKĘ = % PATH %; % ProgramFiles (x86) %\MSBuild**.  
  
     Jeśli masz zainstalowanego programu Visual Studio, możesz też użyć **wiersz polecenia programu Visual Studio**, która zawiera ścieżki, która zawiera folder programu MSBuild.  
  
## <a name="using-the-project-file-to-build-the-application"></a>Korzystanie z pliku projektu do skompilowania aplikacji  
 Teraz do skompilowania aplikacji, należy użyć pliku projektu, który został właśnie utworzony.  
  
#### <a name="to-build-the-application"></a>Tworzenie aplikacji  
  
1.  W wierszu polecenia wpisz **msbuild helloworld.csproj /t:Build**.  
  
     Powoduje to skompilowanie docelowy kompilacji w pliku projektu Helloworld przez kompilator Visual C#, aby utworzyć aplikację Helloworld.  
  
2.  Testowanie aplikacji, wpisując **helloworld**.  
  
     **Hello, world!** powinien zostać wyświetlony komunikat.  
  
> [!NOTE]
>  Aby zobaczyć więcej szczegółów kompilacji, należy zwiększyć poziom szczegółowości. Aby ustawić poziom szczegółowości "szczegółowe", wpisz dowolne z następujących poleceń w wierszu polecenia:  
>   
>  **/ verbosity /t:Build helloworld.csproj MSBUILD: szczegółowy**  
  
## <a name="adding-build-properties"></a>Dodawanie właściwości kompilacji  
 Właściwości kompilacji można dodać do pliku projektu, aby ściślej kontrolować kompilacji. Teraz dodaj następujące właściwości:  
  
-   `AssemblyName` Właściwość, aby określić nazwę aplikacji.  
  
-   `OutputPath` Właściwości w celu określenia folderu zawierającego aplikację.  
  
#### <a name="to-add-build-properties"></a>Aby dodać właściwości kompilacji  
  
1.  Usuń istniejącą aplikację, wpisując **del helloworld.exe** w wierszu polecenia.  
  
2.  W pliku projektu, Wstaw `PropertyGroup` element zaraz po otwarciu `Project` elementu:  
  
    ```xml  
    <PropertyGroup>  
      <AssemblyName>MSBuildSample</AssemblyName>  
      <OutputPath>Bin\</OutputPath>  
    </PropertyGroup>  
    ```  
  
3.  Dodaj zadanie do docelowego kompilacji bezpośrednio przed `Csc` zadań:  
  
    ```xml  
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
    ```  
  
     `MakeDir` Zadań tworzy folder o nazwie przez `OutputPath` właściwości, pod warunkiem, że nie o takiej nazwie obecnie istnieje folder.  
  
4.  Dodaj tę `OutputAssembly` atrybutu `Csc` zadań:  
  
    ```xml  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    ```  
  
     To powoduje, że kompilator Visual C#, aby utworzyć zestaw o nazwie przez `AssemblyName` właściwości i umieść ją w folderze o nazwie przez `OutputPath` właściwości.  
  
5.  Zapisz zmiany.  
  
 Plik projektu powinien teraz wyglądać następujący kod:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
</Project>  
```  
  
> [!NOTE]
>  Firma Microsoft zaleca dodanie kreska ułamkowa odwrócona (\\) ogranicznik ścieżki na końcu nazwy folderu, w przypadku określenia `OutputPath` elementu zamiast opcji dodawania w `OutputAssembly` atrybutu `Csc` zadań. W związku z tym  
>   
>  `<OutputPath>Bin\</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
>  jest lepszym rozwiązaniem niż  
>   
>  `<OutputPath>Bin</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="testing-the-build-properties"></a>Testowanie właściwości kompilacji  
 Teraz można utworzyć aplikacji przy użyciu pliku projektu używane właściwości kompilacji można określić nazwę folderu i aplikacji danych wyjściowych.  
  
#### <a name="to-test-the-build-properties"></a>Aby przetestować właściwości kompilacji  
  
1.  W wierszu polecenia wpisz **msbuild helloworld.csproj /t:Build**.  
  
     To tworzy \Bin\ folder wywołuje kompilator Visual C#, aby utworzyć aplikację MSBuildSample i umieszcza je w folderze \Bin\.  
  
2.  Aby sprawdzić \Bin\ folder został utworzony i czy zawiera aplikacji MSBuildSample, wpisz **katalog Bin**.  
  
3.  Testowanie aplikacji, wpisując **Bin\MSBuildSample**.  
  
     **Hello, world!** powinien zostać wyświetlony komunikat.  
  
## <a name="adding-build-targets"></a>Dodawanie elementów docelowych kompilacji  
 Następnie dodaj dwa więcej elementów docelowych do pliku projektu następujący sposób:  
  
-   Wyczyść obiekt docelowy, która usuwa stare pliki.  
  
-   Element docelowy odbudowy, który używa `DependsOnTargets` atrybutu, aby wymusić czystą zadania do uruchomienia przed zadania kompilacji.  
  
 Teraz, gdy masz wiele elementów docelowych, można ustawić docelowy kompilacji jako domyślnego obiektu docelowego.  
  
#### <a name="to-add-build-targets"></a>Aby dodać obiekty docelowe kompilacji  
  
1.  W pliku projektu należy dodać tych dwóch elementów docelowych tylko po elemencie docelowym kompilacji:  
  
    ```xml  
    <Target Name="Clean" >  
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
    ```  
  
     Docelowy czystą wywołuje Usuń zadanie, aby usunąć aplikację. Docelowy Odbuduj nie zostanie uruchomione, dopóki obiekt docelowy czystą i element docelowy kompilacji został uruchomiony. Mimo że element docelowy Odbuduj nie ma zadań, powoduje czystą cel do uruchomienia przed elementem docelowym kompilacji.  
  
2.  Dodaj tę `DefaultTargets` atrybutu w celu otwarcia `Project` elementu:  
  
    ```xml  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
     Element docelowy kompilacji to ustawienie jako domyślnego obiektu docelowego.  
  
 Plik projektu powinien teraz wyglądać następujący kod:  
  
```xml  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Clean" >  
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
</Project>  
```  
  
## <a name="testing-the-build-targets"></a>Testowanie obiekty docelowe kompilacji  
 Można korzystać nowe obiekty docelowe kompilacji do przetestowania tych funkcji w pliku projektu:  
  
-   Tworzenie kompilacji domyślnej.  
  
-   Ustawienie nazwy aplikacji, w wierszu polecenia.  
  
-   Usuwanie aplikacji przed jest wbudowana w innej aplikacji.  
  
-   Usuwanie aplikacji bez tworzenia innej aplikacji.  
  
#### <a name="to-test-the-build-targets"></a>Aby przetestować obiekty docelowe kompilacji  
  
1.  W wierszu polecenia wpisz **/p:AssemblyName helloworld.csproj programu msbuild = pozdrowienia**.  
  
     Ponieważ nie używasz **/t** przełączyć jawnie ustawić obiekt docelowy, MSBuild uruchamia element docelowy kompilacji domyślnej. **/P** przełącznika zastąpienia `AssemblyName` właściwości i nadaje mu nową wartość `Greetings`. Powoduje to nową aplikację, Greetings.exe, należy utworzyć w folderze \Bin\.  
  
2.  Aby sprawdzić, czy \Bin\ folder zawiera zarówno aplikacji MSBuildSample, jak i Nowa aplikacja pozdrowienia, wpisz **katalog Bin**.  
  
3.  Testowanie aplikacji pozdrowienia wpisując **Bin\Greetings**.  
  
     **Hello, world!** powinien zostać wyświetlony komunikat.  
  
4.  Usuń aplikację MSBuildSample wpisując **msbuild helloworld.csproj /t: czystą**.  
  
     Ta funkcja jest uruchamiana czystą zadań w celu usunięcia aplikacji, która domyślnie `AssemblyName` wartość właściwości `MSBuildSample`.  
  
5.  Usuń aplikację pozdrowienia wpisując **msbuild helloworld.csproj /t: clean /p:AssemblyName = pozdrowienia**.  
  
     Ta funkcja jest uruchamiana czystą zadań, aby usunąć aplikację, która ma danego **AssemblyName** wartość właściwości `Greetings`.  
  
6.  Aby sprawdzić, czy \Bin\ folder jest pusta, wpisz **katalog Bin**.  
  
7.  Typ **msbuild**.  
  
     Mimo że nie określono pliku projektu, program MSBuild tworzy plik helloworld.csproj, ponieważ istnieje tylko jeden plik projektu w bieżącym folderze. Powoduje to, że aplikacja MSBuildSample ma zostać utworzony w folderze \Bin\.  
  
     Aby sprawdzić, czy \Bin\ folder zawiera aplikację MSBuildSample, wpisz **katalog Bin**.  
  
## <a name="building-incrementally"></a>Kompilacja przyrostowa  
 Można ustalić MSBuild do tworzenia obiektu docelowego, tylko wtedy, gdy zostały zmienione pliki źródłowe lub pliki docelowe zależy od obiektu docelowego. MSBuild używa sygnaturę czasową pliku w celu określenia, czy została ona zmieniona.  
  
#### <a name="to-build-incrementally"></a>Aby kompilacja przyrostowa  
  
1.  W pliku projektu należy dodać te atrybuty do otwarcia docelowej kompilacji:  
  
    ```  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     To ustawienie określa, że element docelowy kompilacji zależy od plików wejściowych, które są określone w `Compile` grupy elementów, a element docelowy danych wyjściowych jest pliku aplikacji.  
  
     Wynikowy obiekt docelowy kompilacji powinien przypominać następujący kod:  
  
    ```xml  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2.  Testowanie docelowy kompilacji, wpisując **msbuild /v:d** w wierszu polecenia.  
  
     Należy pamiętać, domyślny plik projektu jest helloworld.csproj, czy tej kompilacji jest elementem docelowym domyślne.  
  
     **/V:d** przełącznik określa pełen opis procesu kompilacji.  
  
     Powinny być wyświetlane następujące wiersze:  
  
     **Pomijanie elementu docelowego "Kompilacji", ponieważ wszystkie pliki wyjściowe są aktualne w porównaniu z plikami wejściowymi.**  
  
     **Pliki wejściowe: HelloWorld.cs**  
  
     **Pliki wyjściowe: BinMSBuildSample.exe**  
  
     MSBuild pomija docelowy kompilacji, ponieważ żaden z plików źródłowych zostały zmienione od czasu ostatniego została skompilowana aplikacja.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono plik projektu, który kompiluje się [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji oraz rejestruje komunikat, który zawiera nazwę pliku wyjściowego.  
  
### <a name="code"></a>Kod  
  
```xml
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files of type CSFile -->  
        <CSC  
            Sources = "@(CSFile)"  
            OutputAssembly = "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Komentarze  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono plik projektu, który kompiluje się [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aplikacji oraz rejestruje komunikat, który zawiera nazwę pliku wyjściowego.  
  
### <a name="code"></a>Kod  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldVB</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <VBFile Include = "consolehwvb1.vb"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">      
        <!-- Run the Visual Basic compilation using input files of type VBFile -->  
        <VBC  
            Sources = "@(VBFile)"  
            OutputAssembly= "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the VBC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </VBC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="whats-next"></a>Co to jest dalej?  
 Visual Studio automatycznie można wykonać większość zadań, które przedstawiono w tym przewodniku. Aby dowiedzieć się, jak używać programu Visual Studio do tworzenia, edytowania, tworzenie i testowanie pliki projektu programu MSBuild, zobacz [wskazówki: przy użyciu programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="see-also"></a>Zobacz też  
[Przegląd MSBuild](../msbuild/msbuild.md)  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)