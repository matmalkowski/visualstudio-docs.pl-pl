---
title: "Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 2 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 96f6e6f27938635628db66f2a6eb58a56cee0d18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>Wskazówki: tworzenie niestandardowej akcji elementu projektu z Szablonem elementu, Część 2
  Po zdefiniowaniu niestandardowego typu elementu projektu SharePoint i skojarzyć go z szablonu elementów programu Visual Studio, można również podać Kreatora szablonu. Kreator służy do zbierania informacji od użytkowników, gdy będą oni używać szablonu można dodać nowe wystąpienie elementu projektu do projektu. Informacje zbierane można zainicjować elementu projektu.  
  
 W tym przewodniku kreatora zostaną dodane do akcji niestandardowej elementu projektu, który jest przedstawiona w [wskazówki: Tworzenie elementu projektu akcji niestandardowych z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Gdy użytkownik dodaje element akcji niestandardowej projektu do projektu SharePoint, Kreator zbiera informacje o akcji niestandardowej (takiej jak lokalizacji i adres URL, można przejść do, gdy użytkownik końcowy wybierze go) i dodaje te informacje do pliku Elements.xml w nowym Element projektu.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie kreatora niestandardowego skojarzonego z szablonem elementu typu elementu projektu SharePoint.  
  
-   Definiowanie niestandardowego kreatora interfejsu użytkownika, podobny wbudowanych kreatorów dla elementów projektu SharePoint w Visual Studio.  
  
-   Przy użyciu parametrów wymiennych zainicjować pliki projektu programu SharePoint z danymi, które można zbierać w kreatorze.  
  
-   Debugowanie i testowanie kreatora.  
  
> [!NOTE]  
>  Możesz pobrać przykład, który zawiera projekty ukończone, kodu i innych plików w ramach tego przewodnika z następującej lokalizacji: [pliki projektu dla wskazówki rozszerzalność narzędzi SharePoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać tego przewodnika, należy najpierw utworzyć rozwiązanie CustomActionProjectItem, wykonując [wskazówki: Tworzenie elementu projektu akcji niestandardowych z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Należy również następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Windows, SharePoint i Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio SDK. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrażania elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Kreatorzy szablonów projektów i elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: użycie kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md) i <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.  
  
-   Akcje niestandardowe w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Akcja niestandardowa](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="creating-the-wizard-project"></a>Tworzenie projektu Kreatora  
 W tym przewodniku, należy dodać projekt do rozwiązania CustomActionProjectItem, który został utworzony w [wskazówki: Tworzenie elementu projektu akcji niestandardowych z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Zostaną zaimplementowane <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu i zdefiniuj Kreatora interfejsu użytkownika w tym projekcie.  
  
#### <a name="to-create-the-wizard-project"></a>Aby utworzyć projekt Kreatora  
  
1.  W programie Visual Studio Otwórz rozwiązanie CustomActionProjectItem  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **Windows** węzła.  
  
4.  W górnej części **nowy projekt** okna dialogowego upewnij się, że **.NET Framework 4.5** jest wybrane na liście wersji programu .NET Framework.  
  
5.  Wybierz **Biblioteka kontrolek użytkownika WPF** projektu szablonu, nazwy projektu **ItemTemplateWizard**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **ItemTemplateWizard** projektu do rozwiązania.  
  
6.  Usuń element UserControl1 z projektu.  
  
## <a name="configuring-the-wizard-project"></a>Konfigurowanie projektu Kreatora  
 Przed utworzeniem kreatora, należy dodać okno Windows Presentation Foundation (WPF), plik kodu i odwołania do zestawów do projektu.  
  
#### <a name="to-configure-the-wizard-project"></a>Aby skonfigurować projekt Kreatora  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów z **ItemTemplateWizard** węzła projektu, a następnie wybierz **właściwości**.  
  
2.  W **projektanta projektu**, upewnij się, że platforma docelowa jest ustawiona na .NET Framework 4.5.  
  
     Projekty Visual C#, tę wartość można ustawić na **aplikacji** kartę. Projekty Visual Basic tę wartość można ustawić na **skompilować** kartę. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  W **ItemTemplateWizard** projekt, Dodaj **okna (WPF)** elementu do projektu, a następnie nazwą elementu **WizardWindow**.  
  
4.  Dodaj dwa pliki kodu o nazwach CustomActionWizard i ciągów.  
  
5.  Otwórz menu skrótów **ItemTemplateWizard** projektu, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
6.  W **Menedżera odwołań - ItemTemplateWizard** okna dialogowego, w obszarze **zestawy** węzła, wybierz **rozszerzenia** węzła.  
  
7.  Zaznacz pola wyboru obok następujące zestawy, a następnie wybierz pozycję **OK** przycisk:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  W **Eksploratora rozwiązań**w **odwołania** wybierz folder dla projektu ItemTemplateWizard **EnvDTE** odwołania.  
  
9. W **właściwości** okna, zmień wartość **Osadź typy międzyoperacyjne** właściwości **False**.  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>Definiowanie domyślnej lokalizacji i ciągi identyfikatorów dla akcji niestandardowych  
 Wszystkie akcje niestandardowe ma położenie i identyfikator, który jest określony w `GroupID` i `Location` atrybuty `CustomAction` elementu w pliku Elements.xml. W tym kroku należy zdefiniować część prawidłowe ciągi tych atrybutów w projekcie ItemTemplateWizard. Po ukończeniu tego przewodnika tych ciągów są zapisywane w pliku Elements.xml w elemencie projektu akcji niestandardowej, gdy użytkownik określi lokalizację i identyfikator w kreatorze.  
  
 Dla uproszczenia w tym przykładzie obsługuje tylko dostępne domyślne lokalizacje i identyfikatorów. Aby uzyskać pełną listę, zobacz [domyślne lokalizacje akcji niestandardowych i identyfikatory](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Aby zdefiniować domyślną lokalizację i ciągi identyfikatorów  
  
1.  Otwórz.  
  
2.  W **ItemTemplateWizard** projekt, Zastąp kod w pliku kodu ciągów z następującym kodem.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>Tworzenie kreatora interfejsu użytkownika  
 Dodaj XAML, aby zdefiniować interfejsu użytkownika kreatora i Dodaj kod powiązać niektóre formanty w Kreatorze ciągi identyfikatorów. Kreator tworzenia podobny wbudowanych kreatora dla projektów programu SharePoint w Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Aby utworzyć Kreator interfejsu użytkownika  
  
1.  W **ItemTemplateWizard** projektu, otwórz menu skrótów **WizardWindow.xaml** pliku, a następnie wybierz pozycję **Otwórz** można otworzyć okna w projektancie.  
  
2.  W widoku XAML zastąpić bieżący XAML następujące XAML. XAML definiuje interfejsu użytkownika, który zawiera nagłówek, sterowania służący do określania zachowania akcji niestandardowej, a przyciski nawigacji w dolnej części okna.  
  
    > [!NOTE]  
    >  Projekt ma błędy kompilacji, po dodaniu tego kodu. Te błędy zniknie po dodaniu kod w kolejnych krokach.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  Okno jest tworzony w tym języku XAML jest pochodną <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy podstawowej. Po dodaniu niestandardowe okno dialogowe WPF do programu Visual Studio, firma Microsoft zaleca, pochodzi z okna dialogowego z tej klasy mają stylów spójne z innych okien dialogowych w programie Visual Studio i aby uniknąć problemów, które mogłyby wystąpić z modalnych okien dialogowych. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie modalnych okien dialogowych](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Jeśli projektujesz projektu Visual Basic, Usuń `ItemTemplateWizard` przestrzeni nazw z `WizardWindow` nazwę klasy w `x:Class` atrybutu `Window` elementu. Stanem tego elementu jest w pierwszym wierszu pliku XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien przypominać następujący kod:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  W pliku CodeBehind dla pliku WizardWindow.xaml Zastąp bieżący kod następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>Implementowanie Kreatora  
 Zdefiniuj funkcje kreatora zaimplementowanie <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.  
  
#### <a name="to-implement-the-wizard"></a>Aby zaimplementować Kreatora  
  
1.  W **ItemTemplateWizard** otwarciu projektu **CustomActionWizard** code pliku, a następnie zastąp bieżący kod w tym pliku następującym kodem:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie w prezentacji, całego kodu dla kreatora znajduje się teraz w projekcie. Skompiluj projekt, aby upewnić się, że skompilowany bez błędów.  
  
#### <a name="to-build-your-project"></a>Aby utworzyć projekt  
  
1.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
## <a name="associating-the-wizard-with-the-item-template"></a>Kojarzenie kreatora z szablonu elementu  
 Teraz, gdy zostały zaimplementowane kreatora, musisz skojarzyć go z **Akcja niestandardowa** szablon elementu, wykonując trzech głównych kroków:  
  
1.  Zaloguj się przy użyciu silnej nazwy zestawu kreatora.  
  
2.  Pobierz token klucza publicznego zestawu kreatora.  
  
3.  Dodaj odwołanie do zestawu kreatora w pliku .vstemplate **Akcja niestandardowa** szablon elementu.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Aby zarejestrować Kreatora zestawu o silnej nazwie  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów z **ItemTemplateWizard** węzła projektu, a następnie wybierz **właściwości**.  
  
2.  Na **podpisywanie** wybierz opcję **Podpisz zestaw** pole wyboru.  
  
3.  W **wybierz plik klucza o silnej nazwie** wybierz  **\<nowy... >**.  
  
4.  W **tworzenie silnej nazwy klucza** okna dialogowego wprowadź nazwę, usuń zaznaczenie **ochrony pliku klucza przy użyciu hasła** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
5.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Aby uzyskać klucz publiczny tokenu dla zestawu Kreatora  
  
1.  W oknie Wiersz polecenia programu Visual Studio, uruchom następujące polecenie, zastępując *PathToWizardAssembly* z pełną ścieżką do skompilowany zestaw ItemTemplateWizard.dll ItemTemplateWizard projektu na komputerze komputer.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Token klucza publicznego zestawu ItemTemplateWizard.dll są zapisywane w oknie Wiersz polecenia programu Visual Studio.  
  
2.  Nie zamykaj okna Wiersz polecenia programu Visual Studio. Będziesz potrzebować token klucza publicznego do wykonania w następnej procedurze.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Aby dodać odwołanie do zestawu kreatora w pliku .vstemplate  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **ItemTemplate** węzła projektu, a następnie otwórz plik ItemTemplate.vstemplate.  
  
2.  Pod koniec pliku, Dodaj następujący `WizardExtension` element między `</TemplateContent>` i `</VSTemplate>` tagów. Zastąp *YourToken* wartość `PublicKeyToken` atrybutu z tokenem klucza publicznego, które zostały uzyskane w poprzedniej procedurze.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Aby uzyskać więcej informacji na temat `WizardExtension` elementu, zobacz [wizardextension — Element &#40; Szablony Visual Studio &#41; ](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Zapisz i zamknij plik.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Dodawanie do pliku Elements.xml w szablonie elementu parametry wymienne  
 Dodaj kilka parametrów wymiennych do pliku Elements.xml w projekcie ItemTemplate. Te parametry są inicjowane w `PopulateReplacementDictionary` metoda `CustomActionWizard` klasy, która wcześniej zdefiniowany. Gdy użytkownik dodaje niestandardowa akcja elementu projektu do projektu, Visual Studio automatycznie zastępuje tych parametrów w pliku Elements.xml nowego elementu projektu z wartościami, które są określone w kreatorze.  
  
 Parametr wymienny to token, który rozpoczyna się i kończy się znakiem dolara ($). Oprócz Definiowanie wymienne parametry, można użyć wbudowanych parametry systemu projektu SharePoint definiuje i inicjuje. Aby uzyskać więcej informacji, zobacz [parametry wymienne](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Aby dodać do pliku Elements.xml parametry wymienne  
  
1.  W projekcie ItemTemplate Zastąp zawartość pliku Elements.xml następujący kod XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Nowy kod XML zmienia wartości `Id`, `GroupId`, `Location`, `Description`, i `Url` atrybuty do parametry wymienne.  
  
2.  Zapisz i zamknij plik.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Dodawanie kreatora do pakietu VSIX  
 W pliku source.extension.vsixmanifest w projekcie VSIX dodać odwołanie do projektu kreatora z pakietem VSIX, który zawiera element projektu jest wdrożona.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Aby dodać kreatora do pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów z **source.extension.vsixmanifest** pliku w projekcie CustomActionProjectItem, a następnie wybierz pozycję **Otwórz** otworzyć plik w edytorze manifestu.  
  
2.  W edytorze manifestu wybierz **zasoby** , a następnie wybierz **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
3.  W **typu** wybierz **Microsoft.VisualStudio.Assembly**.  
  
4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
5.  W **projektu** wybierz **ItemTemplateWizard**, a następnie wybierz pozycję **OK** przycisku.  
  
6.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.  
  
## <a name="testing-the-wizard"></a>Testowanie Kreatora  
 Teraz można przystąpić do testowania kreatora. Najpierw Rozpocznij debugowanie rozwiązania CustomActionProjectItem w eksperymentalne wystąpienie programu Visual Studio. Następnie należy przetestować kreatora dla elementu projektu Akcja niestandardowa w projekcie programu SharePoint w eksperymentalne wystąpienie programu Visual Studio. Na koniec Skompiluj i uruchom projekt programu SharePoint, aby sprawdzić, czy akcja niestandardowa działa zgodnie z oczekiwaniami.  
  
#### <a name="to-start-to-debug-the-solution"></a>Aby rozpocząć debugowanie rozwiązania  
  
1.  Uruchom ponownie program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie CustomActionProjectItem.  
  
2.  W projekcie ItemTemplateWizard, otwórz plik kodu CustomActionWizard, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `RunStarted` metody.  
  
3.  Na pasku menu wybierz **debugowania**, **wyjątki**.  
  
4.  W **wyjątki** okna dialogowego upewnij się, że **wyrzuconych** i **nieobsługiwanych przez użytkownika** pól wyboru dla **wspólnego języka środowiska uruchomieniowego wyjątki**zostaną wyczyszczone, a następnie wybierz **OK** przycisku.  
  
5.  Rozpocznij debugowanie, wybierając klawisz F5 lub na pasku menu, wybierając **debugowania**, **Rozpocznij debugowanie**.  
  
     Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 projektu akcji i uruchamia eksperymentalne wystąpienie programu Visual Studio. Element projektu przetestujesz, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Aby przetestować kreatora w programie Visual Studio  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Rozwiń węzeł **Visual C#** lub **Visual Basic** węzeł (w zależności od języka obsługującego szablonu elementu), rozwiń węzeł **SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.  
  
3.  Na liście szablony projektów, wybierz **projektu programu SharePoint 2010**, nazwij projekt **CustomActionWizardTest**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  W **Kreator dostosowania programu SharePoint**, wprowadź adres URL witryny, która ma być używany na potrzeby debugowania, a następnie wybierz pozycję **Zakończ** przycisku.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła projektu, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
6.  W **Dodaj nowy element - CustomItemWizardTest** okna dialogowego rozwiń **SharePoint** węzeł, a następnie rozwiń węzeł **2010** węzła.  
  
7.  Na liście elementów projektu, wybierz **Akcja niestandardowa** elementu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
8.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `RunStarted` metody.  
  
9. Kontynuowania debugowania projektu, wybierając klawisz F5 lub z menu, wybierając **debugowania**, **Kontynuuj**.  
  
     Zostanie wyświetlony Kreator dostosowania programu SharePoint.  
  
10. W obszarze **lokalizacji**, wybierz **listy edytować** przycisk opcji.  
  
11. W **identyfikator grupy** wybierz **komunikacji**.  
  
12. W **tytuł** wprowadź **SharePoint Developer Center**.  
  
13. W **opis** wprowadź **otwiera witrynę sieci Web programu SharePoint Developer Center**.  
  
14. W **adres URL** wprowadź **http://msdn.microsoft.com/sharepoint/default.aspx**, a następnie wybierz pozycję **Zakończ** przycisku.  
  
     Visual Studio dodaje element o nazwie **CustomAction1** do projektu i otwiera Elements.xml plik w edytorze. Sprawdź, czy Elements.xml zawiera wartości, które zostały określone w kreatorze.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Aby przetestować akcji niestandardowej w programie SharePoint  
  
1.  W eksperymentalnym wystąpieniu programu Visual Studio, wybierz klawisz F5 lub, na pasku menu **debugowania**, **Rozpocznij debugowanie**.  
  
     Spakowanego i wdrożonych w witrynie programu SharePoint, określony przez akcję niestandardową **adres URL witryny** Otwiera właściwości projektu i przeglądarki sieci web do domyślnej strony w tej lokacji.  
  
    > [!NOTE]  
    >  Jeśli **wyłączenia debugowania skryptu** zostanie wyświetlone okno dialogowe, wybierz **tak** przycisku.  
  
2.  W obszarze listy witryny programu SharePoint, wybierz **zadania** łącza.  
  
     **Zadania — wszystkie zadania** zostanie wyświetlona strona.  
  
3.  Na **narzędzia listy** kartę na Wstążce wybierz **listy** kartę, a następnie w **ustawienia** grupy, wybierz **ustawień listy**.  
  
     **Ustawień listy** zostanie wyświetlona strona.  
  
4.  W obszarze **komunikacji** pozycji w górnej części strony, wybierz **SharePoint Developer Center** łącza, upewnij się, że przeglądarka otworzy http://msdn.microsoft.com/sharepoint/ witryny sieci Web default.aspx, a następnie zamknij przeglądarkę.  
  
## <a name="cleaning-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim  
 Po zakończeniu testowania elementu projektu, należy usunąć szablonu elementu projektu z eksperymentalne wystąpienie programu Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić na komputerze deweloperskim  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **elementu projektu akcji niestandardowych** rozszerzenia, a następnie wybierz pozycję **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisk, aby potwierdzić, że chcesz odinstalować rozszerzenia, a następnie wybierz pozycję **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.  
  
4.  Zamknij oba wystąpienia programu Visual Studio (eksperymentalne wystąpienie i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie CustomActionProjectItem).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Definiowanie typów elementów projektu SharePoint niestandardowych](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Porady: Korzystanie z kreatora z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Identyfikatory i domyślne lokalizacje akcji niestandardowej](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  