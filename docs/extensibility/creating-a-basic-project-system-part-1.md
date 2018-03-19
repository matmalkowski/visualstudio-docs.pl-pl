---
title: "Tworzenie systemu podstawowego projektu, część 1 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bf0570dd6f58d6a6893be5babdcde530d3a57109
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="creating-a-basic-project-system-part-1"></a>Tworzenie systemu podstawowego projektu, część 1
W programie Visual Studio projekty są kontenerami, które deweloperzy korzystać w celu uporządkowania plików kodu źródłowego i innych zasobów. Projekty są wyświetlane jako elementy podrzędne rozwiązań w **Eksploratora rozwiązań**. Projekty umożliwiają organizowanie, tworzenia, debugowania i wdróż kod źródłowy i utworzyć odwołania do usług sieci Web, baz danych i innych zasobów.  
  
 Projekty są definiowane w plikach projektu, na przykład pliku .csproj projektach Visual C#. Możesz utworzyć własne typu projektu, który ma własne rozszerzenie nazwy pliku projektu. Aby uzyskać więcej informacji na temat typów projektów, zobacz [typów projektów](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Należy rozszerzyć Visual Studio z typem niestandardowe projektu, dlatego zdecydowanie zalecamy wykorzystaniu [Visual Studio System projektu](https://github.com/Microsoft/VSProjectSystem) (VSPS) który ma wiele zalet w porównaniu z tworzenia projektu systemu od zera:  
>   
>  -  Łatwiejsze dołączania.  Nawet systemu podstawowego projektu wymaga dziesiątki tysięcy wierszy kodu.  Wykorzystanie VSPS zmniejsza koszt dołączania kilka kliknięć, przed wszystko będzie gotowe dostosować go do potrzeb.  
>  -  Łatwiejsze konserwacji.  Dzięki wykorzystaniu VSPS, wystarczy do obsługi własnych scenariuszy.  Chronimy utrzymania wszystkich infrastruktury systemu projektu.  
>   
>  Jeśli potrzebujesz do docelowej wersji programu Visual Studio starsze niż Visual Studio 2013, nie można wykorzystać VSPS rozszerzenia programu Visual Studio.  Jeśli tak jest, w tym przewodniku jest dobrym miejscem, aby rozpocząć pracę.  
  
 W tym przewodniku przedstawiono sposób tworzenia typem projektu, który ma .myproj rozszerzenia nazwy pliku projektu. W tym przewodniku obiektowy istniejącego systemu projektów Visual C#.  
  
> [!NOTE]
>  Więcej przykładów dotyczących projektów rozszerzeń, zobacz [przykłady VSSDK](http://aka.ms/vs2015sdksamples).  
  
 Ten przewodnik zawiera instrukcje wykonać te zadania:  
  
-   Tworzenie typu podstawowego projektu.  
  
-   Tworzenie szablonu podstawowego projektu.  
  
-   Zarejestruj szablonu projektu programu Visual Studio.  
  
-   Utwórz wystąpienie projekt, otwierając **nowy projekt** okno dialogowe, a następnie użyć szablonu.  
  
-   Tworzenie fabryki projektu systemu projektu.  
  
-   Utworzyć węzła projektu systemu projektu.  
  
-   Dodawanie ikon niestandardowych dla systemu projektu.  
  
-   Implementuje zamienny parametr szablonu podstawowego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Należy również pobrać kodu źródłowego dla [zarządzane Framework pakietu dla projektów](http://mpfproj12.codeplex.com/). Wyodrębnij plik do lokalizacji, która jest dostępna do rozwiązania, które chcesz utworzyć.  
  
## <a name="creating-a-basic-project-type"></a>Tworzenie typu podstawowego projektu  
 Tworzenie projektu VSIX C# o nazwie **SimpleProject**. (**Pliku, nowe, projekt** , a następnie **projektach Visual C#, rozszerzalności, VSIX**). Dodawanie szablonu elementu projektu pakietu Visual Studio (w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**, następnie przejdź do **rozszerzalności / pakietu Visual Studio**). Nadaj nazwę plikowi **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Tworzenie szablonu projektu podstawowe  
 Teraz możesz zmodyfikować ten podstawowy pakiet VSPackage do zaimplementowania nowy typ projektu .myproj. Aby utworzyć projekt, który jest oparty na typie projektu .myproj, Visual Studio musi wiedzieć, które pliki, zasobów i odwołania do dodania do nowego projektu. Aby podać te informacje, należy umieścić pliki projektu w folderze szablonu projektu. Gdy użytkownik używa projektu .myproj, aby utworzyć projekt, pliki są kopiowane do nowego projektu.  
  
#### <a name="to-create-a-basic-project-template"></a>Aby utworzyć szablon projektu podstawowe  
  
1.  Dodaj trzy foldery do projektu, co w innych: **Templates\Projects\SimpleProject**. (W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **SimpleProject** węzła projektu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **nowy Folder**. Nazwa folderu `Templates`. W **szablony** folderu, Dodaj folder o nazwie `Projects`. W **projekty** folderu, Dodaj folder o nazwie `SimpleProject`.)  
  
2.  W **Templates\Projects\SimpleProject** folderu, Dodaj plik bitmapy jako ikonę o nazwie `SimpleProject.ico`. Po kliknięciu **Dodaj**, zostanie otwarty w edytorze ikon.  
  
3.  Ikona charakterystyczne. Ta ikona zostanie wyświetlony w **nowy projekt** okno dialogowe później w tym przewodnikiem.  
  
     ![Ikona prostego projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  Zapisz i zamknij Edytor ikony.  
  
5.  W **Templates\Projects\SimpleProject** folderu, Dodaj **klasy** elementu o nazwie `Program.cs`.  
  
6.  Zastąp istniejący kod następujące wiersze.  
  
    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
  
    namespace $nameSpace$
    {  
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```
  
    > [!IMPORTANT]
    >  To nie jest ostatecznej formie kodu Program.cs; Parametry zamiany będzie rozpatrywane w kolejnym kroku. Może zostać wyświetlony błędy kompilacji, ale tak długo, jak pliku **BuildAction** jest **zawartości**, powinno być możliwe skompilować i uruchomić projekt w zwykły sposób.  
  
1.  Zapisz plik.  
  
2.  Skopiuj plik AssemblyInfo.cs z **właściwości** folder **Projects\SimpleProject** folderu.  
  
3.  W **Projects\SimpleProject** folderu Dodaj plik XML o nazwie `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  Rozszerzenie nazwy pliku dla wszystkich projektów tego typu jest .myproj. Jeśli chcesz zmienić, należy ją zmienić wszędzie tam, gdzie są one wymienione w tym przewodnikiem.  
  
4.  Zastąp istniejącą zawartość następujące wiersze.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
5.  Zapisz plik.  
  
6.  W **właściwości** ustaw **Akcja kompilacji** AssemblyInfo.cs, plik Program.cs, SimpleProject.ico i SimpleProject.myproj do **zawartości**i ustawić ich  **Uwzględnione w pliku VSIX** właściwości **True**.  
  
 Ten szablon projektu zawiera opis podstawowych Visual C# projekt, który ma konfiguracji debugowania i konfiguracji wydanie. Projekt zawiera pliki źródłowe dwóch AssemblyInfo.cs i Program.cs i kilka zestawów odwołań. Po utworzeniu projektu z szablonu wartość ProjectGuid jest automatycznie zastępowane nowego identyfikatora GUID.  
  
 W **Eksploratora rozwiązań**, rozwinięty **szablony** folderu powinna wyglądać następująco:

```
Templates  
   Projects  
      SimpleProject  
         AssemblyInfo.cs  
         Program.cs  
         SimpleProject.ico  
         SimpleProject.myproj  
```

## <a name="creating-a-basic-project-factory"></a>Tworzenie fabryki podstawowego projektu  
 Visual Studio należy wskazać lokalizację folderu szablonu projektu. Aby to zrobić, należy dodać atrybut do klasy pakiet VSPackage, która implementuje fabrykę projektów, dzięki czemu lokalizacji szablonu jest zapisywany w rejestrze systemu podczas VSPackage jest wbudowana. Rozpocznij od utworzenia fabryki podstawowego projektu, identyfikowany przez identyfikator GUID fabryki projektu. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutu klasy SimpleProjectPackage nawiązać połączenia fabrykę projektów.  
  
#### <a name="to-create-a-basic-project-factory"></a>Można utworzyć fabryki podstawowego projektu  
  
1.  Tworzenie identyfikatorów GUID fabrycznej projektu (na **narzędzia** menu, kliknij przycisk **utworzyć identyfikatora GUID**), lub użyj w poniższym przykładzie. Dodaj identyfikatory GUID do klasy SimpleProjectPackage sekcji z już zdefiniowanym w pobliżu `PackageGuidString`. Identyfikatory GUID musi być zarówno w formie GUID, jak i w postaci ciągu. Wynikowy kod powinien wyglądać następująco.  
  
    ```csharp  
        public sealed class SimpleProjectPackage : Package
        {  
            ...
            public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
            public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
    
            public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);  
        }  
    ```  
  
3.  Dodaj klasę do góry **SimpleProject** folder o nazwie `SimpleProjectFactory.cs`.  
  
4.  Dodaj następujące instrukcje using:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Dodaj atrybut Guid do klasy SimpleProjectFactory. Wartość atrybutu jest nowa fabryka projektu identyfikatora GUID.  
  
    ```csharp  
    [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Możesz teraz zarejestrować szablonu projektu.  
  
#### <a name="to-register-the-project-template"></a>Aby zarejestrować szablonu projektu  
  
1.  W SimpleProjectPackage.cs, Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutu klasy SimpleProjectPackage w następujący sposób.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectPackage.PackageGuidString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Ponownie skompiluj rozwiązanie i sprawdź, czy zbudował bez błędów.  
  
     Ponowne kompilowanie rejestruje szablonu projektu.  
  
 Parametry `defaultProjectExtension` i `possibleProjectExtensions` są ustawione na rozszerzenie nazwy pliku projektu (.myproj). `projectTemplatesDirectory` Parametr jest ustawiony na ścieżkę względną do folderu Szablony. Podczas kompilacji ta ścieżka zostanie przekonwertowany na pełnej kompilacji i dodane w rejestrze zarejestrować system projektu.  
  
## <a name="testing-the-template-registration"></a>Testowanie rejestracji szablonu  
 Szablon rejestracji informuje Visual Studio lokalizacji folderu projektu szablonu, aby Visual Studio można wyświetlić nazwy szablonu i ikonę w **nowy projekt** okno dialogowe.  
  
#### <a name="to-test-the-template-registration"></a>Aby przetestować rejestracji szablonu  
  
1.  Naciśnij klawisz F5, aby rozpocząć debugowanie eksperymentalne wystąpienie programu Visual Studio.  
  
2.  W eksperymentalnym wystąpieniu Utwórz nowy projekt typu z nowo utworzonego projektu. W **nowy projekt** okno dialogowe, powinny pojawić się **SimpleProject** w obszarze **zainstalowane szablony**.  
  
 Teraz masz fabryki projektu, który jest zarejestrowany. Jednak jeszcze nie może utworzyć projekt. Pakiet projektu i projektu fabryki działają razem, Utwórz i zainicjuj projekt.  
  
## <a name="add-the-managed-package-framework-code"></a>Dodaj kod zarządzany Framework pakietu  
 Implementuje połączenie między pakiet projektu i fabryki projektu.  
  
-   Importowanie plików kodu źródłowego dla struktury pakietu zarządzania.  
  
    1.  Zwolnienie projektu SimpleProject (w **Eksploratora rozwiązań**, wybierz węzeł projektu i w menu kontekstowym kliknij **Zwolnij projekt**.), a następnie otwórz plik projektu w edytorze XML.  
  
    2.  Dodaj poniższe bloki do pliku projektu (tylko powyżej \<Import > bloki). Ustaw ProjectBasePath do lokalizacji pliku ProjectBase.files w kod zarządzany Framework pakietu, który został pobrany. Może być konieczne dodanie ukośnik odwrotny do nazwy ścieżki. W przeciwnym razie projekt może nie udało się znaleźć kod zarządzany Framework pakietu.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  Nie zapomnij ukośnikiem na końcu ścieżki.  
  
    3.  Ponownie Załaduj projekt.  
  
    4.  Dodaj odwołania do następujących zestawów:  
  
        -   Microsoft.VisualStudio.Designer.Interfaces (w \<VSSDK instalacji > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Aby zainicjować fabrykę projektów  
  
1.  W pliku SimpleProjectPackage.cs, Dodaj następujący `using` instrukcji.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Pochodzi `SimpleProjectPackage` klasę z `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Zarejestruj fabrykę projektów. Dodaj następujący wiersz do `SimpleProjectPackage.Initialize` metody tuż po `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implementowanie abstrakcyjnych właściwości `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  W SimpleProjectFactory.cs, Dodaj następujący `using` instrukcji po istniejącej `using` instrukcje.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Pochodzi `SimpleProjectFactory` klasę z `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Dodaj następującą metodę zastępczego do `SimpleProjectFactory` klasy. Ta metoda będzie implementowany w dalszej części artykułu.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Dodaj następujące pola i konstruktora `SimpleProjectFactory` klasy. To `SimpleProjectPackage` odwołania są buforowane w pole prywatne, dzięki czemu można ustawić witryna dostawcy usług.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Ponownie skompiluj rozwiązanie i sprawdź, czy zbudował bez błędów.  
  
## <a name="testing-the-project-factory-implementation"></a>Testowanie projektu wdrożenie fabryki  
 Sprawdź, czy wywołania konstruktora fabryki implementacji projektu.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Aby przetestować wdrożenie fabryki projektu  
  
1.  W pliku SimpleProjectFactory.cs Ustaw punkt przerwania w następującym wierszu w `SimpleProjectFactory` konstruktora.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Naciśnij klawisz F5, aby Uruchom eksperymentalne wystąpienie programu Visual Studio.  
  
3.  W eksperymentalnym wystąpieniu Uruchom, aby utworzyć nowy projekt. W **nowy projekt** okno dialogowe, wybierz opcję SimpleProject typ projektu, a następnie kliknij przycisk **OK**. Wykonanie zatrzymuje się na punkt przerwania.  
  
4.  Usuń punkt przerwania i Zatrzymaj debugowanie. Ponieważ węzła projektu nie został jeszcze utworzony, kod tworzenia projektu nadal zgłasza wyjątków.  
  
## <a name="extending-the-project-node-class"></a>Rozszerzenie klasy węzła projektu  
 Teraz można wdrożyć `SimpleProjectNode` klasy, która jest pochodną `ProjectNode` klasy. `ProjectNode` Klasy podstawowej obsługuje następujące zadania tworzenia projektu:  
  
-   Kopiuje plik projektu szablonu SimpleProject.myproj, do nowego folderu projektu. Kopia jest zmieniana zgodnie z nazwą wprowadzoną w **nowy projekt** okno dialogowe. `ProjectGuid` Wartość właściwości zostało zastąpione przez nowy identyfikator GUID.  
  
-   Przechodzi przez elementy programu MSBuild pliku szablonu projektu SimpleProject.myproj oraz szuka `Compile` elementów. Dla każdego `Compile` pliku docelowego, kopiuje plik do nowego folderu projektu.  
  
 Pochodne `SimpleProjectNode` klasa obsługuje te zadania:  
  
-   Włącza ikony w węzłach projektu i pliku **Eksploratora rozwiązań** ma zostać utworzona lub wybrana.  
  
-   Umożliwia podstawienia parametru szablonu projektu dodatkowe należy określić.  
  
#### <a name="to-extend-the-project-node-class"></a>Aby rozszerzyć klasy węzła projektu  
  
1.  
  
2.  Dodaj klasę o nazwie `SimpleProjectNode.cs`.  
  
3.  Zastąp istniejący kod następującym kodem.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Project;  
  
    namespace SimpleProject  
    {  
        public class SimpleProjectNode : ProjectNode  
        {  
            private SimpleProjectPackage package;  
  
            public SimpleProjectNode(SimpleProjectPackage package)  
            {  
                this.package = package;  
            }  
            public override Guid ProjectGuid  
            {  
                get { return SimpleProjectPackage.guidSimpleProjectFactory; }  
            }  
            public override string ProjectType  
            {  
                get { return "SimpleProjectType"; }  
            }  
  
            public override void AddFileFromTemplate(  
                string source, string target)  
            {  
                this.FileTemplateProcessor.UntokenFile(source, target);  
                this.FileTemplateProcessor.Reset();  
            }  
        }  
    }  
    ```  
  
 To `SimpleProjectNode` te przesłoniętej metody ma implementację klasy:  
  
-   `ProjectGuid`, która zwraca GUID fabryki projektu.  
  
-   `ProjectType`, która zwraca zlokalizowana nazwa typu projektu.  
  
-   `AddFileFromTemplate`, które kopiuje wybrane pliki w folderze szablonów do projektu docelowego. Ta metoda jest dalsze zaimplementowana w dalszej części artykułu.  
  
 `SimpleProjectNode` Konstruktora, takiej jak `SimpleProjectFactory` buforuje konstruktora, `SimpleProjectPackage` odwołania w pole prywatne do późniejszego użycia.  
  
 Aby połączyć `SimpleProjectFactory` klasa do `SimpleProjectNode` klasy, trzeba utworzyć wystąpienie nowego `SimpleProjectNode` w `SimpleProjectFactory.CreateProject` — metoda i pamięć podręczna go w pole prywatne do późniejszego użycia.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Nawiązywanie połączenia klasę fabryki projektu i klasa węzła  
  
1.  W pliku SimpleProjectFactory.cs, Dodaj następujący `using` instrukcji:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Zastąp `SimpleProjectFactory.CreateProject` metody przy użyciu następującego kodu.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Ponownie skompiluj rozwiązanie i sprawdź, czy zbudował bez błędów.  
  
## <a name="testing-the-project-node-class"></a>Testowanie klasa węzła projektu  
 Przetestuj fabryką projektu, aby zobaczyć, czy tworzy hierarchii projektu.  
  
#### <a name="to-test-the-project-node-class"></a>Aby przetestować klasa węzła projektu  
  
1.  Naciśnij klawisz F5, aby rozpocząć debugowania. W eksperymentalnym wystąpieniu Utwórz nowe SimpleProject.  
  
2.  Visual Studio powinny wywoływać fabryką projektu do tworzenia projektu.  
  
3.  Zamknij eksperymentalne wystąpienie programu Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Dodawanie ikony węzła projektu niestandardowych  
 Ikona węzła projektu w we wcześniejszej sekcji jest ikona domyślna. Można go zmienić na ikoną niestandardową.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Aby dodać ikony węzła projektu niestandardowych  
  
1.  W **zasobów** folderu, Dodaj plik mapy bitowej o nazwie SimpleProjectNode.bmp.  
  
2.  W **właściwości** systemu windows, Zmniejsz mapy bitowej do 16 na 16 pikseli. Należy charakterystyczne mapy bitowej.  
  
     ![Simple Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  W **właściwości** Zmień **Akcja kompilacji** mapy bitowej do **osadzonego zasobu**.  
  
4.  W SimpleProjectNode.cs, Dodaj następujący `using` instrukcji:  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Dodaj następujące pola statyczne i konstruktora `SimpleProjectNode` klasy.  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Dodaj następujące właściwości na początku `SimpleProjectNode` klasy.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Zastąp następujący kod konstruktora wystąpienia.  
  
    ```  
    public SimpleProjectNode(SimpleProjectPackage package)  
    {  
        this.package = package;  
  
        imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
        foreach (Image img in imageList.Images)  
        {  
            this.ImageHandler.AddImage(img);  
        }  
    }  
    ```  
  
 Podczas konstruowania statycznych `SimpleProjectNode` pobiera mapy bitowej węzła projektu z zasobów manifestu zestawu i buforuje ją w pole prywatne do późniejszego użycia. Zwróć uwagę, składnia <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ścieżkę obrazu. Aby wyświetlić nazwy manifestu zasoby osadzone w zestawie, należy użyć <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metody. Gdy ta metoda jest stosowany do `SimpleProject` zestawu wyników powinna być następująca:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Podczas konstruowania wystąpienia `ProjectNode` Resources.imagelis.bmp, w którym są osadzone często używane bitmapy 16 x 16 z Resources\imagelis.bmp ładuje klasy podstawowej. Ta lista mapa bitowa ma zostać udostępnione `SimpleProjectNode` jako ImageHandler.ImageList. `SimpleProjectNode` dołącza mapy bitowej węzła projektu do listy. Przesunięcie mapy bitowej węzła projektu na liście obrazów jest buforowana do późniejszego użytku jako wartość publicznego `ImageIndex` właściwości. Visual Studio używa tej właściwości, aby określić, które mapy bitowej do wyświetlenia jako ikonę węzła projektu.  
  
## <a name="testing-the-custom-project-node-icon"></a>Testowanie ikony węzła projektu niestandardowych  
 Przetestuj fabryką projektu, aby zobaczyć, czy tworzy hierarchii projektu jako ikony węzła projektu niestandardowych.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Aby przetestować ikony węzła projektu niestandardowych  
  
1.  Rozpocznij debugowanie, a w eksperymentalnym wystąpieniu Utwórz nowe SimpleProject.  
  
2.  Nowo utworzonego projektu Zwróć uwagę, że SimpleProjectNode.bmp jest używana jako ikony węzła projektu.  
  
     ![Proste projektu nowego projektu węzła](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Otwórz plik Program.cs w edytorze kodu. Powinien zostać wyświetlony kod źródłowy, podobny do następującego kodu.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Zwróć uwagę, parametry szablonu $nameSpace$ i $className$ nie mają nowe wartości. Dowiesz się implementowania zamienny parametr szablonu w następnej sekcji.  
  
## <a name="substituting-template-parameters"></a>Zastępowanie parametrów szablonu  
 W sekcji wcześniej został zarejestrowany szablonu projektu z programem Visual Studio przy użyciu `ProvideProjectFactory` atrybutu. Rejestrowanie ścieżkę folderu szablonu w ten sposób umożliwia zamienny parametr szablonu podstawowego zastępowanie i rozwijając `ProjectNode.AddFileFromTemplate` klasy. Aby uzyskać więcej informacji, zobacz [nowej generacji projektu: pod maską, dwie części](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Teraz Dodaj kod zastępczy `AddFileFromTemplate` klasy.  
  
#### <a name="to-substitute-template-parameters"></a>Aby zastąpić parametrów szablonu  
  
1.  W pliku SimpleProjectNode.cs, Dodaj następujący `using` instrukcji.  
  
    ```  
    using System.IO;  
    ```  
  
2.  Zastąp `AddFileFromTemplate` metody przy użyciu następującego kodu.  
  
    ```  
    public override void AddFileFromTemplate(  
        string source, string target)  
    {  
        string nameSpace =   
            this.FileTemplateProcessor.GetFileNamespace(target, this);  
        string className = Path.GetFileNameWithoutExtension(target);  
  
        this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
        this.FileTemplateProcessor.AddReplace("$className$", className);  
  
        this.FileTemplateProcessor.UntokenFile(source, target);  
        this.FileTemplateProcessor.Reset();  
    }  
    ```  
  
3.  Ustaw punkt przerwania w metodzie zaraz po `className` instrukcji przypisania.  
  
 Instrukcje przypisania określania rozsądne wartości dla przestrzeni nazw i nazwy klasy. Dwa `ProjectNode.FileTemplateProcessor.AddReplace` wywołania metody zastępowanie odpowiednie wartości parametrów szablonu przy użyciu tych nowych wartości.  
  
## <a name="testing-the-template-parameter-substitution"></a>Testowanie zamienny parametr szablonu  
 Teraz możesz przetestować zamienny parametr szablonu.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Aby przetestować zamienny parametr szablonu  
  
1.  Rozpocznij debugowanie, a w eksperymentalnym wystąpieniu Utwórz nowe SimpleProject.  
  
2.  Wykonanie zatrzymuje się na punkt przerwania w `AddFileFromTemplate` metody.  
  
3.  Sprawdź wartości `nameSpace` i `className` parametrów.  
  
    -   `nameSpace` podano wartość \<RootNamespace > w pliku szablonu projektu \Templates\Projects\SimpleProject\SimpleProject.myproj. W takim przypadku wartość to "MyRootNamespace".  
  
    -   `className` podano wartość Nazwa klasy źródła pliku bez rozszerzenia nazwy pliku. W tym przypadku jest to plik ma zostać skopiowany do folderu docelowego AssemblyInfo.cs; w związku z tym wartość className jest "AssemblyInfo".  
  
4.  Usuń punkt przerwania, a następnie naciśnij klawisz F5, aby kontynuować działanie.  
  
     Visual Studio należy zakończyć tworzenia projektu.  
  
5.  Otwórz plik Program.cs w edytorze kodu. Powinien zostać wyświetlony kod źródłowy, podobny do następującego kodu.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace MyRootNamespace  
    {  
        public class Program  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Zwróć uwagę, że przestrzeń nazw jest teraz "MyRootNamespace", a nazwa klasy jest teraz "Program".  
  
6.  Rozpocznij debugowanie projektu. Nowy projekt należy skompilować, uruchom i wyświetlić "tekst Hello VSX"! w oknie konsoli.  
  
     ![Polecenie prostego projektu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Gratulacje! Wdrożono system podstawowych zarządzanego projektu.