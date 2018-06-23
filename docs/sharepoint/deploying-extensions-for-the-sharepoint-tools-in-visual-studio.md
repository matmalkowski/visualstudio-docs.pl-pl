---
title: Wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58b430d1331a12e080d238d34a4817afea8585d1
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326868"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio

Aby wdrożyć rozszerzenie narzędzia programu SharePoint, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX), który zawiera zestaw rozszerzenia i inne pliki, które chcesz dystrybuować z rozszerzeniem. Pakiet VSIX jest skompresowany plik znajdujący się standard otwarte konwencje pakietów (OPC). Pakiety VSIX zawierają *.vsix* rozszerzenia.

Po utworzeniu pakietu VSIX innych użytkowników można uruchomić plik .vsix, aby zainstalować rozszerzenie. Gdy użytkownik instaluje rozszerzenia, wszystkie pliki są instalowane w folderze %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Aby wdrożyć rozszerzenie, możesz przekazać pakiet VSIX [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witryny sieci Web, lub można rozproszyć pakiet do klientów przy użyciu innych metod, takich jak hosting pakietu na udziału sieciowego lub innej witryny sieci Web.

Aby uzyskać więcej informacji na temat tworzenia pakietów VSIX i wdrażanie ich do [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), zobacz [wysyłania rozszerzenia dla programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Pakiet VSIX można utworzyć za pomocą **projektu VSIX** szablonu w programie Visual Studio, lub można ręcznie utworzyć pakiet VSIX.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Umożliwia tworzenie pakietów VSIX VSIX projektów

Można użyć **projektu VSIX** szablonem programu Visual Studio SDK, aby utworzyć pakiety VSIX dla rozszerzeń narzędzi SharePoint. Przy użyciu projektu VSIX zapewnia kilka korzyści przez utworzenie pakietu VSIX ręcznie:

-   Podczas kompilowania projektu programu Visual Studio automatycznie generuje pakietu VSIX. Zadania, takie jak dodawanie plików wdrożenia pakietu i tworzenie pliku XML [Content_Types] dla pakietu są wykonywane automatycznie.

-   Istnieje możliwość skonfigurowania projektu VSIX, aby dołączyć dane wyjściowe kompilacji projektu rozszerzenia i inne pliki, takie jak szablony projektów i szablony elementów pakietu VSIX.

Aby uzyskać więcej informacji o korzystaniu z projektu VSIX, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organizowania projektów

Domyślnie projektów VSIX generować tylko pakiety VSIX, nie zestawów. W związku z tym należy zwykle nie należy implementować rozszerzeń narzędzi SharePoint w projekcie VSIX. Ogólnie rzecz biorąc pracować z co najmniej dwa projekty:

-   Projekt VSIX.

-   Projektu biblioteki klas, który implementuje rozszerzenia.

Możesz także pracować z projektami dodatkowych dla niektórych typów rozszerzeń:

-   Projekt biblioteki klasy, który implementuje żadnych poleceń programu SharePoint, które są używane przez rozszerzenia. Aby uzyskać wskazówki, które przedstawiono w tym scenariuszu, zobacz [wskazówki: rozszerzanie Eksploratora serwera do wyświetlania elementów sieci web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

-   Projekt elementu lub szablon projektu, który tworzy element lub szablon projektu, jeśli rozszerzenie definiuje nowy typ elementu projektu SharePoint. Aby uzyskać wskazówki, które przedstawiono w tym scenariuszu, zobacz [wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

-   Projekt biblioteki klasy, który implementuje Kreator niestandardowy szablon elementu lub szablonu projektu, jeśli rozszerzenie zawiera szablon. Aby uzyskać wskazówki, które przedstawiono w tym scenariuszu, zobacz [wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Jeśli dołączysz wszystkich projektów, w tym samym rozwiązaniu Visual Studio, można zmodyfikować pliku source.extension.vsixmanifest w projekcie VSIX, aby dołączyć dane wyjściowe kompilacji projektów biblioteki klas.

### <a name="edit-the-vsix-manifest"></a>Edytuj VSIX manifest

Należy edytować plik Source.Extension.vsixmanifest,a w projektu VSIX, aby dołączyć wpisy dla wszystkich elementów, które chcesz uwzględnić w Twoje rozszerzenie. Po otwarciu pliku source.extension.vsixmanifest z menu skrótów, plik zostanie wyświetlony w projektancie, która zapewnia interfejs użytkownika do edycji kodu XML w pliku. Aby uzyskać więcej informacji, zobacz [projektanta manifestu VSIX](../extensibility/vsix-manifest-designer.md).

Należy dodać wpisów do pliku source.extension.vsixmanifest dla następujących elementów:

-   Zestaw rozszerzeń.

-   Zestaw, który implementuje żadnych poleceń programu SharePoint, które są używane przez Twoje rozszerzenie.

-   Szablony projektów lub szablony elementów, które są skojarzone z rozszerzeniem.

-   Kreator niestandardowy szablon, który jest skojarzony z rozszerzeniem.

Poniższe procedury zawierają opis można dodawać do pliku .vsixmanifest dla każdego z tych elementów.

#### <a name="to-include-the-extension-assembly"></a>Aby uwzględnić zestawu rozszerzenia

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz**.

     Plik zostanie otwarty w Projektancie

2.  Na **zasoby** karta edytora, wybierz **nowy** przycisku.

     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.

3.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.

4.  W **źródła** listy, wykonaj jedną z następujących czynności:

    -   Jeśli zestawu rozszerzenia składa się z projektu, należącego do tego samego rozwiązania co projekt VSIX, wybierz **projekt w bieżącym rozwiązaniu**. W **projektu** listy, wybierz nazwę projektu.

    -   Jeśli zestawu rozszerzenia jest uwzględniona jako pliku w projekcie, wybierz **pliku w systemie plików**. W **ścieżki** listy, wprowadź pełną ścieżkę do pliku zestawu rozszerzenia lub użyj **Przeglądaj** przycisk, aby znaleźć i wybrać plik zestawu.

5.  Wybierz **OK** przycisku.

#### <a name="to-include-a-sharepoint-command-assembly"></a>Aby uwzględnić zestaw poleceń programu SharePoint

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz** przycisku.

     Plik zostanie otwarty w projektancie.

2.  W **zasoby** sekcji edytora, wybierz **nowy** przycisku.

     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.

3.  W **typu** wprowadź **SharePoint.Commands.v4**.

4.  W **źródła** listy, wykonaj jedną z następujących czynności:

    -   Polecenie zestaw składa się z projektu, należącego do tego samego rozwiązania co projekt VSIX, jeśli **projekt w bieżącym rozwiązaniu**. W **projektu** listy, wybierz nazwę projektu.

    -   Jeśli zestaw poleceń jest uwzględniana jako pliku w projekcie, wybierz **pliku w systemie plików**. W **ścieżki** listy, wprowadź pełną ścieżkę do pliku zestawu rozszerzenia lub użyj **Przeglądaj** przycisk, aby znaleźć i wybrać plik zestawu.

5.  Wybierz **OK** przycisku.

#### <a name="to-include-a-template-that-you-create"></a>Aby uwzględnić utworzonego szablonu

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz** przycisku.

     Plik zostanie otwarty w projektancie.

2.  W **zasoby** sekcji edytora, wybierz **nowy** przycisku.

     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.

3.  W **typu** wybierz **Microsoft.VisualStudio.ProjectTemplate** lub **Microsoft.VisualStudio.ItemTemplate**.

4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

5.  W **projektu** listy, wybierz nazwę projektu, a następnie wybierz **OK** przycisku.

6.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu lub elementu szablon projektu, a następnie wybierz **Zwolnij projekt**.

7.  Ponownie otwórz menu skrótów węzła projektu, a następnie wybierz pozycję **Edytuj***YourTemplateProjectName***.csproj** lub **Edytuj***YourTemplateProjectName***. vbproj**.

8.  Znajdź następujące `VSTemplate` elementu w pliku projektu.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Zamień ten element następujący kod XML.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` Element określa dodatkowe foldery w ścieżce, w którym szablon projektu jest tworzony podczas kompilowania projektu. Foldery określone tutaj upewnij się, szablon elementu będą dostępne tylko wtedy, gdy klienci Otwórz **Dodawanie nowego projektu** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010**  węzła.

10. Zapisz i zamknij plik.

11. W **Eksploratora rozwiązań**, otwórz menu skrótów projektu lub elementu szablon projektu, a następnie wybierz **Załaduj ponownie projekt**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Aby uwzględnić szablon, który można tworzyć ręcznie

1.  W projekcie VSIX należy dodać nowy folder do projektu, który zawiera szablon.

2.  W tym folderze nowe, utwórz następujące podfoldery, a następnie dodaj plik szablonu (.zip) do *identyfikator ustawień regionalnych* folderu.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Identyfikator ustawień regionalnych*

     *YourTemplateName*zip

     Na przykład, jeśli szablon elementu o nazwie ContosoCustomAction.zip, który obsługuje ustawień regionalnych angielski (Stany Zjednoczone), pełna ścieżka może być *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3.  W **Eksploratora rozwiązań**, wybierz plik szablonu (*YourTemplateName*.zip).

4.  W **właściwości** ustaw **Akcja kompilacji** właściwości **zawartości**.

5.  Otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz pozycję **Otwórz**.

     Plik zostanie otwarty w projektancie.

6.  W **zasoby** sekcji edytora, wybierz **nowy** przycisku.

     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.

7.  W **typu** wybierz **Microsoft.VisualStudio.ItemTemplate** lub **Microsoft.VisualStudio.ProjectTemplate**.

8.  W **źródła** wybierz **pliku w systemie plików**.

9. W **ścieżki** wprowadź pełną ścieżkę do zestawu (na przykład *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, lub użyj **Przeglądaj**przycisk Znajdź i wybierz zestaw, a następnie wybierz **OK** przycisku.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Aby uwzględnić Kreatora szablonu projektu lub elementu szablonu

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz**.

     Plik zostanie otwarty w projektancie.

2.  W **zasoby** sekcji edytora, wybierz **nowy** przycisku.

     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.

3.  W **typu** wybierz **Microsoft.VisualStudio.Assembly**.

4.  W **źródła** listy, wykonaj jedną z następujących czynności:

    -   Jeśli zestaw kreatora składa się z projektu, należącego do tego samego rozwiązania co projekt VSIX, wybierz **projekt w bieżącym rozwiązaniu**. W **projektu** listy, wybierz nazwę projektu.

    -   Jeśli Kreator zestawu jest uwzględniona jako pliku w projekcie, wybierz **pliku w systemie plików**. W **ścieżki** pola, wprowadź pełną ścieżkę do pliku zestawu lub użyj **Przeglądaj** przycisk, aby znaleźć i wybrać zestaw.

5.  Wybierz **OK** przycisku.

### <a name="related-walkthroughs"></a>Instruktaże pokrewne

W poniższej tabeli przedstawiono wskazówki, które przedstawiają sposób umożliwiają wdrażanie różnych rodzajów rozszerzeń narzędzi SharePoint projektu VSIX.

|Typ rozszerzenia|Instruktaże pokrewne|
|--------------------|--------------------------|
|Rozszerzenie, które obejmują tylko zestawu rozszerzenia|[Wskazówki: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Wskazówki: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Wskazówki: Wywołują modelu obiektów klienta programu SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Rozszerzenie zawiera polecenia SharePoint|[Wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Rozszerzenie zawiera szablon programu Visual Studio|[Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Rozszerzenie zawiera Kreatora szablonu|[Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Ręczne tworzenie pakietów VSIX

Jeśli chcesz ręcznie utworzyć pakietu VSIX dla narzędzi SharePoint rozszerzenia, wykonaj następujące czynności:

1.  Utwórz plik extension.vsixmanifest i pliku XML [Content_Types] w nowym folderze. Aby uzyskać więcej informacji, zobacz [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2.  W Eksploratorze Windows kliknij prawym przyciskiem myszy folder, który zawiera dwa pliki XML, kliknij przycisk Wyślij do, a następnie kliknij Folder skompresowane. Zmień nazwę wynikowy plik zip na Filename.vsix, gdzie nazwa pliku jest nazwą pliku do dystrybucji, który instaluje pakiet.

3.  Dodaj używanego zestawu rozszerzeń do pakietu VSIX. Jeśli rozszerzenie zawiera polecenie programu SharePoint, należy również dodać zestawu, który implementuje polecenie programu SharePoint do pakietu VSIX.

4.  Należy zmodyfikować plik extension.vsixmanifest:

    -   Dodaj `Microsoft.VisualStudio.MefComponent` elementu w obszarze `Assets` elementu, a następnie ustaw wartość nowego elementu do zestawu, który implementuje rozszerzenie pakietu VSIX ścieżkę względną. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).

    -   Jeśli rozszerzenie zawiera polecenie programu SharePoint, który odwołuje się do modelu obiektów serwera dla programu SharePoint, należy dodać `Microsoft.VisualStudio.Assembly` elementu w obszarze `Assets` elementu. Wartość nowego elementu do zestawu, który implementuje polecenie programu SharePoint w pakiecie VSIX ścieżkę względną. Aby uzyskać więcej informacji, zobacz [zasobów — Element (schemat VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).

    -   Jeśli rozszerzenie zawiera szablon projektu lub szablon elementu, należy dodać `ProjectTemplate` lub `ItemTemplate` elementu w obszarze `Assets` elementu. Wartość nowego elementu względną ścieżkę folderu, który zawiera szablon pakietu VSIX. Aby uzyskać więcej informacji, zobacz [ProjectTemplate — Element (schemat VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1) i [elementu ItemTemplate (schemat VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).

    -   Jeśli rozszerzenie zawiera Kreator niestandardowy szablon projektu lub elementu szablonu, Dodaj `Assembly` elementu w obszarze `Assets` elementu. Ustaw wartość nowego elementu do ścieżki względnej zestawu w pakiecie VSIX, a następnie ustaw `AssemblyName` atrybutu nazwy pełnego zestawu (w tym wersję, kulturę i token klucza publicznego). Aby uzyskać więcej informacji, zobacz [zależności — Element (schemat VSX)](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono zawartość pliku extension.vsixmanifest dla rozszerzeń narzędzi SharePoint. Rozszerzenie jest zaimplementowana w zestawie o nazwie Contoso.ProjectExtension.dll. Rozszerzenie zawiera zestaw polecenie programu SharePoint o nazwie Contoso.ExtensionCommands.dll i szablonu elementów w folderze o nazwie **elementów** w pakiecie VSIX. W tym przykładzie przyjęto założenie, że oba zestawy są w tym samym folderze co plik extension.vsixmanifest w pakiecie VSIX.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Debugowanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
