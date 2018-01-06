---
title: "Tworzenie systemu podstawowego projektu, część 2 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9b3f46a0e4fb87e6064fb3e975cd6b7313270c13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-basic-project-system-part-2"></a>Tworzenie systemu podstawowego projektu, część 2
Pierwszy wskazówki w tej serii [tworzenia podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md), pokazuje, jak utworzyć podstawowy projekt systemu. W tym przewodniku opiera się na system podstawowych projektów przez dodanie szablonu Visual Studio, strony właściwości i inne funkcje. Pierwszy wskazówki należy wykonać przed rozpoczęciem tego.  
  
 W tym przewodniku pokazuje sposób tworzenia typem projektu, który ma .myproj rozszerzenia nazwy pliku projektu. Aby ukończyć przewodnika, nie masz do tworzenia własnych języka, ponieważ wskazówki obiektowy istniejącego systemu projektów Visual C#.  
  
 Ten przewodnik zawiera instrukcje wykonać te zadania:  
  
-   Tworzenie szablonu programu Visual Studio.  
  
-   Wdrażanie szablonu Visual Studio.  
  
-   Utwórz węzeł podrzędny typu projektu w **nowy projekt** okno dialogowe.  
  
-   Włącz zamienny parametr szablonu Visual Studio.  
  
-   Utwórz stronę właściwości projektu.  
  
> [!NOTE]
>  Kroki opisane w tym przewodniku są oparte na projektu C#. Jednak z wyjątkiem szczegóły, takie jak rozszerzeń nazw plików i kod, można użyć te same kroki dla projektu Visual Basic.  
  
## <a name="creating-a-visual-studio-template"></a>Tworzenie szablonu programu Visual Studio  
 [Tworzenie podstawowych System projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md) pokazano, jak utworzyć szablon projektu podstawowych i dodaj go do systemu projektu. Przedstawiono również sposób rejestrowania tego szablonu przy użyciu programu Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybut, który zapisuje pełną ścieżkę do folderu \Templates\Projects\SimpleProject\ w rejestrze systemu.  
  
 Za pomocą szablonu Visual Studio (plik .vstemplate) zamiast szablonu projektu podstawowych, można kontrolować sposób wyświetlania szablonu **nowy projekt** okno dialogowe i jak mają być zastępowane parametrów szablonu.  Plik .vstemplate jest plik XML, który opisuje, jak są pliki źródłowe do uwzględnienia podczas tworzenia projektu za pomocą szablonu projektu systemu. System projektu jest utworzony przez pobierania pliku .vstemplate i plików źródłowych w pliku .zip i wdrażane przez skopiowanie pliku zip do lokalizacji, która jest znany dla programu Visual Studio. Ten proces jest szczegółowo w dalszej części tego przewodnika.  
  
1.  W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz rozwiązanie SimpleProject, który został utworzony przez następujące [tworzenia podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2.  W pliku SimpleProjectPackage.cs znajduje się atrybut ProvideProjectFactory. Zamień na drugi parametr (nazwa projektu) z wartością null, a parametr czwarty (ścieżka do folderu szablon projektu) ". \\\NullPath ", wykonując następujące czynności.  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
        ".\\NullPath",  
    LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  Dodaj plik XML o nazwie SimpleProject.vstemplate do folderu \Templates\Projects\SimpleProject\.  
  
4.  Zastąp zawartość SimpleProject.vstemplate z następującym kodem.  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
      <TemplateData>  
        <Name>SimpleProject Application</Name>  
        <Description>  
            A project for creating a SimpleProject application  
         </Description>  
         <Icon>SimpleProject.ico</Icon>  
         <ProjectType>SimpleProject</ProjectType>  
      </TemplateData>  
      <TemplateContent>  
        <Project File="SimpleProject.myproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
              Program.cs  
          </ProjectItem>  
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
             AssemblyInfo.cs  
          </ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
5.  W **właściwości** okna, wybierz pięciu wszystkie pliki w folderze \Templates\Projects\SimpleProject\ i zestaw **Akcja kompilacji** do **ZipProject**.  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 \<TemplateData > sekcji określa lokalizację i wyglądu SimpleProject typu projektu w **nowy projekt** okno dialogowe, w następujący sposób:  
  
-   \<Name > szablon projektu był aplikacji SimpleProject nazwy elementu.  
  
-   \<Opis > element zawiera opis wyświetlany w **nowy projekt** okno dialogowe, w przypadku wybrania szablonu projektu.  
  
-   \<Ikona > element Określa ikonę, która pojawia się wraz z SimpleProject typu projektu.  
  
-   \<ProjectType > typ projektu w nazwy elementu **nowy projekt** okno dialogowe. Ta nazwa zastępuje atrybutu ProvideProjectFactory parametr nazwy projektu.  
  
    > [!NOTE]
    >  \<ProjectType > musi być zgodny element `LanguageVsTemplate` argument `ProvideProjectFactory` atrybutu w pliku SimpleProjectPackage.cs.  
  
 \<TemplateContent > sekcji opisano te pliki, które są generowane podczas tworzenia nowego projektu:  
  
-   SimpleProject.myproj  
  
-   Plik program.CS  
  
-   AssemblyInfo.cs  
  
 Wszystkie trzy pliki mają `ReplaceParameters` wartość true, dzięki czemu podstawienia parametru.  Nazwa pliku Program.cs `OpenInEditor` wartość true, co powoduje, że plik ma zostać otwarty w edytorze kodu podczas tworzenia projektu.  
  
 Aby uzyskać więcej informacji na temat elementy w schemacie szablon programu Visual Studio, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Jeśli projekt zawiera więcej niż jeden szablon programu Visual Studio, co szablon jest w oddzielnym folderze. Każdy plik w tym folderze musi mieć **Akcja kompilacji** ustawioną **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Dodawanie pliku vsct minimalnego  
 Visual Studio musi być uruchamiana w trybie instalacji rozpoznać nowe lub zmodyfikowane szablonu Visual Studio. Tryb instalacji wymaga obecności pliku vsct. W związku z tym należy dodać pliku vsct minimalnego do projektu.  
  
1.  Dodaj plik XML o nazwie SimpleProject.vsct do projektu SimpleProject.  
  
2.  Zastąp zawartość pliku SimpleProject.vsct następującym kodem.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Ustaw **Akcja kompilacji** tego pliku do **VSCTCompile**. Można to zrobić tylko w pliku .csproj nie w **właściwości** okna. Upewnij się, że **Akcja kompilacji** ten plik jest ustawiony na wartość **Brak** w tym momencie.  
  
    1.  Kliknij prawym przyciskiem myszy węzeł SimpleProject, a następnie kliknij przycisk **Edytuj SimpleProject.csproj**.  
  
    2.  W pliku .csproj zlokalizuj element SimpleProject.vsct.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Zmiany akcji kompilacji na **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  plik projektu i zamknij Edytor.  
  
    5.  Zapisz węzła SimpleProject, a następnie w **Eksploratora rozwiązań** kliknij **Załaduj ponownie projekt**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Badanie kroki procesu kompilacji dla szablonu programu Visual Studio  
 System kompilacji projektu pakiet VSPackage zwykle uruchamia programu Visual Studio w trybie instalacji zostanie zmieniony plik .vstemplate lub projektu, który zawiera plik .vstemplate zostanie odtworzony. Możesz kontynuować pracę, ustawiając poziom szczegółowości programu MSBuild na normalny lub nowszej.  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  Rozwiń węzeł **projekty i rozwiązania** węzeł, a następnie wybierz **skompilować i uruchomić**.  
  
3.  Ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny**. Kliknij przycisk **OK**.  
  
4.  Skompiluj ponownie projekt SimpleProject.  
  
 Kroku kompilacji, aby utworzyć plik zip projektu powinien wyglądać następująco.  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploying-a-visual-studio-template"></a>Wdrażanie szablonu programu Visual Studio  
 Szablony Visual Studio nie zawierają informacje o ścieżce. W związku z tym należy wdrożyć szablon pliku zip do lokalizacji, która jest znany dla programu Visual Studio. Lokalizacja folderu ProjectTemplates jest zwykle  **\<LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Aby wdrożyć fabryką projektu, program instalacyjny musi mieć uprawnienia administratora. Wdrażania szablonów w węźle instalacji programu Visual Studio: **14.0\Common7\IDE\ProjectTemplates programu Visual Studio ...\Microsoft**.  
  
## <a name="testing-a-visual-studio-template"></a>Testowanie szablon programu Visual Studio  
 Przetestuj fabryką projektu, aby zobaczyć, czy tworzy hierarchii projektu przy użyciu szablonu z programu Visual Studio.  
  
1.  Zresetuj eksperymentalne wystąpienie programu Visual Studio SDK.  
  
     Na [!INCLUDE[win7](../debugger/includes/win7_md.md)]: W Start menu znaleźć **Microsoft Visual Studio/Microsoft Visual Studio SDK/narzędzia** folder, a następnie wybierz **Zresetuj Microsoft Visual Studio eksperymentalne wystąpienie programu**.  
  
     W nowszych wersjach systemu Windows: na stronie Start ekranu, typ **zresetować programu Microsoft Visual Studio \<wersji > eksperymentalne wystąpienie**.  
  
2.  Zostanie wyświetlone okno wiersza polecenia. Po wyświetleniu słowa `Press any key to continue`, naciśnij klawisz ENTER. Po zamknięciu okna, Otwórz program Visual Studio.  
  
3.  Skompiluj ponownie projekt SimpleProject i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
4.  W eksperymentalnym wystąpieniu Utwórz projekt SimpleProject. W **nowy projekt** okno dialogowe, wybierz opcję **SimpleProject**.  
  
5.  Nowe wystąpienie klasy SimpleProject powinna zostać wyświetlona.  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Tworzenie projektu typu węzła podrzędnego  
 Można dodać węzła podrzędnego w węźle typu projektu **nowy projekt** okno dialogowe.  Na przykład dla typu projektu SimpleProject, może mieć węzłów podrzędnych aplikacji konsoli, okna aplikacji, aplikacji sieci web, i tak dalej.  
  
 Węzły podrzędne są tworzone przez zmianę pliku projektu i dodawanie \<OutputSubPath > dzieci \<ZipProject > elementów. Po skopiowaniu szablonu podczas kompilacji lub wdrożenia każdego węzła podrzędnego staje się podfolder folderu szablonów projektu.  
  
 W tej sekcji przedstawiono sposób tworzenia elementem podrzędnym konsoli SimpleProject typu projektu.  
  
1.  Zmień nazwę folderu \Templates\Projects\SimpleProject\ na \Templates\Projects\ConsoleApp\\.  
  
2.  W **właściwości** okna, wybierz wszystkie pięć plików w folderze \Templates\Projects\ConsoleApp\ i upewnij się, że **Akcja kompilacji** ustawiono **ZipProject**.  
  
3.  W pliku SimpleProject.vstemplate, Dodaj następujący wiersz na końcu \<TemplateData > sekcji, bezpośrednio przed tagu zamykającego.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Powoduje to, że szablon aplikacji konsoli jest wyświetlany zarówno w konsoli węzła podrzędnego w SimpleProject węzła nadrzędnego, który jest o jeden poziom wyżej węzeł podrzędny.  
  
4.  Zapisz plik SimpleProject.vstemplate.  
  
5.  W pliku .csproj dodać \<OutputSubPath > do poszczególnych elementów ZipProject. Zwolnienie projektu, jak wcześniej i edytowania pliku projektu.  
  
6.  Zlokalizuj \<ZipProject > elementów. Do każdego \<ZipProject > elementu, Dodaj \<OutputSubPath > element i nadaj mu wartość konsoli. ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  Dodaj tę \<PropertyGroup > do pliku projektu:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  Zapisz plik projektu i ponownie Załaduj projekt.  
  
## <a name="testing-the-project-type-child-node"></a>Testowanie węzeł podrzędny typu projektu  
 Testowanie pliku projektu zmodyfikowane, aby zobaczyć, czy **konsoli** węzła podrzędnego pojawia się w **nowy projekt** okno dialogowe.  
  
1.  Uruchom **Zresetuj Microsoft Visual Studio eksperymentalne wystąpienie programu** narzędzia.  
  
2.  Skompiluj ponownie projekt SimpleProject i Rozpocznij debugowanie. Powinna zostać wyświetlona eksperymentalne wystąpienie programu  
  
3.  W **nowy projekt** okna dialogowego, kliknij przycisk **SimpleProject** węzła. **Aplikacji konsoli** szablon powinien zostać wyświetlony w **szablony** okienka.  
  
4.  Rozwiń węzeł **SimpleProject** węzła. **Konsoli** węzła podrzędnego powinna zostać wyświetlona. **Aplikacji SimpleProject** szablon będzie wyświetlany w **szablony** okienka.  
  
5.  . Kliknij przycisk **anulować** i Zatrzymaj debugowanie  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Zastępowanie parametrów szablonu projektu  
 [Tworzenie podstawowych System projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md) pokazano, jak zastąpić `ProjectNode.AddFileFromTemplate` metodę, aby wykonać podstawowe rodzaj zamienny parametr szablonu. Ta sekcja zawiera sposób użycia dokładniejsze parametrów szablonu Visual Studio.  
  
 Podczas tworzenia projektu za pomocą szablonu Visual Studio w **nowy projekt** okno dialogowe ciągi są zamieniane na parametry szablonu, aby dostosować projekt. Parametr szablonu to specjalne token, który rozpoczyna się i kończy się znakiem dolara ($), na przykład $time$. Następujące dwa parametry są szczególnie przydatne w przypadku włączania dostosowania w projektach, które są oparte na szablonie:  
  
-   $ $GUID [1 – 10] zastępuje nowego identyfikatora Guid. Można określić maksymalnie 10 unikatowy GUID, na przykład $guid1$.  
  
-   $safeprojectname$ to nazwa podana przez użytkownika w **nowy projekt** okno dialogowe, zmodyfikowane w celu usunięcia wszystkich znaków niebezpieczne i spacje.  
  
 Aby uzyskać pełną listę parametrów szablonu, zobacz [parametrów szablonu](../ide/template-parameters.md).  Jeśli chcesz utworzyć parametru szablonu niestandardowego, zobacz [NIB: porady: przekazywanie niestandardowych parametrów szablonów](http://msdn.microsoft.com/en-us/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### <a name="to-substitute-project-template-parameters"></a>Aby zastąpić parametrów szablonu projektu  
  
1.  W pliku SimpleProjectNode.cs Usuń `AddFileFromTemplate` metody.  
  
2.  W pliku \Templates\Projects\ConsoleApp\SimpleProject.myproj Znajdź \<RootNamespace > właściwości i zmień wartość na $safeprojectname$.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  W pliku \Templates\Projects\SimpleProject\Program.cs Zastąp zawartość pliku następującym kodem:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  Skompiluj ponownie projekt SimpleProject i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
5.  Utwórz nową aplikację konsoli SimpleProject. (W **typy projektów** okienku wybierz **SimpleProject**. W obszarze **zainstalowane szablony Visual Studio**, wybierz pozycję **aplikacji konsoli**.)  
  
6.  W nowo utworzonego projektu otwórz plik Program.cs. Powinien on wyglądać podobnie do następującej (wartości identyfikatora GUID w pliku będą się różnić.):  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creating-a-project-property-page"></a>Tworzenie strony właściwości projektu  
 Można utworzyć strony właściwości dla danego typu projektu, dzięki czemu użytkownicy mogą wyświetlać i zmieniać właściwości w projektach, które są oparte na szablonie. W tej sekcji przedstawiono sposób tworzenia strony właściwości niezależny od konfiguracji. Tej strony właściwości podstawowych używa siatki właściwości, aby wyświetlić właściwości publiczne, których udostępniono w Twojej klasy strony właściwości.  
  
 Pochodzi z klasy strony właściwości `SettingsPage` klasy podstawowej. Siatki właściwości udostępniane przez `SettingsPage` klasy zna najbardziej pierwotne typy danych i sposób ich wyświetlania.  Ponadto `SettingsPage` klasy potrafi zachować wartości właściwości do pliku projektu.  
  
 Strony właściwości utworzone w tej sekcji pozwala zmienić i zapisać te właściwości projektu:  
  
-   AssemblyName  
  
-   Atrybut OutputType  
  
-   RootNamespace.  
  
1.  W pliku SimpleProjectPackage.cs dodać `ProvideObject` atrybutu `SimpleProjectPackage` klasy:  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))]  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     Rejestruje to klasy strony właściwości `GeneralPropertyPage` z modelu COM.  
  
2.  W pliku SimpleProjectNode.cs, Dodaj te dwie metody przesłoniętych `SimpleProjectNode` klasy:  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
    }  
    protected override Guid[] GetPriorityProjectDesignerPages()  
    {  
        Guid[] result = new Guid[1];  
        result[0] = typeof(GeneralPropertyPage).GUID;  
         return result;  
    }  
    ```  
  
     Obie te metody zwracają tablicę strony właściwości GUID.  Identyfikator GUID GeneralPropertyPage jest tylko element w tablicy, więc **strony właściwości** zostanie wyświetlone okno dialogowe tylko jedną stronę.  
  
3.  Dodaj plik klasy o nazwie GeneralPropertyPage.cs do projektu SimpleProject.  
  
4.  Zastąp zawartość tego pliku, używając następującego kodu:  
  
    ```  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Project;  
    using System.ComponentModel;  
  
    namespace SimpleProject  
    {  
        [ComVisible(true)]  
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
        public class GeneralPropertyPage : SettingsPage  
        {  
            private string assemblyName;  
            private OutputType outputType;  
            private string defaultNamespace;  
  
            public GeneralPropertyPage()  
            {  
                this.Name = "General";  
            }  
  
            [Category("AssemblyName")]  
            [DisplayName("AssemblyName")]  
            [Description("The output file holding assembly metadata.")]  
            public string AssemblyName  
            {  
                get { return this.assemblyName; }  
            }  
            [Category("Application")]  
            [DisplayName("OutputType")]  
            [Description("The type of application to build.")]  
            public OutputType OutputType  
            {  
                get { return this.outputType; }  
                set { this.outputType = value; this.IsDirty = true; }  
            }  
            [Category("Application")]  
            [DisplayName("DefaultNamespace")]  
            [Description("Specifies the default namespace for added items.")]  
            public string DefaultNamespace  
            {  
                get { return this.defaultNamespace; }  
                set { this.defaultNamespace = value; this.IsDirty = true; }  
            }  
  
            protected override void BindProperties()  
            {  
                this.assemblyName = this.ProjectMgr.GetProjectProperty(  
    "AssemblyName", true);  
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
    "RootNamespace", false);  
  
                string outputType = this.ProjectMgr.GetProjectProperty(  
    "OutputType", false);  
                this.outputType =   
    (OutputType)Enum.Parse(typeof(OutputType), outputType);  
            }  
  
            protected override int ApplyChanges()  
            {  
                this.ProjectMgr.SetProjectProperty(  
    "AssemblyName", this.assemblyName);  
                this.ProjectMgr.SetProjectProperty(  
    "OutputType", this.outputType.ToString());  
                this.ProjectMgr.SetProjectProperty(  
    "RootNamespace", this.defaultNamespace);  
                this.IsDirty = false;  
  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    ```  
  
     `GeneralPropertyPage` Klasa udostępnia trzy właściwości publiczne AssemblyName, OutputType i RootNamespace. Ponieważ AssemblyName nie ma zestawu metody, jest on wyświetlany jako właściwość tylko do odczytu. Atrybut OutputType jest wyliczany stała jest widoczny jako listy rozwijanej.  
  
     `SettingsPage` Udostępnia klasę podstawową `ProjectMgr` utrwalić właściwości. `BindProperties` Używa metody `ProjectMgr` można pobrać wartości właściwości trwałych i ustaw odpowiednie właściwości.  `ApplyChanges` Używa metody `ProjectMgr` do pobrania wartości właściwości i utrwalić je do pliku projektu. Właściwość set Ustawia metodę `IsDirty` wartość "prawda" oznacza, że właściwości mieć utrwalenia.  Trwałość występuje, gdy zapiszesz projekt lub rozwiązanie.  
  
5.  Ponownie skompiluj rozwiązanie SimpleProject i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
6.  W eksperymentalnym wystąpieniu Utwórz nową aplikację SimpleProject.  
  
7.  Visual Studio wymaga fabryką projektu do tworzenia projektu za pomocą szablonu Visual Studio. Nowy plik Program.cs jest otwarty w edytorze kodu.  
  
8.  Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**, a następnie kliknij przycisk **właściwości**. **Strony właściwości** zostanie wyświetlone okno dialogowe.  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Testowanie strony właściwości projektu  
 Teraz można sprawdzić, czy można zmodyfikować, a zmiany wartości właściwości.  
  
1.  W **strony właściwości MyConsoleApplication** okno dialogowe, zmień **DefaultNamespace** do **MyApplication**.  
  
2.  Wybierz **OutputType** właściwości, a następnie wybierz **biblioteki klas**.  
  
3.  Kliknij przycisk **Zastosuj**, a następnie kliknij przycisk **OK**.  
  
4.  Otwórz ponownie **strony właściwości** okna dialogowego i zweryfikować, że zmiany zostały utrwalone.  
  
5.  Zamknij eksperymentalne wystąpienie programu Visual Studio.  
  
6.  Otwórz ponownie eksperymentalne wystąpienie.  
  
7.  Otwórz ponownie **strony właściwości** okna dialogowego i zweryfikować, że zmiany zostały utrwalone.  
  
8.  Zamknij eksperymentalne wystąpienie programu Visual Studio.  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")