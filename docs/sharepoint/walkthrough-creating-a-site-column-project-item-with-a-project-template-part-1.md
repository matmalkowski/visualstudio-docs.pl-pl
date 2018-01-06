---
title: "Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 05a0f2a997791564a8358287ff1d632c3ff7bffe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1"></a>Wskazówki: tworzenie elementu projektu kolumn witryny z Szablonem projektu, Część 1
  SharePoint — projekty są kontenerami dla jednego lub więcej elementów projektu programu SharePoint. System projektu programu SharePoint w Visual Studio można rozszerzyć przez utworzenie własnych typów elementów projektu SharePoint i kojarzenie je za pomocą szablonu projektu. W tym przewodniku określi typu elementu projektu do tworzenia kolumny witryny, a następnie zostanie utworzony szablon projektu, który może służyć do tworzenia nowego projektu, który zawiera elementu projektu kolumn witryny.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie rozszerzenia programu Visual Studio, który definiuje nowy typ elementu projektu SharePoint dla kolumny witryny. Typ elementu projektu zawiera proste właściwości niestandardowej, która jest wyświetlana w **właściwości** okna.  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] szablon projektu do elementu projektu.  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) do wdrożenia szablonu projektu i zestawu rozszerzenia.  
  
-   Debugowanie i testowanie elementu projektu.  
  
 Jest to autonomiczny wskazówki. Po ukończeniu tego przewodnika, można zwiększyć przez dodanie kreatora do szablonu projektu elementu projektu. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
>  Możesz pobrać przykład, który zawiera projekty ukończone, kodu i innych plików w ramach tego przewodnika z następującej lokalizacji: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Microsoft Windows SharePoint i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrażania elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Kolumny witryny w programie SharePoint. Aby uzyskać więcej informacji, zobacz [kolumn](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
-   Szablony projektów programu Visual Studio. Aby uzyskać więcej informacji, zobacz [szablony tworzenie projektów i elementów](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
 W tym przewodniku, należy utworzyć trzy projekty:  
  
-   Projekt VSIX. Ten projekt tworzy pakiet VSIX do wdrażania elementu projektu kolumn witryny i szablon projektu.  
  
-   Projekt szablonu projektu. Ten projekt tworzy szablon projektu, który może służyć do Utwórz nowy projekt programu SharePoint, która zawiera elementu projektu kolumn witryny.  
  
-   Projektu biblioteki klas. Ten projekt, który implementuje rozszerzenie programu Visual Studio, który definiuje zachowanie elementu projektu kolumn witryny.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
3.  W górnej części **nowy projekt** okna dialogowego upewnij się, że **.NET Framework 4.5** jest wybrane na liście wersji programu .NET Framework.  
  
4.  Rozwiń węzeł **Visual Basic** lub **Visual C#** węzłów, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne wcześniej w tym temacie.  
  
5.  Na liście szablony projektów, wybierz **projektu VSIX**.  
  
6.  W **nazwa** wprowadź **SiteColumnProjectItem**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **SiteColumnProjectItem** projektu do **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-project-template-project"></a>Aby utworzyć projekt szablonu projektu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W górnej części **nowy projekt** okna dialogowego upewnij się, że **.NET Framework 4.5** jest wybrane na liście wersji programu .NET Framework.  
  
3.  Rozwiń węzeł **Visual C#** lub **Visual Basic** węzeł, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
4.  Na liście szablony projektów, wybierz **szablonu projektu C#** lub **szablon projektu Visual Basic** szablonu.  
  
5.  W **nazwa** wprowadź **SiteColumnProjectTemplate**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **SiteColumnProjectTemplate** projektu do rozwiązania.  
  
6.  Usuń plik kodu Class1 z projektu.  
  
7.  Jeśli utworzono projekt Visual Basic, Usuń również następujące pliki z projektu:  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.Settings  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W górnej części **nowy projekt** okna dialogowego upewnij się, że **.NET Framework 4.5** jest wybrane na liście wersji programu .NET Framework.  
  
3.  Rozwiń węzeł **Visual C#** lub **Visual Basic** węzłów, wybierz **Windows** węzła, a następnie wybierz pozycję **biblioteki klas** szablonu.  
  
4.  W **nazwa** wprowadź **ProjectItemTypeDefinition** , a następnie wybierz **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **ProjectItemTypeDefinition** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configuring-the-extension-project"></a>Konfigurowanie projekt rozszerzenia  
 Dodawanie plików kodu i odwołania do zestawów, aby skonfigurować projekt rozszerzenia.  
  
#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt  
  
1.  W projekcie ProjectItemTypeDefinition dodać plik kodu o nazwie **SiteColumnProjectItemTypeProvider**.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
3.  W **Menedżera odwołań - ProjectItemTypeDefinition** okna dialogowego rozwiń **zestawy** węzła, wybierz **Framework** węzeł, a następnie wybierz Pole wyboru System.ComponentModel.Composition.  
  
4.  Wybierz **rozszerzenia** węzła, zaznacz pole wyboru obok zestawu Microsoft.VisualStudio.SharePoint, a następnie wybierz **OK** przycisku.  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>Definiowanie nowy typ elementu projektu SharePoint  
 Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu Definiowanie zachowania nowy typ elementu projektu. Zawsze, gdy chcesz zdefiniować nowy typ elementu projektu, należy zaimplementować ten interfejs.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Aby określić nowy typ elementu projektu SharePoint  
  
1.  W **SiteColumnProjectItemTypeProvider** code pliku, Zastąp następujący kod w kodzie domyślnym, a następnie zapisz plik.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="creating-a-visual-studio-project-template"></a>Tworzenie szablonu projektu programu Visual Studio  
 Tworząc szablon projektu umożliwia innych deweloperom tworzenie SharePoint — projekty zawierające elementy projektu kolumn witryny. Szablon projektu programu SharePoint obejmuje pliki, które są wymagane dla wszystkich projektów w programie Visual Studio, takich jak .csproj lub .vbproj i .vstemplate — pliki i pliki, które są specyficzne dla projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 W tej procedurze utworzysz pusty projekt SharePoint generuje pliki, które są specyficzne dla SharePoint — projekty. Te pliki można następnie dodać do projektu SiteColumnProjectTemplate, dzięki czemu są one dołączone do szablonu, który jest generowany na podstawie tego projektu. Możesz również skonfigurować plik projektu SiteColumnProjectTemplate, aby określić, gdzie szablon projektu jest wyświetlany w **nowy projekt** okno dialogowe.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>Aby utworzyć pliki szablonu projektu  
  
1.  Uruchom drugie wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu poświadczeń administracyjnych.  
  
2.  Tworzenie projektu programu SharePoint 2010 o nazwie **BaseSharePointProject**.  
  
    > [!IMPORTANT]  
    >  W **Kreator dostosowania programu SharePoint**, nie należy wybierać **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
3.  Dodawanie elementu pustego elementu do projektu, a następnie nazwą elementu **pole1**.  
  
4.  Zapisz projekt, a następnie zamknij drugie wystąpienie parametru [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5.  W wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem Otwórz rozwiązanie, które ma w **Eksploratora rozwiązań**, otwórz menu skrótów **SiteColumnProjectTemplate** węzła projektu, wybierz  **Dodaj**, a następnie wybierz pozycję **istniejący element**.  
  
6.  W **Dodaj istniejący element** okno dialogowe Otwórz listę rozszerzeń nazw plików, a następnie wybierz **wszystkie pliki (\*.\*)** .  
  
7.  W katalogu, który zawiera projekt BaseSharePointProject, wybierz plik key.snk, a następnie wybierz pozycję **Dodaj** przycisku.  
  
    > [!NOTE]  
    >  W tym przewodniku zostaje utworzony szablon projektu używa tego samego pliku key.snk do podpisywania każdego projektu, który jest tworzony przy użyciu szablonu. Aby dowiedzieć się, jak w celu rozszerzenia tego przykładu, aby utworzyć plik key.snk różne dla każdego wystąpienia projektu, zobacz [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8.  Powtórz kroki 5 – 8, aby dodać następujące pliki z określonej podfoldery w katalogu BaseSharePointProject:  
  
    -   \Field1\Elements.XML  
  
    -   \Field1\SharePointProjectItem.spdata  
  
    -   \Features\Feature1\Feature1.Feature  
  
    -   \Features\Feature1\Feature1.template.XML  
  
    -   \Package\Package.Package  
  
    -   \Package\Package.template.XML  
  
     Dodaj te pliki bezpośrednio do projektu SiteColumnProjectTemplate; nie ponownie utworzyć podfoldery pole1, funkcji lub pakietu w projekcie. Aby uzyskać więcej informacji o tych plikach, zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Aby skonfigurować sposób deweloperzy odnajdywanie szablonu projektu w oknie dialogowym Nowy projekt  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **SiteColumnProjectTemplate** węzła projektu, a następnie wybierz **Zwolnij projekt**. Jeśli zostanie wyświetlony monit, aby zapisać zmiany do wszystkich plików, wybierz **tak** przycisku.  
  
2.  Otwórz menu skrótów dla **SiteColumnProjectTemplate** węzeł ponownie, a następnie wybierz pozycję **Edytuj SiteColumnProjectTemplate.csproj** lub **Edytuj SiteColumnProjectTemplate.vbproj**.  
  
3.  W pliku projektu, Znajdź następujące `VSTemplate` elementu.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Zamień ten element następujący kod XML.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Element określa dodatkowe foldery w ścieżce, w którym szablon projektu jest tworzony podczas kompilowania projektu. Foldery określone tutaj upewnij się, szablon projektu będą dostępne tylko wtedy, gdy klienci Otwórz **nowy projekt** okna dialogowego rozwiń **programu SharePoint** węzeł, a następnie wybierz pozycję **2010**  węzła.  
  
5.  Zapisz i zamknij plik.  
  
6.  W **Eksploratora rozwiązań**, otwórz menu skrótów **SiteColumnProjectTemplate** projektu, a następnie wybierz pozycję **Załaduj ponownie projekt**.  
  
## <a name="editing-the-project-template-files"></a>Edytowanie plików projektu szablonu  
 W projekcie SiteColumnProjectTemplate edytować następujących plików Definiowanie zachowania szablonu projektu:  
  
-   AssemblyInfo.cs lub AssemblyInfo.vb  
  
-   Elements.XML  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.Feature  
  
-   Package.Package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj lub ProjectTemplate.vbproj  
  
 W poniższych procedurach warto parametry wymienne niektóre z tych plików. Parametr wymienny to token, który rozpoczyna się i kończy się znakiem dolara ($). Gdy użytkownik używa tego szablonu projektu, aby utworzyć projekt, Visual Studio automatycznie zastępuje tych parametrów w nowym projekcie z określonymi wartościami. Aby uzyskać więcej informacji, zobacz [parametry wymienne](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Aby edytować pliku AssemblyInfo.cs lub AssemblyInfo.vb  
  
1.  W projekcie SiteColumnProjectTemplate otworzyć pliku AssemblyInfo.cs lub AssemblyInfo.vb, a następnie dodaj następującą instrukcję na początku:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Podczas **rozwiązania typu piaskownica** ma ustawioną właściwość projektu SharePoint **True**, dodaje Visual Studio <xref:System.Security.AllowPartiallyTrustedCallersAttribute> do pliku kodu AssemblyInfo. Jednak nie importuje plik AssemblyInfo kodu w szablonie projektu <xref:System.Security> przestrzeni nazw domyślnie. Należy dodać to **przy użyciu** lub **importów** instrukcji, aby zapobiec błędy kompilacji.  
  
2.  Zapisz i zamknij plik.  
  
#### <a name="to-edit-the-elementsxml-file"></a>Aby edytować plik Elements.xml  
  
1.  W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku Elements.xml następujący kod XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Dodaje nowe XML `Field` element, który definiuje nazwy kolumny witryny, jego typ podstawowy i grupę, w których do tworzenia listy kolumny witryny w galerii. Aby uzyskać więcej informacji o zawartości tego pliku, zobacz [schematu definicji pola](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Zapisz i zamknij plik.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Aby edytować plik SharePointProjectItem.spdata  
  
1.  W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku SharePointProjectItem.spdata następujący kod XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     Nowy kod XML wprowadza następujące zmiany w pliku:  
  
    -   Zmiany `Type` atrybutu `ProjectItem` elementu, aby te same parametry przekazywane do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> w definicji elementu projektu ( `SiteColumnProjectItemTypeProvider` klasy, który został utworzony we wcześniejszej części tego przewodnika).  
  
    -   Usuwa `SupportedTrustLevels` i `SupportedDeploymentScopes` atrybutów z `ProjectItem` elementu. Wartości tych atrybutów są zbędne, ponieważ poziomy zaufania i wdrożenia zakresy są określone w `SiteColumnProjectItemTypeProvider` klasy w projekcie ProjectItemTypeDefinition.  
  
     Aby uzyskać więcej informacji o zawartości .spdata — pliki, zobacz [odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2.  Zapisz i zamknij plik.  
  
#### <a name="to-edit-the-feature1feature-file"></a>Aby edytować plik Feature1.feature  
  
1.  W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku Feature1.feature następujący kod XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     Nowy kod XML wprowadza następujące zmiany w pliku:  
  
    -   Zmienia wartości `Id` i `featureId` atrybuty `feature` elementu `$guid4$`.  
  
    -   Zmienia wartości `itemId` atrybutu `projectItemReference` elementu `$guid2$`.  
  
     Aby uzyskać więcej informacji na temat plików .feature zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Zapisz i zamknij plik.  
  
#### <a name="to-edit-the-packagepackage-file"></a>Aby edytować plik Package.package  
  
1.  W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku Package.package następujący kod XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     Nowy kod XML wprowadza następujące zmiany w pliku:  
  
    -   Zmienia wartości `Id` i `solutionId` atrybuty `package` elementu `$guid3$`.  
  
    -   Zmienia wartości `itemId` atrybutu `featureReference` elementu `$guid4$`.  
  
     Aby uzyskać więcej informacji na temat plików .package zobacz [Tworzenie szablonów elementów i szablonów projektu dla SharePoint — elementy projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Zapisz i zamknij plik.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Aby edytować plik SiteColumnProjectTemplate.vstemplate  
  
1.  W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku SiteColumnProjectTemplate.vstemplate jedną z następujących sekcji w pliku XML.  
  
    -   Jeśli tworzysz szablon projektu Visual C#, użyj następującego kodu XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   Jeśli tworzysz szablon projektu Visual Basic, użyj następującego pliku XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Nowy kod XML wprowadza następujące zmiany w pliku:  
  
    -   Ustawia `Name` elementu na wartość **kolumny witryny**. (Ta nazwa jest wyświetlana **nowy projekt** okno dialogowe).  
  
    -   Dodaje `ProjectItem` elementy dla każdego filethat obiektu zawarte w każdym wystąpieniu projektu.  
  
    -   Używa przestrzeni nazw "http://schemas.microsoft.com/developer/vstemplate/2005". Inne pliki projektu, w tym rozwiązaniu użycie tej przestrzeni nazw "http://schemas.microsoft.com/developer/msbuild/2003". W związku z tym komunikaty ostrzegawcze schematu XML, który zostanie wygenerowany, ale można je pominąć w tym przewodniku.  
  
     Aby uzyskać więcej informacji o zawartość plików .vstemplate, zobacz [odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2.  Zapisz i zamknij plik.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Aby edytować plik ProjectTemplate.csproj lub ProjectTemplate.vbproj  
  
1.  W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku ProjectTemplate.csproj lub ProjectTemplate.vbproj z jednym z następujących sekcji w pliku XML.  
  
    -   Jeśli tworzysz szablon projektu Visual C#, użyj następującego kodu XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Jeśli tworzysz szablon projektu Visual Basic, użyj następującego pliku XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Nowy kod XML wprowadza następujące zmiany w pliku:  
  
    -   Używa `TargetFrameworkVersion` elementu, aby określić programu .NET Framework 3.5, nie 4.5.  
  
    -   Dodaje `SignAssembly` i `AssemblyOriginatorKeyFile` elementy do podpisywania wyniku projektu.  
  
    -   Dodaje `Reference` elementy dla zestawu odwołuje się do używające projektów programu SharePoint.  
  
    -   Dodaje elementy dla każdego pliku domyślnego w projekcie, takie jak Elements.xml i SharePointProjectItem.spdata.  
  
2.  Zapisz i zamknij plik.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-template"></a>Tworzenie pakietu VSIX, aby wdrożyć szablon projektu  
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w **SiteColumnProjectItem** rozwiązania, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX, modyfikując plik Source.Extension.vsixmanifest,a, który jest dołączony do projektu VSIX. Następnie utwórz pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i tworzenia pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**w **SiteColumnProjectItem** projekt, otwórz plik Source.Extension.vsixmanifest,a w edytorze manifestu.  
  
     Plik Source.Extension.vsixmanifest,a stanowi podstawę dla wszystkich pakietów VSIX wymaga plik extension.vsixmanifest. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **kolumny witryny**.  
  
3.  W **autora** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **projekt Tworzenie kolumny witryny programu SharePoint A**.  
  
5.  Wybierz **zasoby** karcie, a następnie wybierz pozycję **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `ProjectTemplate` elementu w pliku extension.vsixmanifest. Ten element określa podfolderu w pakiet VSIX, który zawiera szablon projektu. Aby uzyskać więcej informacji, zobacz [ProjectTemplate — Element (schemat VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** listy, a następnie wybierz pozycję **SiteColumnProjectTemplate**, a następnie wybierz pozycję **OK** przycisku.  
  
9. Wybierz **nowy** przycisk ponownie.  
  
     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.  
  
10. W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
12. W **projektu** wybierz **ProjectItemTypeDefinition**, a następnie wybierz pozycję **OK** przycisku.  
  
13. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt skompiluje się bez błędów.  
  
## <a name="testing-the-project-template"></a>Szablon projektu do testowania  
 Teraz można przystąpić do testowania szablonu projektu. Najpierw należy uruchomić debugowanie rozwiązania SiteColumnProjectItem w eksperymentalne wystąpienie programu Visual Studio. Następnie sprawdź **kolumny witryny** projektu w eksperymentalne wystąpienie programu Visual Studio. Na koniec Skompiluj i uruchom projekt programu SharePoint, aby sprawdzić, czy kolumna lokacji działa zgodnie z oczekiwaniami.  
  
#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania  
  
1.  Uruchom ponownie program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie SiteColumnProjectItem.  
  
2.  
  
3.  W pliku kodu SiteColumnProjectItemTypeProvider, Dodaj punkt przerwania do pierwszego wiersza kodu w `InitializeType` metody, a następnie wybierz pozycję **F5** klucza można rozpocząć debugowania.  
  
     Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Element projektu przetestuje w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Aby przetestować projekt w programie Visual Studio  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Rozwiń węzeł **Visual C#** lub **Visual Basic** rozwiń węzeł (w zależności od języka obsługującego szablon projektu), **programu SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
3.  Na liście szablony projektów, wybierz **kolumny witryny** szablonu.  
  
4.  W **nazwa** wprowadź **SiteColumnTest** , a następnie wybierz **OK** przycisku.  
  
     W **Eksploratora rozwiązań**, nowy projekt, który pojawi się z elementem projektu o nazwie **pole1**.  
  
5.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `InitializeType` metody, a następnie wybierz pozycję **F5** klawisz, aby kontynuować debugowanie projektu.  
  
6.  W **Eksploratora rozwiązań**, wybierz **pole1** węzeł, a następnie wybierz pozycję **F4** klucza.  
  
     **Właściwości** zostanie otwarte okno.  
  
7.  Na liście właściwości upewnij się, że właściwość **przykład właściwości** jest wyświetlana.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Aby przetestować kolumny witryny w programie SharePoint  
  
1.  W **Eksploratora rozwiązań**, wybierz **SiteColumnTest** węzła.  
  
2.  W **właściwości** okna, w polu tekstowym, który jest obok pozycji **adres URL witryny** właściwości, wprowadź **http://localhost**.  
  
     Ten krok określa lokalnej witryny programu SharePoint na komputerze dewelopera, który ma być używany na potrzeby debugowania.  
  
    > [!NOTE]  
    >  **Adres URL witryny** właściwość jest pusta, domyślnie, ponieważ szablon projektu kolumn witryny nie udostępnia kreatora pobierania tej wartości podczas tworzenia projektu. Aby dowiedzieć się, jak dodać kreatora, który żąda dewelopera dla tej wartości, a następnie konfiguruje tę właściwość w nowym projekcie, zobacz [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Wybierz **F5** klucza.  
  
     Kolumny witryny zostaje spakowany i wdrożone do witryny programu SharePoint, która została określona w **adres URL witryny** właściwości projektu. Przeglądarki sieci web zostanie otwarty na domyślną stronę tej lokacji.  
  
    > [!NOTE]  
    >  Jeśli **wyłączenia debugowania skryptu** zostanie wyświetlone okno dialogowe, wybierz **tak** przycisk, aby kontynuować debugowanie projektu.  
  
4.  Na **Akcje witryny** menu, wybierz **ustawienia lokacji**.  
  
5.  Na **ustawienia lokacji** w obszarze **galerie** wybierz **kolumny witryny** łącza.  
  
6.  Na liście kolumn witryn, upewnij się, że **kolumny niestandardowe** grupa zawiera kolumny o nazwie **SiteColumnTest**.  
  
7.  Zamknij przeglądarkę sieci web.  
  
## <a name="cleaning-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim  
 Po zakończeniu testowania projektu, należy usunąć szablon projektu z eksperymentalne wystąpienie programu Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić na komputerze deweloperskim  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **kolumny witryny** rozszerzenia, a następnie wybierz pozycję **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisk, aby potwierdzić, że chcesz odinstalować rozszerzenia.  
  
4.  Wybierz **Zamknij** przycisk, aby ukończyć dezinstalację.  
  
5.  Zamknij oba wystąpienia programu Visual Studio (eksperymentalne wystąpienie i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie SiteColumnProjectItem).  
  
## <a name="next-steps"></a>Następne kroki  
 Po ukończeniu tego przewodnika, można dodać do szablonu projektu kreatora. Gdy użytkownik tworzy projekt kolumny witryny, Kreator zapyta, użytkownika, adres URL witryny do użycia na potrzeby debugowania i nowe rozwiązanie jest w trybie piaskownicy, a Kreator konfiguruje nowy projekt z tymi informacjami. Kreator również umożliwia zbieranie informacji o kolumnie (takie jak typ podstawowy i grupę, w której na liście kolumn w galerii kolumny) i dodaje te informacje do pliku Elements.xml w nowym projekcie. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Definiowanie typów elementów projektu SharePoint niestandardowych](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  