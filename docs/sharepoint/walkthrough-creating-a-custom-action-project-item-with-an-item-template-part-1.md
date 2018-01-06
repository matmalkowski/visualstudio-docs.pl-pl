---
title: "Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1 | Dokumentacja firmy Microsoft"
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
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: "152"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 70a307fe1eb68cb6e1409d0a43178795f0d9421c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1"></a>Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1
  System projektu programu SharePoint w Visual Studio można rozszerzyć przez utworzenie własnego projektu typów elementów. W tym przewodniku spowoduje utworzenie elementu projektu, który można dodać do projektu SharePoint do tworzenia niestandardowych akcji w witrynie programu SharePoint. Akcja niestandardowa dodaje element menu, aby **Akcje witryny** menu witryny programu SharePoint.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie rozszerzenia programu Visual Studio, który definiuje nowy typ elementu projektu SharePoint dla akcji niestandardowej. Nowy typ elementu projektu implementuje kilka funkcji niestandardowych:  
  
    -   Menu skrótów, która służy jako punkt początkowy dla dodatkowych zadań związanych z elementu projektu, takie jak wyświetlanie projektanta dla akcji niestandardowej w programie Visual Studio.  
  
    -   Kod wykonywany kiedy dewelopera zmiany niektórych właściwości elementu projektu i projektu, który go zawiera.  
  
    -   Niestandardowe ikonę, która jest wyświetlana obok elementu projektu w **Eksploratora rozwiązań**.  
  
-   Tworzenie szablonu elementów programu Visual Studio dla elementu projektu.  
  
-   Tworzenie pakietu rozszerzenia serwera Visual Studio (VSIX) do wdrożenia szablonu elementu projektu i zestawu rozszerzenia.  
  
-   Debugowanie i testowanie elementu projektu.  
  
 Jest to autonomiczny wskazówki. Po ukończeniu tego przewodnika, można zwiększyć przez dodanie kreatora do szablonu elementu elementu projektu. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie elementu projektu akcji niestandardowych z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Możesz pobrać przykład, który zawiera projekty ukończone, kodu i innych plików w ramach tego przewodnika z następującej lokalizacji: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Microsoft Windows, SharePoint i Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrażania elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Akcje niestandardowe w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Akcja niestandardowa](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Szablony elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [szablony tworzenie projektów i elementów](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
 W tym przewodniku, należy utworzyć trzy projekty:  
  
-   Projekt VSIX. Ten projekt tworzy pakiet VSIX do wdrażania elementu projektu SharePoint.  
  
-   Element projektu szablonu. Ten projekt tworzy szablon elementu, który może służyć do dodania do projektu SharePoint elementu projektu SharePoint.  
  
-   Projektu biblioteki klas. Ten projekt implementuje rozszerzenie programu Visual Studio, który definiuje zachowanie elementu projektu SharePoint.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
3.  Na liście w górnej części **nowy projekt** okna dialogowego upewnij się, że **.NET Framework 4.5** jest zaznaczone.  
  
4.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne wcześniej w tym temacie.  
  
5.  Wybierz **projektu VSIX** szablonu.  
  
6.  W **nazwa** wprowadź **CustomActionProjectItem**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **CustomActionProjectItem** projektu do **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-item-template-project"></a>Aby utworzyć projekt szablonu elementu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  Na liście w górnej części **nowy projekt** okna dialogowego upewnij się, że **.NET Framework 4.5** jest zaznaczone.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
4.  Na liście szablony projektów, wybierz **szablonu elementu języka C#** lub **szablon elementu Visual Basic** szablonu.  
  
5.  W **nazwa** wprowadź **ItemTemplate**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **ItemTemplate** projektu do rozwiązania.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  Na liście w górnej części **nowy projekt** okna dialogowego upewnij się, że **.NET Framework 4.5** jest zaznaczone.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, wybierz **systemu Windows** węzeł, a następnie wybierz pozycję  **Biblioteka klas** szablonu projektu.  
  
4.  W **nazwa** wprowadź **ProjectItemDefinition**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **ProjectItemDefinition** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configuring-the-extension-project"></a>Konfigurowanie projekt rozszerzenia  
 Przed przystąpieniem do napisania kod, aby zdefiniować typu elementu projektu SharePoint, należy dodać pliki kodu i odwołania do zestawów w projekcie rozszerzenia.  
  
#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ProjectItemDefinition** projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.  
  
2.  Na liście elementów projektu, wybierz **pliku kodu**.  
  
3.  W **nazwa** wprowadź nazwę **Akcja niestandardowa** z odpowiednie rozszerzenie nazwy pliku, a następnie wybierz pozycję **Dodaj** przycisku.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ProjectItemDefinition** projektu, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
5.  W **Menedżera odwołań - ProjectItemDefinition** okna dialogowego wybierz **zestawy** węzeł, a następnie wybierz pozycję **Framework** węzła.  
  
6.  Zaznacz pole wyboru obok każdego z następujących zestawów:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Wybierz **rozszerzenia** węzła, zaznacz pole wyboru obok zestawu Microsoft.VisualStudio.Sharepoint, a następnie wybierz **OK** przycisku.  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>Definiowanie nowy typ elementu projektu SharePoint  
 Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu Definiowanie zachowania nowy typ elementu projektu. Zawsze, gdy chcesz zdefiniować nowy typ elementu projektu, należy zaimplementować ten interfejs.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Aby określić nowy typ elementu projektu SharePoint  
  
1.  W projekcie ProjectItemDefinition Otwórz plik kodu Akcja niestandardowa.  
  
2.  Zastąp kod w tym pliku następującym kodem.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="creating-an-icon-for-the-project-item-in-solution-explorer"></a>Tworzenie ikony dla elementu projektu w Eksploratorze rozwiązań  
 Podczas tworzenia niestandardowego elementu projektu SharePoint obrazu (ikony lub mapy bitowej) można skojarzyć z elementem projektu. Ten obraz jest wyświetlany obok elementu projektu w **Eksploratora rozwiązań**.  
  
 Poniższa procedura służy do utworzenia ikony dla elementu projektu i osadzone ikony zestawu rozszerzenia. Odwołuje się ta ikona <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> z `CustomActionProjectItemTypeProvider` klasy, który został utworzony wcześniej.  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Aby utworzyć niestandardowe ikonę dla elementu projektu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ProjectItemDefinition** projektu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy element...** .  
  
2.  Na liście elementów projektu, wybierz **pliku ikony** elementu.  
  
    > [!NOTE]  
    >  W projektach Visual Basic, musisz wybrać **ogólne** węzeł, aby wyświetlić **pliku ikony** elementu.  
  
3.  W **nazwa** wprowadź **CustomAction_SolutionExplorer.ico**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Otwiera nową ikonę w **edytor obrazów**.  
  
4.  Edytuj wersji 16 x 16 pliku ikony, aby projekt może rozpoznać, a następnie zapisz plik ikony.  
  
5.  W **Eksploratora rozwiązań**, wybierz **CustomAction_SolutionExplorer.ico**.  
  
6.  W **właściwości** okna, wybierz strzałkę obok pozycji **Akcja kompilacji** właściwości.  
  
7.  Na liście wybierz **osadzonego zasobu**.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie w prezentacji, całego kodu dla elementu projektu jest teraz w projekcie. Skompiluj projekt, aby sprawdzić, czy skompilowany bez błędów.  
  
#### <a name="to-build-your-project"></a>Aby utworzyć projekt  
  
1.  Otwórz menu skrótów **ProjectItemDefinition** projekt i wybierz pozycję **kompilacji**.  
  
## <a name="creating-a-visual-studio-item-template"></a>Tworzenie szablonu elementów programu Visual Studio  
 Aby włączyć inne deweloperom używanie tego elementu projektu, należy utworzyć szablon projektu lub szablon elementu. Deweloperzy używać tych szablonów w programie Visual Studio do utworzenia wystąpienia elementu z projektu przez utworzenie nowego projektu lub Dodaj element do istniejącego projektu. W ramach tego przewodnika umożliwia skonfigurowanie tego elementu projektu projektu ItemTemplate.  
  
#### <a name="to-create-the-item-template"></a>Aby utworzyć szablon elementu  
  
1.  Usuń plik kodu Class1 z projektu ItemTemplate.  
  
2.  W projekcie ItemTemplate Otwórz plik ItemTemplate.vstemplate.  
  
3.  Zastąp zawartość pliku z następującego pliku XML, a następnie zapisz i zamknij plik.  
  
    > [!NOTE]  
    >  Następujący kod XML jest szablonu elementu języka Visual C#. Jeśli tworzysz szablon elementu programu Visual Basic, zastąp wartość `ProjectType` element z `VisualBasic`.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Ten plik definiuje zawartości i zachowania szablon elementu. Aby uzyskać więcej informacji o zawartości tego pliku, zobacz [odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ItemTemplate** projektu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
5.  W **Dodaj nowy element** oknie dialogowym wybierz **pliku tekstowego** szablonu.  
  
6.  W **nazwa** wprowadź **CustomAction.spdata**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
7.  Dodaj następujący kod XML do pliku CustomAction.spdata, a następnie zapisz i zamknij plik.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Ten plik zawiera informacje o plikach, które są zawarte w elemencie projektu. `Type` Atrybutu `ProjectItem` element musi być ustawiony na ten sam ciąg, który jest przekazywany do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> w definicji elementu projektu ( `CustomActionProjectItemTypeProvider` klasy utworzony we wcześniejszej części tego przewodnika). Aby uzyskać więcej informacji o zawartości .spdata — pliki, zobacz [odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ItemTemplate** projektu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
9. W **Dodaj nowy element** oknie dialogowym wybierz **pliku XML** szablonu.  
  
10. W **nazwa** wprowadź **Elements.xml**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
11. Zastąp zawartość pliku Elements.xml następującego pliku XML, a następnie zapisz i zamknij plik.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Ten plik Określa domyślne działanie niestandardowych, które tworzy element menu na **Akcje witryny** menu witryny programu SharePoint. Po wybraniu elementu menu, adres URL określony w `UrlAction` elementu otwiera w przeglądarce sieci web. Aby uzyskać więcej informacji na temat elementów XML, służy do definiowania akcji niestandardowej, zobacz [niestandardowe definicje akcji](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Opcjonalnie Otwórz plik ItemTemplate.ico i zmodyfikuj go, aby projekt, który może rozpoznać. Ta ikona będzie wyświetlana obok elementu projektu w **Dodaj nowy element** okno dialogowe.  
  
13. W **Eksploratora rozwiązań**, otwórz menu skrótów **ItemTemplate** projektu, a następnie wybierz pozycję **Zwolnij projekt**.  
  
14. Otwórz menu skrótów **ItemTemplate** ponownie projekt, a następnie wybierz **Edytuj ItemTemplate.csproj** lub **Edytuj ItemTemplate.vbproj**.  
  
15. Znajdź następujące `VSTemplate` elementu w pliku projektu.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Zastąp to `VSTemplate` elementu o następujące XML, a następnie zapisz i zamknij plik.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Element określa dodatkowe foldery w ścieżce, w którym szablon elementu jest tworzony podczas kompilowania projektu. Foldery określone tutaj upewnij się, szablon elementu będą dostępne tylko wtedy, gdy klienci Otwórz **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010**  węzła.  
  
17. W **Eksploratora rozwiązań**, otwórz menu skrótów **ItemTemplate** projektu, a następnie wybierz pozycję **Załaduj ponownie projekt**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item"></a>Tworzenie pakietu VSIX do wdrażania elementu projektu  
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX, modyfikując plik Source.Extension.vsixmanifest,a, który jest dołączony do projektu VSIX. Następnie utwórz pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i tworzenia pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **source.extension.vsixmanifest** pliku w projekcie CustomActionProjectItem, a następnie wybierz pozycję **Otwórz**.  
  
     Visual Studio otwiera plik w edytorze manifestu. Plik Source.Extension.vsixmanifest,a stanowi podstawę dla wszystkich pakietów VSIX wymaga plik extension.vsixmanifest. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **elementu projektu akcji niestandardowych**.  
  
3.  W **autora** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **elementu projektu A SharePoint, który reprezentuje akcję niestandardową**.  
  
5.  Na **zasoby** , wybierz pozycję **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `ItemTemplate` elementu w pliku extension.vsixmanifest. Ten element określa podfolderu w pakiet VSIX, który zawiera szablon elementu projektu. Aby uzyskać więcej informacji, zobacz [elementu ItemTemplate (schemat VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** wybierz **ItemTemplate**, a następnie wybierz pozycję **OK** przycisku.  
  
9. W **zasoby** , wybierz pozycję **nowy** przycisk ponownie.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
10. W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
12. W **projektu** wybierz **ProjectItemDefinition**.  
  
13. Wybierz **OK** przycisku.  
  
14. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt skompiluje się bez błędów.  
  
15. Upewnij się, że folder wyjściowy kompilacji projektu CustomActionProjectItem zawiera plik CustomActionProjectItem.vsix.  
  
     Domyślnie jest folder wyjściowy kompilacji... \bin\Debug folderu w folderze, który zawiera projekt CustomActionProjectItem.  
  
## <a name="testing-the-project-item"></a>Testowanie elementu projektu  
 Teraz można przystąpić do przetestowania elementu projektu. Najpierw należy uruchomić debugowanie rozwiązania CustomActionProjectItem w eksperymentalne wystąpienie programu Visual Studio. Następnie sprawdź **Akcja niestandardowa** elementu projektu w projekcie programu SharePoint w eksperymentalne wystąpienie programu Visual Studio. Na koniec Skompiluj i uruchom projekt programu SharePoint, aby sprawdzić, czy akcja niestandardowa działa zgodnie z oczekiwaniami.  
  
#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania  
  
1.  Uruchom ponownie program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie CustomActionProjectItem.  
  
2.  Otwórz plik kodu Akcja niestandardowa, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `InitializeType` metody.  
  
3.  Wybierz **F5** klucza można rozpocząć debugowania.  
  
     Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 projektu akcji i uruchamia eksperymentalne wystąpienie programu Visual Studio. Element projektu przetestujesz, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Aby przetestować element projektu w programie Visual Studio  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Rozwiń węzeł **Visual C#** lub **Visual Basic** (w zależności od języka obsługującego szablonu elementu), rozwiń węzeł **SharePoint**, a następnie wybierz pozycję **2010**  węzła.  
  
3.  Na liście szablony projektów, wybierz **projektu programu SharePoint 2010**.  
  
4.  W **nazwa** wprowadź **CustomActionTest**, a następnie wybierz pozycję **OK** przycisku.  
  
5.  W **Kreator dostosowania programu SharePoint**, wprowadź adres URL witryny, która ma być używany na potrzeby debugowania, a następnie wybierz pozycję **Zakończ** przycisku.  
  
6.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła projektu, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
7.  W **Dodaj nowy element** oknie dialogowym wybierz **2010** węźle **SharePoint** węzła.  
  
     Sprawdź, czy **Akcja niestandardowa** element będzie wyświetlany na liście elementów projektu.  
  
8.  Wybierz **Akcja niestandardowa** elementu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Visual Studio dodaje element o nazwie **CustomAction1** do projektu i otwiera Elements.xml plik w edytorze.  
  
9. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `InitializeType` metody.  
  
10. Wybierz **F5** klawisz, aby kontynuować debugowanie projektu.  
  
11. W eksperymentalne wystąpienie programu Visual Studio w **Eksploratora rozwiązań**, otwórz menu skrótów dla **CustomAction1** węzeł, a następnie wybierz pozycję **projektanta akcji niestandardowych widoków**.  
  
12. Sprawdź, czy pojawi się okno komunikatu, a następnie wybierz **OK** przycisku.  
  
     Aby zapewnić dodatkowe opcje lub polecenia dla deweloperów, takie jak wyświetlanie projektanta dla akcji niestandardowej, można użyć tego menu skrótów.  
  
13. Na pasku menu wybierz **widoku**, **dane wyjściowe**.  
  
     **Dane wyjściowe** zostanie otwarte okno.  
  
14. W **Eksploratora rozwiązań**, otwórz menu skrótów **CustomAction1** elementu, a następnie zmień jego nazwę, aby **MyCustomAction**.  
  
     W **dane wyjściowe** zostanie wyświetlone okno, komunikat potwierdzenia. Ta wiadomość została napisana przez <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> obsługi zdarzeń, który został zdefiniowany w `CustomActionProjectItemTypeProvider` klasy. Może obsłużyć tego zdarzenia oraz inne zdarzenia element projektu do zaimplementowania niestandardowe zachowanie, gdy dewelopera modyfikuje elementu projektu.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Aby przetestować akcji niestandardowej w programie SharePoint  
  
1.  Eksperymentalne wystąpienie programu Visual Studio, otwórz plik Elements.xml, który jest elementem podrzędnym **MyCustomAction** elementu projektu.  
  
2.  W pliku Elements.xml wprowadź następujące zmiany, a następnie zapisz plik:  
  
    -   W `CustomAction` , ustaw `Id` atrybut GUID lub unikatowy ciąg jak przedstawiono na poniższym przykładzie:  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   W `CustomAction` , ustaw `Title` atrybutu, jak przedstawiono na poniższym przykładzie:  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   W `CustomAction` , ustaw `Description` atrybutu, jak przedstawiono na poniższym przykładzie:  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   W `UrlAction` , ustaw `Url` atrybutu, jak przedstawiono na poniższym przykładzie:  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Wybierz klawisz F5.  
  
     Akcja niestandardowa zostaje spakowany i wdrożone do witryny programu SharePoint, która została określona w **adres URL witryny** właściwości projektu. Przeglądarki sieci web zostanie otwarty na domyślną stronę tej lokacji.  
  
    > [!NOTE]  
    >  Jeśli **wyłączenia debugowania skryptu** zostanie wyświetlone okno dialogowe, wybierz **tak** przycisk, aby kontynuować debugowanie projektu.  
  
4.  Na **Akcje witryny** menu, wybierz **SharePoint Developer Center**, sprawdź, czy przeglądarka otworzy http://msdn.microsoft.com/sharepoint/default.aspx witryny sieci Web, a następnie zamknij przeglądarkę sieci web.  
  
## <a name="cleaning-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim  
 Po zakończeniu testowania elementu projektu, należy usunąć szablonu elementu projektu z eksperymentalne wystąpienie programu Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić na komputerze deweloperskim  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **elementu projektu akcji niestandardowych**, a następnie wybierz pozycję **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisk, aby potwierdzić, że chcesz odinstalować rozszerzenia.  
  
4.  Wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.  
  
5.  Zamknij zarówno eksperymentalne wystąpienie programu Visual Studio i wystąpienia, w którym rozwiązania CustomActionProjectItem jest otwarty.  
  
## <a name="next-steps"></a>Następne kroki  
 Po ukończeniu tego przewodnika, można dodać do szablonu elementu kreatora. Gdy użytkownik dodaje niestandardowa akcja elementu projektu do projektu SharePoint, Kreator zbiera informacje o akcji (na przykład jego położenie i adres URL nawigacji po wybraniu akcji) i dodaje te informacje do pliku Elements.xml w nowym elemencie projektu. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie elementu projektu akcji niestandardowych z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Definiowanie typów elementów projektu SharePoint niestandardowych](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)   
 [Tworzenie ikony lub innego obrazu &#40; edytor obrazów dla ikon &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  