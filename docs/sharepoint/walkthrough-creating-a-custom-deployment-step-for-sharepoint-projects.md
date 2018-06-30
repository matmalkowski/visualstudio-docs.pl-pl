---
title: 'Wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aee7c1bf7a7a8d71d02da7bab270c4df1a4a52ab
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120331"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint
  Podczas wdrażania projektu SharePoint Visual Studio wykonuje serię kroków wdrożenia w określonej kolejności. Visual Studio obejmuje wiele kroków wdrażania wbudowanych, ale mogą także tworzyć własne.  
  
 W tym przewodniku spowoduje utworzenie niestandardowego kroku wdrożenia do uaktualnienia rozwiązań na serwerze z programem SharePoint. Visual Studio zawiera kroki wdrażania wbudowanych dla wielu zadań, takich odwołaniem lub Dodawanie rozwiązania, ale nie zawiera krok wdrażania dotyczące uaktualniania rozwiązań. Domyślnie podczas wdrażania rozwiązania programu SharePoint, Visual Studio najpierw wycofuje rozwiązania (jeśli została już wdrożona), a następnie wdraża ponownie całego rozwiązania. Aby uzyskać więcej informacji na temat kroków związanych wbudowanych wdrożenia, zobacz [wdrażanie, publikowanie oraz aktualizowanie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie rozszerzenia programu Visual Studio, który wykonuje dwie główne zadania:  
  
    -   Rozszerzenie definiuje niestandardowego kroku wdrożenia do uaktualnienia rozwiązań programu SharePoint.  
  
    -   Rozszerzenie tworzy rozszerzenia projektu, który definiuje nową konfigurację wdrożenia, który jest zestaw kroków wdrażania, które są wykonywane dla danego projektu. Nową konfigurację wdrożenia zawiera niestandardowego kroku wdrożenia i kilka kroków wdrażania wbudowanych.  
  
-   Utwórz dwa niestandardowych poleceń programu SharePoint, które wywołuje zestawu rozszerzenia. Polecenia SharePoint są metody, które mogą być wywoływane przez zestawy rozszerzenia, aby użyć interfejsów API w modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Tworzenie pakietu rozszerzenia serwera Visual Studio (VSIX) w celu wdrażania zarówno zestawów.  
  
-   Testowanie nowy krok wdrożenia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Windows, SharePoint i Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio SDK. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX, aby wdrożyć rozszerzenie. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Za pomocą modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [za pomocą modelu obiektów programu SharePoint Foundation po stronie serwera](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Rozwiązania programu SharePoint. Aby uzyskać więcej informacji, zobacz [omówienie rozwiązań](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Uaktualnianie rozwiązań programu SharePoint. Aby uzyskać więcej informacji, zobacz [uaktualniania rozwiązania](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="create-the-projects"></a>Tworzenie projektów
 W tym przewodniku, należy utworzyć trzy projekty:  
  
-   Aby utworzyć pakiet VSIX, aby wdrożyć rozszerzenie projekt VSIX.  
  
-   Projektu biblioteki klas, który implementuje rozszerzenia. Ten projekt musi wskazywać na .NET Framework 4.5.  
  
-   Projektu biblioteki klas, który definiuje niestandardowe polecenia programu SharePoint. Ten projekt musi wskazywać na .NET Framework 3.5.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku** > **nowy** > **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne wcześniej w tym temacie.  
  
4.  W górnej części okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
5.  Wybierz **projektu VSIX** szablonu, nazwy projektu **UpgradeDeploymentStep**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **UpgradeDeploymentStep** projektu do **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła UpgradeDeploymentStep rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **Windows** węzła.  
  
3.  W górnej części okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
4.  Wybierz **biblioteki klas** projektu szablonu, nazwy projektu **DeploymentStepExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **DeploymentStepExtension** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Aby utworzyć projekt polecenia SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła UpgradeDeploymentStep rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **Windows** węzła.  
  
3.  W górnej części okna dialogowego, wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.  
  
4.  Wybierz **biblioteki klas** projektu szablonu, nazwy projektu **SharePointCommands**, a następnie wybierz pozycję **OK** przycisku.  
  
     Dodaje programu Visual Studio **SharePointCommands** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed przystąpieniem do napisania kod w celu utworzenia niestandardowego kroku wdrożenia, należy dodać pliki kodu i odwołania do zestawów i należy skonfigurować projektów.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Aby skonfigurować projekt DeploymentStepExtension
  
1.  W **DeploymentStepExtension** projekt, dodaj dwa pliki kodu, które mają następujące nazwy:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Otwórz menu skrótów projektu DeploymentStepExtension, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
3.  Na **Framework** , a następnie wybierz pole wyboru dla zestawu System.ComponentModel.Composition.  
  
4.  Na **rozszerzenia** karcie, zaznacz pole wyboru dla zestawu Microsoft.VisualStudio.SharePoint, a następnie wybierz **OK** przycisku.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Aby skonfigurować projekt SharePointCommands
  
1.  W **SharePointCommands** projekt, Dodaj plik kodu, który ma nazwę polecenia.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów na **SharePointCommands** węzła projektu, a następnie wybierz **Dodaj odwołanie**.  
  
3.  Na **rozszerzenia** karcie, zaznacz pola wyboru dla następujących zestawów, a następnie kliknij przycisk Wybierz **OK** przycisku  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="define-the-custom-deployment-step"></a>Definiowanie niestandardowego kroku wdrożenia
 Utwórz klasę, która definiuje krok uaktualniania wdrożenia. Aby zdefiniować kroku wdrożenia implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfejsu. Implementuje ten interfejs umożliwia zdefiniowanie niestandardowego kroku wdrożenia.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Aby zdefiniować niestandardowego kroku wdrożenia  
  
1.  W **DeploymentStepExtension** projektu, otwórz plik kodu UpgradeStep, a następnie wklej następujący kod do niego.  
  
    > [!NOTE]  
    >  Po dodaniu tego kodu, projektu mają błędy kompilacji, ale będzie zniknie po dodaniu kod w kolejnych krokach.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Tworzenie konfiguracji wdrażania, która obejmuje krok niestandardowe wdrożenie
 Tworzenie rozszerzenia projektu dla konfiguracji wdrażania nowych obejmuje kilka kroków wdrażania wbudowanych i nowy krok uaktualniania wdrożenia. Tworząc to rozszerzenie, możesz pomóc deweloperom programu SharePoint do użycia w projektach programu SharePoint krok uaktualniania wdrożenia.  
  
 Aby utworzyć konfigurację wdrożenia implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu. Implementuje ten interfejs umożliwia tworzenie rozszerzenia projektu SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Aby utworzyć konfigurację wdrożenia  
  
1.  W **DeploymentStepExtension** projektu, otwórz plik kodu DeploymentConfigurationExtension, a następnie wklej następujący kod do niego.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Tworzenie niestandardowych poleceń programu SharePoint
 Utwórz dwa polecenia niestandardowych, które wywołują modelu obiektów serwera dla programu SharePoint. Jedno polecenie Określa, czy rozwiązanie zostało już wdrożone; inne polecenia uaktualnia rozwiązania.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować polecenia SharePoint  
  
1.  W **SharePointCommands** projektu, otwórz plik kodu polecenia, a następnie wklej następujący kod do niego.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie w prezentacji, całego kodu niestandardowego kroku wdrożenia i poleceń programu SharePoint są teraz w projektach. Je, aby upewnić się, że ich Kompiluj bez błędów kompilacji.  
  
#### <a name="to-build-the-projects"></a>Tworzenie projektów  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **DeploymentStepExtension** projektu, a następnie wybierz pozycję **kompilacji**.  
  
2.  Otwórz menu skrótów **SharePointCommands** projektu, a następnie wybierz pozycję **kompilacji**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Utwórz pakiet VSIX, aby wdrożyć rozszerzenie
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakietu VSIX, modyfikując plik Source.Extension.vsixmanifest,a w projekcie VSIX. Następnie utwórz pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i tworzenia pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**w obszarze **UpgradeDeploymentStep** projektu, otwórz menu skrótów **source.extension.vsixmanifest** pliku, a następnie wybierz pozycję  **Otwórz**.  
  
     Visual Studio otwiera plik w edytorze manifestu. Plik Source.Extension.vsixmanifest,a stanowi podstawę dla wszystkich pakietów VSIX wymaga plik extension.vsixmanifest. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **uaktualnienia kroku wdrożenia dla projektów SharePoint**.  
  
3.  W **autora** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **zawiera krok niestandardowe wdrożenie uaktualnienia, który może być używana w SharePoint — projekty**.  
  
5.  W **zasoby** karta edytora, wybierz **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** wybierz **DeploymentStepExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
9. W edytorze manifestu wybierz **nowy** przycisk ponownie.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
10. W **typu** listy, wprowadź **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Ten element określa rozszerzenie niestandardowe, które chcesz uwzględnić w rozszerzenie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [zasobów — Element (schemat VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
12. W **projektu** wybierz **SharePointCommands**, a następnie wybierz pozycję **OK** przycisku.  
  
13. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.  
  
14. Upewnij się, że folder wyjściowy kompilacji projektu UpgradeDeploymentStep zawiera teraz UpgradeDeploymentStep.vsix pliku.  
  
     Domyślnie jest folder wyjściowy kompilacji... folder \bin\Debug folder zawierający plik projektu.  
  
## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Przygotowanie do testowania krok uaktualniania wdrożenia
 Aby przetestować krok uaktualniania wdrożenia, należy najpierw wdrożyć przykładowe rozwiązanie z witryną programu SharePoint. Uruchom profilowanie rozszerzenie w eksperymentalne wystąpienie programu Visual Studio. Następnie utwórz definicji listy i wystąpienie listy na potrzeby testowania kroku wdrożenia, a następnie wdrożyć je w witrynie programu SharePoint. Następnie zmodyfikuj definicji listy i wystąpienia listy i ponownie wdrożyć je, aby zademonstrować, jak domyślny proces wdrażania powoduje zastąpienie rozwiązań w witrynie programu SharePoint.  
  
 W dalszej części tego przewodnika będą wprowadzane zmiany definicji listy i wystąpienia listy, a następnie będzie ich uaktualnieniem w witrynie programu SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia  
  
1.  Uruchom ponownie program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie UpgradeDeploymentStep.  
  
2.  W projekcie DeploymentStepExtension, otwórz plik kodu UpgradeStep, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `CanExecute` i `Execute` metody.  
  
3.  Rozpocznij debugowanie, wybierając **F5** klucza lub, w menu pasek wybierania **debugowania** > **Rozpocznij debugowanie**.  
  
4.  Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade kroku wdrożenia dla SharePoint Projects\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Krok uaktualniania wdrożenia przetestujesz, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Aby utworzyć projekt programu SharePoint z definicji listy i wystąpienia listy  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **pliku** > **nowy** > **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** węzła lub **Visual Basic** węzła, rozwiń węzeł **programu SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.  
  
3.  W górnej części okna dialogowego, upewnij się, że **.NET Framework 3.5** pojawią się na liście wersji programu .NET Framework.  
  
     Projekty dla [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] wymagają tej wersji programu .NET Framework.  
  
4.  Na liście szablony projektów, wybierz **projektu programu SharePoint 2010**, nazwij projekt **EmployeesListDefinition**, a następnie wybierz pozycję **OK** przycisku.  
  
5.  W **Kreator dostosowania programu SharePoint**, wprowadź adres URL witryny, która ma być używany na potrzeby debugowania.  
  
6.  W obszarze **co to jest poziom zaufania dla tego rozwiązania SharePoint**, wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
    > [!NOTE]  
    >  Krok uaktualniania wdrożenia nie obsługuje rozwiązania w trybie piaskownicy.  
  
7.  Wybierz **Zakończ** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt EmployeesListDefinition.  
  
8.  Otwórz menu skrótów projektu EmployeesListDefinition, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
9. W **Dodaj nowy element - EmployeesListDefinition** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
10. Wybierz **listy** element szablonu, nazwy elementu **listy pracowników**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Zostanie wyświetlony Kreator dostosowania programu SharePoint  
  
11. Na **wybierz ustawienia listy** strony, należy sprawdzić następujące ustawienia, a następnie wybierz **Zakończ** przycisk:  
  
    1.  **Lista pracowników** pojawia się w **jaką nazwę chcesz wyświetlić listy?** pole.  
  
    2.  **Tworzenie na podstawie listy można dostosowywać:** wybrano opcję.  
  
    3.  **Domyślne (pusta)** jest wybierany w **tworzenie na podstawie listy można dostosowywać:** listy.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy element listy pracowników z kolumnę tytułu i SIS pusty i otworzy w Projektancie listy.  
  
12. W Projektancie listy na **kolumn** , wybierz pozycję **wpisz nazwę nowej lub istniejącej kolumny** wiersza, a następnie dodaj następujących kolumn w **Nazwa wyświetlana kolumna** listy:  
  
    1.  Imię  
  
    2.  firmy  
  
    3.  Telefon służbowy  
  
    4.  Wiadomości e-Mail  
  
13. Zapisz wszystkie pliki, a następnie zamknij projektanta listy.  
  
14. W **Eksploratora rozwiązań**, rozwiń węzeł **listy pracowników** węzeł, a następnie rozwiń węzeł **wystąpienia listy pracowników** węzeł podrzędny.  
  
15. W *Elements.xml* pliku, Zastąp domyślne XML w tym pliku następujący kod XML. Plik XML zmienia nazwę na liście, aby **pracowników** i dodaje informacje dotyczące pracownika, który ma o nazwie Jan Kowalski.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Zapisz i Zamknij *Elements.xml* pliku.  
  
17. Otwórz menu skrótów projektu EmployeesListDefinition, a następnie wybierz pozycję **Otwórz** lub **właściwości**.  
  
     Otwiera właściwości projektanta.  
  
18. Na **SharePoint** kartę, wyczyść **wycofać automatycznie po debugowaniu** pole wyboru, a następnie Zapisz właściwości.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Wdrażanie definicji listy i wystąpienia listy  
  
1.  W **Eksploratora rozwiązań**, wybierz **EmployeesListDefinition** węzła projektu.  
  
2.  W **właściwości** okna, upewnij się, że **aktywnej konfiguracji wdrożenia** właściwość jest ustawiona na **domyślne**.  
  
3.  Wybierz **F5** klucza, lub na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.  
  
4.  Sprawdź pomyślnie kompilacji projektu, że przeglądarka sieci web otwiera się do witryny programu SharePoint, która **wymieniono** element paska Szybkie uruchamianie zawiera nowe **pracowników** listy, a  **Pracownicy** lista zawiera wpis dla Jan Kowalski.  
  
5.  Zamknij przeglądarkę sieci web.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Do modyfikowania listy definicji i wystąpienia listy i wdróż je ponownie  
  
1.  W projekcie EmployeesListDefinition Otwórz *Elements.xml* pliku, który jest elementem podrzędnym **wystąpienia listy pracowników** elementu projektu.  
  
2.  Usuń `Data` elementu i jego elementów podrzędnych, aby usunąć wpis dla Jan Kowalski z listy.  
  
     Po zakończeniu plik powinien zawierać następujący kod XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Zapisz i Zamknij *Elements.xml* pliku.  
  
4.  Otwórz menu skrótów **listy pracowników** elementu projektu, a następnie wybierz pozycję **Otwórz** lub **właściwości**.  
  
5.  W Projektancie listy wybierz **widoków** kartę.  
  
6.  W **wybrane kolumny** wybierz **załączników**, a następnie wybierz pozycję < klucza można przenieść tej kolumny, aby **dostępne kolumny** listy.  
  
7.  Powtórz poprzedni krok, aby przenieść **Telefon służbowy** kolumny z **wybrane kolumny** listy, aby **dostępne kolumny** listy.  
  
     Ta akcja usuwa te pola z domyślny widok **pracowników** listy w witrynie programu SharePoint.  
  
8.  Rozpocznij debugowanie, wybierając **F5** klucza lub, w menu pasek wybierania **debugowania** > **Rozpocznij debugowanie**.  
  
9. Sprawdź, czy **konflikty wdrażania** zostanie wyświetlone okno dialogowe.  
  
     To okno dialogowe jest wyświetlany, gdy próbuje wdrożyć rozwiązanie (wystąpienia listy) programu Visual Studio w witrynie programu SharePoint, do którego został już wdrożony tego rozwiązania. To okno dialogowe nie będzie wyświetlane podczas wykonywania kroku uaktualniania wdrożenia później w tym przewodniku.  
  
10. W **konflikty wdrażania** oknie dialogowym wybierz **automatycznie rozwiązać** przycisk opcji.  
  
     Visual Studio usuwa wystąpienie listy w witrynie programu SharePoint, wdraża elementu listy w projekcie, a następnie otwiera witrynę programu SharePoint.  
  
11. W **wymieniono** sekcji paska szybkiego uruchamiania wybierz **pracowników** listy, a następnie sprawdź następujące informacje:  
  
    -   **Załączników** i **Telefon domowy** kolumn nie są wyświetlane w tym widoku listy.  
  
    -   Lista jest pusta. Kiedy używać **domyślne** konfiguracji wdrożenia na ponownego wdrożenia rozwiązania, **pracowników** listy został zastąpiony nową listę pusta w projekcie.  
  
## <a name="test-the-deployment-step"></a>Testowanie kroku wdrożenia
 Teraz można przystąpić do testowania krok uaktualniania wdrożenia. Najpierw dodaj element do wystąpienia listy w programie SharePoint. Następnie zmiany definicji listy i wystąpienia listy, uaktualnij je w witrynie programu SharePoint i upewnij się, że krok uaktualniania wdrożenia nie zastąpienie nowy element.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Aby ręcznie dodać element do listy  
  
1.  Na Wstążce w witrynie programu SharePoint w obszarze **narzędzia listy** , wybierz pozycję **elementów** kartę.  
  
2.  W **nowy** grupy, wybierz **nowy element**.  
  
     Alternatywnie, można wybrać **Dodaj nowy element** łącze w samej listy elementów.  
  
3.  W **pracowników — nowy element** okna w **tytuł** wprowadź **Menedżera urządzeń**.  
  
4.  W **imię** wprowadź **Adama**.  
  
5.  W **firmy** wpisz **Contoso**.  
  
6.  Wybierz **zapisać** przycisku, sprawdź, czy nowy element jest widoczny na liście, a następnie zamknij przeglądarkę sieci web.  
  
     W dalszej części tego przewodnika użyjesz ten element, aby sprawdzić, czy krok uaktualniania wdrożenia nie zastąpić zawartości tej listy.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Aby przetestować krok uaktualniania wdrożenia  
  
1.  W eksperymentalne wystąpienie programu Visual Studio w **Eksploratora rozwiązań**, otwórz menu skrótów **EmployeesListDefinition** węzła projektu, a następnie wybierz **właściwości**.  
  
     Zostanie otwarty Edytor właściwości/projektanta.  
  
2.  Na **SharePoint** ustaw **aktywnej konfiguracji wdrożenia** właściwości **uaktualnienia**.  
  
     Ta konfiguracja niestandardowe wdrożenie obejmuje nowy krok uaktualniania wdrożenia.  
  
3.  Otwórz menu skrótów **listy pracowników** elementu projektu, a następnie wybierz pozycję **właściwości** lub **Otwórz**.  
  
     Zostanie otwarty Edytor właściwości/projektanta.  
  
4.  Na **widoków** , wybierz pozycję **E-Mail** kolumny, a następnie wybierz pozycję **<** klucza można przenieść tej kolumny z **wybrane kolumny**listy, aby **dostępne kolumny** listy.  
  
     Ta akcja usuwa te pola z domyślny widok **pracowników** listy w witrynie programu SharePoint.  
  
5.  Rozpocznij debugowanie, wybierając **F5** klucza lub, w menu pasek wybierania **debugowania** > **Rozpocznij debugowanie**.  
  
6.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `CanExecute` metody.  
  
7.  Wybierz **F5** klucza ponownie, lub na pasku menu wybierz **debugowania** > **Kontynuuj**.  
  
8.  Sprawdź, czy kod zatrzymuje się na punkt przerwania ustawionych wcześniej w `Execute` metody.  
  
9. Wybierz **F5** klucza, lub na pasku menu wybierz **debugowania** > **Kontynuuj** raz ostatni.  
  
     Przeglądarki sieci web otwiera witrynę programu SharePoint.  
  
10. W **wymieniono** sekcji obszaru Szybkie uruchamianie wybierz **pracowników** listy, a następnie sprawdź następujące informacje:  
  
    -   Element, który ręcznie dodane wcześniej (dla Adama, Menedżer urządzeń) jest nadal na liście.  
  
    -   **Telefon służbowy** i **adres E-mail** kolumn nie są wyświetlane w tym widoku listy.  
  
     **Uaktualnienia** konfiguracji wdrożenia modyfikuje istniejące **pracowników** wystąpienia listy w witrynie programu SharePoint. Jeśli używasz **domyślne** konfiguracji wdrożenia zamiast **uaktualnienia** konfiguracji, może wystąpić konflikt wdrażania. Visual Studio może rozwiązać konflikt, zastępując **pracowników** listy i element Adama, Menedżer urządzeń zostaną usunięte.  
  
## <a name="clean-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim
 Po zakończeniu testowania krok uaktualniania wdrożenia, usunąć wystąpienia listy i definicji listy z witryny programu SharePoint i usuń rozszerzenie kroku wdrożenia w programie Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Aby usunąć wystąpienia listy z witryny programu SharePoint  
  
1.  Otwórz **pracowników** listy w witrynie programu SharePoint, jeśli lista nie jest jeszcze otwarty.  
  
2.  Na Wstążce w witrynie programu SharePoint, wybierz **narzędzia listy** karcie, a następnie wybierz pozycję **listy** kartę.  
  
3.  W **ustawienia** grupy, wybierz **ustawień listy** elementu.  
  
4.  W obszarze **uprawnienia i zarządzanie**, wybierz **Usuń tę listę** polecenia, wybierz **OK** potwierdzenie Wysyłanie listy do Kosza, a następnie zamknij sieci web Przeglądarka.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Aby usunąć definicji listy z witryny programu SharePoint  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **kompilacji** > **Wycofaj**.  
  
     Visual Studio wycofuje definicji listy z witryny programu SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenia  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **uaktualnienia kroku wdrożenia dla projektów SharePoint**, a następnie wybierz pozycję **Odinstaluj** polecenia.  
  
3.  W oknie dialogowym wybierz **tak** aby upewnić się, że chcesz odinstalować rozszerzenia, a następnie wybierz pozycję **Uruchom ponownie teraz** aby ukończyć dezinstalację.  
  
4.  Zamknij oba wystąpienia programu Visual Studio (eksperymentalne wystąpienie i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie UpgradeDeploymentStep).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
