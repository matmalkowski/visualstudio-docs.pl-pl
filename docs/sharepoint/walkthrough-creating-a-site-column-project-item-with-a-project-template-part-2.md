---
title: 'Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2 | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0aa938d41540229d6cd91598968f104b3fa3a7be
ms.sourcegitcommit: cc88ccc6aacebe497899fab05d243a65053e194c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2"></a>Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 2
  Po zdefiniowaniu niestandardowego typu elementu projektu SharePoint i skojarzyć go z szablonem projektu w programie Visual Studio, można również podać Kreatora szablonu. Kreator służy do zbierania informacji od użytkowników, gdy będą oni używać szablonu można utworzyć nowy projekt, który zawiera element projektu. Informacje zbierane można zainicjować elementu projektu.  
  
 W tym przewodniku kreatora zostanie dodany do szablonu projektu kolumn witryny przedstawionej w [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Gdy użytkownik tworzy projekt kolumny witryny, Kreator zbiera informacje o kolumny witryny (takie jak jego typu podstawowego i grupy) i dodaje te informacje do pliku Elements.xml w nowym projekcie.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie kreatora niestandardowego typu do elementu projektu SharePoint, który jest skojarzony z szablonem projektu.  
  
-   Definiowanie niestandardowego kreatora interfejsu użytkownika, który jest podobny wbudowanych kreatorów dla projektów programu SharePoint w Visual Studio.  
  
-   Utworzenie dwóch *polecenia SharePoint* służące do wywołania w lokalnej witrynie programu SharePoint podczas działania kreatora. Polecenia SharePoint są metody, które mogą służyć przez rozszerzenia programu Visual Studio do wywoływania interfejsów API w modelu obiektów serwera programu SharePoint. Aby uzyskać więcej informacji, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Przy użyciu parametrów wymiennych zainicjować pliki projektu programu SharePoint z danymi, które można zbierać w kreatorze.  
  
-   Tworzenie nowego pliku .snk — w każdym nowe wystąpienie projektu kolumny witryny. Ten plik jest używany do podpisywania projektu danych wyjściowych, aby zestaw rozwiązania programu SharePoint można wdrożyć w globalnej pamięci podręcznej zestawów.  
  
-   Debugowanie i testowanie kreatora.  
  
> [!NOTE]  
> Serii próbki przepływów pracy, zobacz [przykłady przepływu pracy programu SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać tego przewodnika, należy najpierw utworzyć rozwiązanie SiteColumnProjectItem, wykonując [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Należy również następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Windows, SharePoint i Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio SDK. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrażania elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Kreatorzy szablonów projektów i elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: użycie kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md) i <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.  
  
-   Kolumny witryny w programie SharePoint. Aby uzyskać więcej informacji, zobacz [kolumn](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a> Opis składników Kreatora  
 Kreator przedstawionej w tym przewodniku zawiera kilka składników. W poniższej tabeli opisano te składniki.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Kreator implementacji|To jest klasa o nazwie `SiteColumnProjectWizard`, który implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu. Ten interfejs definiuje metody, które wywołuje program Visual Studio, gdy Kreator uruchamia zakończeniu i w określonym czasie podczas Kreator uruchamia.|  
|Kreator interfejsu użytkownika|Jest to okno na architekturach WPF, o nazwie `WizardWindow`. Znajdują się w nim dwa kontrolek użytkownika o nazwie `Page1` i `Page2`. Te kontrolki użytkownika reprezentować dwie strony kreatora.<br /><br /> W tym przewodniku <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metod wdrażania Kreator wyświetli Kreatora interfejsu użytkownika.|  
|Kreator modelu danych|Jest to klasy pośredniczącej, o nazwie `SiteColumnWizardModel`, który zapewnia warstwę między Kreatora interfejsu użytkownika, jak i implementację kreatora. W tym przykładzie używa tej klasy, aby ułatwić abstrakcji implementacji kreatora i Kreator interfejsu użytkownika z innych; Ta klasa nie jest wymaganym składnikiem wszystkich kreatorów.<br /><br /> W tym przewodniku przekazuje implementacji kreatora `SiteColumnWizardModel` obiektu w oknie kreatora wyświetlanych Kreatora interfejsu użytkownika. Kreator interfejsu użytkownika używa metody tego obiektu do zapisania wartości formantów w Interfejsie użytkownika i do wykonywania zadań, takich jak sprawdzanie, czy adres URL witryny wejściowy jest nieprawidłowy. Po zakończeniu pracy kreatora użytkownik korzysta z Kreatora wdrażania `SiteColumnWizardModel` obiektem, aby określić stan końcowy interfejsu użytkownika.|  
|Menedżer podpisywania projektu|Jest to klasa pomocy o nazwie `ProjectSigningManager`, która umożliwia przez implementację kreator Utwórz nowy plik key.snk w każdym wystąpieniu nowego projektu.|  
|SharePoint — Polecenia|Są to metody, które są używane przez kreatora modelu danych do wywołania w lokalnej witrynie programu SharePoint podczas działania kreatora. Ponieważ polecenia SharePoint muszą wskazywać programu .NET Framework 3.5, te polecenia są implementowane w innym zestawie niż reszta kodem kreatora.|  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
 W tym przewodniku, należy dodać kilka projektów w rozwiązaniu SiteColumnProjectItem, który został utworzony w [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
-   Projekt WPF. Zostaną zaimplementowane <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu i zdefiniuj Kreatora interfejsu użytkownika w tym projekcie.  
  
-   Projektu biblioteki klas, które definiują polecenia SharePoint. Ten projekt muszą wskazywać środowiska.NET Framework 3.5.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz rozwiązanie SiteColumnProjectItem.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów **SiteColumnProjectItem** węzła rozwiązania, wybierz **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
3.  W górnej części **Dodawanie nowego projektu** okna dialogowego upewnij się, że **.NET Framework 4.5** jest wybrane na liście wersji programu .NET Framework.  
  
4.  Rozwiń węzeł **Visual C#** węzła lub **Visual Basic** węzeł i wybierz polecenie **Windows** węzła.  
  
5.  Na liście szablony projektów, wybierz **Biblioteka kontrolek użytkownika WPF**, nazwij projekt **ProjectTemplateWizard**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **ProjectTemplateWizard** projektu do rozwiązania i otwarcie pliku UserControl1.xaml domyślne.  
  
6.  Usuń plik UserControl1.xaml z projektu.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Aby utworzyć projekt polecenia SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła SiteColumnProjectItem rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W górnej części **Dodawanie nowego projektu** oknie dialogowym wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.  
  
3.  Rozwiń węzeł **Visual C#** węzła lub **Visual Basic** węzła, a następnie wybierz pozycję **Windows** węzła.  
  
4.  Wybierz **biblioteki klas** projektu szablonu, nazwy projektu **SharePointCommands**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **SharePointCommands** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configuring-the-projects"></a>Konfigurowanie projektów  
 Przed utworzeniem kreatora, należy dodać niektóre pliki kodu i odwołania do zestawów w projektach.  
  
#### <a name="to-configure-the-wizard-project"></a>Aby skonfigurować projekt Kreatora  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ProjectTemplateWizard** węzła projektu, a następnie wybierz **właściwości**.  
  
2.  W **projektanta projektu**, wybierz **aplikacji** kartę projektach Visual C# lub **skompilować** kartę dla projektu Visual Basic.  
  
3.  Upewnij się, że platforma docelowa jest ustawiona na .NET Framework 4.5, nie programu .NET Framework 4.5 Client Profile.  
  
     Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Otwórz menu skrótów **ProjectTemplateWizard** projektu, wybierz **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
5.  Wybierz **okna (WPF)** pozycja, nazwa elementu **WizardWindow**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
6.  Dodaj dwa **kontrolki użytkownika (WPF)** elementów do projektu, nazwij je **strona 1** i **Strona2**.  
  
7.  Dodawanie plików kodu cztery do projektu i nadaj im następujące nazwy:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Otwórz menu skrótów **ProjectTemplateWizard** węzła projektu, a następnie wybierz **Dodaj odwołanie**.  
  
9. Rozwiń węzeł **zestawy** węzła, wybierz **rozszerzenia** węzeł, a następnie zaznacz pola wyboru obok następujących zestawów:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Wybierz **OK** przycisk, aby dodać zestawy do projektu.  
  
11. W **Eksploratora rozwiązań**w obszarze **odwołania** folder **ProjectTemplateWizard** projektu, wybierz **EnvDTE**.  
  
12. W **właściwości** okna, zmień wartość **Osadź typy międzyoperacyjne** właściwości **False**.  
  
13. Jeśli projektujesz projektu Visual Basic zaimportować ProjectTemplateWizard przestrzeni nazw do projektu przy użyciu **projektanta projektu**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie zaimportowane przestrzenie nazw &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Aby skonfigurować projekt SharePointCommands  
  
1.  W **Eksploratora rozwiązań**, wybierz **SharePointCommands** węzła projektu.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj istniejący element**.  
  
3.  W **Dodaj istniejący element** okno dialogowe, przejdź do folderu, który zawiera pliki kodu dla projektu ProjectTemplateWizard, a następnie wybierz **CommandIds** pliku kodu.  
  
4.  Wybierz strzałkę obok pozycji **Dodaj** przycisk, a następnie wybierz pozycję **Dodaj jako Link** opcji z menu.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje plik kodu do **SharePointCommands** projektu jako łącze. Plik kodowy znajduje się w **ProjectTemplateWizard** również skompilować projekt, ale kod w pliku **SharePointCommands** projektu.  
  
5.  W **SharePointCommands** projekt, Dodaj inny plik kodu, który ma nazwę polecenia.  
  
6.  Wybierz projekt SharePointCommands, a następnie na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
7.  Rozwiń węzeł **zestawy** węzła, wybierz **rozszerzenia** węzeł, a następnie zaznacz pola wyboru obok następujących zestawów:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Wybierz **OK** przycisk, aby dodać zestawy do projektu.  
  
## <a name="creating-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Tworzenie modelu Kreatora podpisywania Manager i identyfikatory poleceń programu SharePoint  
 Dodaj kod do projektu ProjectTemplateWizard do zaimplementowania w próbce następujące składniki:  
  
-   Identyfikatory poleceń programu SharePoint. Te ciągi zidentyfikować poleceń programu SharePoint, które korzysta z kreatora. W dalszej części tego przewodnika dodasz kod w projekcie SharePointCommands do wykonania polecenia.  
  
-   Kreator modelu danych.  
  
-   Menedżer podpisywania projektu.  
  
 Aby uzyskać więcej informacji dotyczących tych składników, zobacz [opis składników kreatora](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>Aby zdefiniować identyfikatory poleceń programu SharePoint  
  
1.  W projekcie ProjectTemplateWizard Otwórz plik kodu CommandIds, a następnie zastąp całą zawartość pliku następującym kodem.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Aby utworzyć model Kreatora  
  
1.  Otwórz plik kodu SiteColumnWizardModel i Zastąp całą zawartość pliku następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Aby utworzyć Menedżera podpisywania projektu  
  
1.  Otwórz plik kodu ProjectSigningManager, a następnie zastąp całą zawartość pliku następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="creating-the-wizard-ui"></a>Tworzenie kreatora interfejsu użytkownika  
 Dodaj kod XAML, aby zdefiniować interfejsu użytkownika kreatora i formanty dwóch użytkownika, które udostępniają interfejs użytkownika dla stron kreatora, a następnie dodaj kod, aby zdefiniować zachowanie formantów okna i użytkownika. Kreator tworzenia podobny wbudowanych kreatora dla projektów programu SharePoint w Visual Studio.  
  
> [!NOTE]  
>  W poniższych krokach projektu mają błędy kompilacji, po dodaniu XAML lub kodu do projektu. Te błędy zniknie po dodaniu kod w kolejnych krokach.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Aby utworzyć okno Kreatora interfejsu użytkownika  
  
1.  W projekcie ProjectTemplateWizard Otwórz menu skrótów dla pliku WizardWindow.xaml, a następnie wybierz **Otwórz** można otworzyć okna w projektancie.  
  
2.  W widoku Projektanta XAML Zastąp bieżący XAML następujące XAML. XAML definiuje interfejs użytkownika, który zawiera nagłówek, <xref:System.Windows.Controls.Grid> zawierającym strony kreatora i przyciski nawigacji w dolnej części okna.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  Okno jest tworzony w tym języku XAML jest pochodną <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy podstawowej. Po dodaniu niestandardowe okno dialogowe WPF do programu Visual Studio, firma Microsoft zaleca, pochodzi z okna dialogowego z tej klasy mają stylów spójne z inne okna dialogowe programu Visual Studio i aby uniknąć problemów modalne okno dialogowe, które mogłyby wystąpić w. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie modalnych okien dialogowych](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Jeśli projektujesz projektu Visual Basic, Usuń `ProjectTemplateWizard` przestrzeni nazw z `WizardWindow` nazwę klasy w `x:Class` atrybutu `Window` elementu. Stanem tego elementu jest w pierwszym wierszu pliku XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien wyglądać jak w następującym przykładzie.  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Otwórz plik CodeBehind dla pliku WizardWindow.xaml.  
  
5.  Zastąp zawartość tego pliku, z wyjątkiem `using` deklaracje w górnej części pliku następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Aby utworzyć pierwszej stronie Kreatora interfejsu użytkownika  
  
1.  W projekcie ProjectTemplateWizard Otwórz menu skrótów dla pliku Page1.xaml, a następnie wybierz **Otwórz** otworzyć kontrolki użytkownika w projektancie.  
  
2.  W widoku Projektanta XAML Zastąp bieżący XAML następujące XAML. XAML definiuje interfejs użytkownika, który zawiera pole tekstowe, w którym użytkownicy mogą wprowadzić adres URL witryny lokalne, które mają być używane do debugowania. Interfejs użytkownika zawiera również przycisków opcji, z którym użytkownicy mogą określić, czy projekt jest w trybie piaskownicy.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Jeśli tworzysz projekt Visual Basic, Usuń `ProjectTemplateWizard` przestrzeni nazw z `Page1` nazwę klasy w `x:Class` atrybutu `UserControl` elementu. To jest pierwszy wiersz pliku XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien wyglądać następująco.  
  
    ```xml  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Zastąp zawartość pliku Page1.xaml, z wyjątkiem `using` deklaracje w górnej części pliku następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Aby utworzyć na drugiej stronie Kreatora interfejsu użytkownika  
  
1.  W projekcie ProjectTemplateWizard Otwórz menu skrótów dla pliku Page2.xaml, a następnie wybierz **Otwórz**.  
  
     Kontrola użytkownika zostanie otwarty w projektancie.  
  
2.  W widoku XAML zastąpić bieżący XAML następujące XAML. XAML definiuje interfejs użytkownika, który zawiera listy rozwijanej wyboru podstawowy typ kolumny witryny, pole kombi służący do określania wbudowanych lub niestandardowych grupę, do którego mają być wyświetlone kolumny witryny w galerii i pole tekstowe do określania nazwy kolumny witryny.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Jeśli tworzysz projekt Visual Basic, Usuń `ProjectTemplateWizard` przestrzeni nazw z `Page2` nazwę klasy w `x:Class` atrybutu `UserControl` elementu. To jest pierwszy wiersz pliku XAML. Gdy wszystko będzie gotowe, pierwszy wiersz powinien wyglądać następująco.  
  
    ```xml  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Zastąp zawartość pliku CodeBehind dla pliku Page2.xaml, z wyjątkiem `using` deklaracje w górnej części pliku następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implementing-the-wizard"></a>Implementowanie Kreatora  
 Zdefiniuj główną funkcjonalność kreatora zaimplementowanie <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu. Ten interfejs definiuje metody, które wywołuje program Visual Studio, gdy Kreator uruchamia zakończeniu i w określonym czasie podczas Kreator uruchamia.  
  
#### <a name="to-implement-the-wizard"></a>Aby zaimplementować Kreatora  
  
1.  W projekcie ProjectTemplateWizard Otwórz plik kodu SiteColumnProjectWizard.  
  
2.  Zastąp całą zawartość pliku następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="creating-the-sharepoint-commands"></a>Tworzenie polecenia SharePoint  
 Utwórz dwa polecenia niestandardowych, które wywołują modelu obiektów programu SharePoint server. Jedno polecenie Określa, czy adres URL witryny, że użytkownik wpisze w kreatorze jest prawidłowa. Inne polecenie pobiera wszystkie typy pól z określonej witryny programu SharePoint, dzięki czemu użytkownicy mogą wybrać, które z nich do użycia jako podstawy dla ich nowej kolumny witryny.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować polecenia SharePoint  
  
1.  W **SharePointCommands** projektu, otwórz plik kodu poleceń.  
  
2.  Zastąp całą zawartość pliku następującym kodem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie w prezentacji, całego kodu dla kreatora znajduje się teraz w projekcie. Skompiluj projekt, aby upewnić się, że skompilowany bez błędów.  
  
#### <a name="to-build-your-project"></a>Aby utworzyć projekt  
  
1.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Usuwanie pliku key.snk z szablonu projektu  
 W [wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), utworzony szablon projektu zawiera plik key.snk, który jest używany do podpisywania każde wystąpienie projektu kolumn witryny. Ten plik key.snk nie jest już konieczne ponieważ Kreator generuje nowy plik key.snk dla każdego projektu. Usuń plik key.snk z szablonu projektu i usunąć odwołania do tego pliku.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Aby usunąć plik key.snk z szablonu projektu  
  
1.  W **Eksploratora rozwiązań**w obszarze **SiteColumnProjectTemplate** węzła, otwórz menu skrótów **key.snk** pliku, a następnie wybierz pozycję **usunąć**.  
  
2.  W oknie dialogowym potwierdzenia wybierz **OK** przycisku.  
  
3.  W obszarze **SiteColumnProjectTemplate** węzła, otwórz plik SiteColumnProjectTemplate.vstemplate, a następnie usuń następujący element z niego.  
  
    ```xml  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Zapisz i zamknij plik.  
  
5.  W obszarze **SiteColumnProjectTemplate** węzła, otwórz plik ProjectTemplate.csproj lub ProjectTemplate.vbproj, a następnie usuń następujące `PropertyGroup` element z niego.  
  
    ```xml  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ``` 
  
6.  Usuń następujące `None` elementu.  
  
    ```xml  
    <None Include="key.snk" />  
    ```  
  
7.  Zapisz i zamknij plik.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Kojarzenie kreatora z szablonu projektu  
 Teraz, gdy zostały zaimplementowane kreatora, należy skojarzyć kreatora **kolumny witryny** szablonu projektu. Istnieją trzy procedur, które należy wykonać, aby to zrobić:  
  
1.  Zaloguj się przy użyciu silnej nazwy zestawu kreatora.  
  
2.  Pobierz token klucza publicznego zestawu kreatora.  
  
3.  Dodaj odwołanie do zestawu kreatora w pliku .vstemplate **kolumny witryny** szablonu projektu.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Aby zarejestrować Kreatora zestawu o silnej nazwie  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ProjectTemplateWizard** projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  Na **podpisywanie** wybierz opcję **Podpisz zestaw** pole wyboru.  
  
3.  W **wybierz plik klucza o silnej nazwie** wybierz  **\<nowy... >**.  
  
4.  W **tworzenie silnej nazwy klucza** okna dialogowego wprowadź nazwę dla nowego pliku klucza, usuń zaznaczenie **ochrony pliku klucza przy użyciu hasła** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
5.  Otwórz menu skrótów **ProjectTemplateWizard** projektu, a następnie wybierz pozycję **kompilacji** można utworzyć pliku ProjectTemplateWizard.dll.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Aby uzyskać klucz publiczny tokenu dla zestawu Kreatora  
  
1.  Na **Start Menu**, wybierz **wszystkie programy**, wybierz **programu Microsoft Visual Studio**, wybierz **programu Visual Studio Tools**, a następnie wybierz pozycję  **Wiersz polecenia dla deweloperów**.  
  
     Zostanie otwarte okno Wiersz polecenia programu Visual Studio.  
  
2.  Uruchom następujące polecenie, zastępując *PathToWizardAssembly* z pełną ścieżką do skompilowany zestaw ProjectTemplateWizard.dll ProjectTemplateWizard projektu na komputerze deweloperskim:  
  
    ```cmd  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Token klucza publicznego zestawu ProjectTemplateWizard.dll są zapisywane w oknie Wiersz polecenia programu Visual Studio.  
  
3.  Nie zamykaj okna Wiersz polecenia programu Visual Studio. Token klucza publicznego, należy podczas następnej procedury.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Aby dodać odwołanie do zestawu kreatora w pliku .vstemplate  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **SiteColumnProjectTemplate** węzeł projektu i Otwórz plik SiteColumnProjectTemplate.vstemplate.  
  
2.  Pod koniec pliku, Dodaj następujący `WizardExtension` element między `</TemplateContent>` i `</VSTemplate>` tagów. Zastąp *Twojego tokenu* wartość `PublicKeyToken` atrybutu z tokenem klucza publicznego, które zostały uzyskane w poprzedniej procedurze.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Aby uzyskać więcej informacji na temat `WizardExtension` elementu, zobacz [wizardextension — Element &#40;szablony Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Zapisz i zamknij plik.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Dodawanie do pliku Elements.xml w szablonie projektu parametry wymienne  
 Dodaj kilka parametrów wymiennych do pliku Elements.xml w projekcie SiteColumnProjectTemplate. Te parametry są inicjowane w `RunStarted` metoda `SiteColumnProjectWizard` klasy, która wcześniej zdefiniowany. Gdy użytkownik tworzy projekt kolumny witryny, Visual Studio automatycznie zastępuje tych parametrów w pliku Elements.xml w nowym projekcie wartości, które są określone w kreatorze.  
  
 Parametr wymienny to token, który rozpoczyna się i kończy się znakiem dolara ($). Oprócz Definiowanie wymienne parametry, można użyć wbudowanych parametrów, które są zdefiniowane i zainicjowane przez system projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [parametry wymienne](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Aby dodać do pliku Elements.xml parametry wymienne  
  
1.  W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku Elements.xml następujący kod XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Nowy kod XML zmienia wartości `Name`, `DisplayName`, `Type`, i `Group` atrybuty niestandardowe parametry wymienne.  
  
2.  Zapisz i zamknij plik.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Dodawanie kreatora do pakietu VSIX  
 Aby wdrożyć kreatora z pakietem VSIX, który zawiera szablon projektu kolumn witryny, dodaj odwołania do projektu kreatora i projektu poleceń programu SharePoint do pliku source.extension.vsixmanifest w projekcie VSIX.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Aby dodać kreatora do pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**w **SiteColumnProjectItem** projektu, otwórz menu skrótów **source.extension.vsixmanifest** pliku, a następnie wybierz pozycję **Otwórz**.  
  
     Visual Studio otwiera plik w edytorze manifestu.  
  
2.  Na **zasoby** karta edytora, wybierz **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.  
  
3.  W **typu** wybierz **Microsoft.VisualStudio.Assembly**.  
  
4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
5.  W **projektu** wybierz **ProjectTemplateWizard**, a następnie wybierz pozycję **OK** przycisku.  
  
6.  Na **zasoby** karta edytora, wybierz **nowy** przycisk ponownie.  
  
     **Dodaj nowy element zawartości** zostanie otwarte okno dialogowe.  
  
7.  W **typu** listy, wprowadź **SharePoint.Commands.v4**.  
  
8.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
9. W **projektu** wybierz **SharePointCommands** projektu, a następnie wybierz pozycję **OK** przycisku.  
  
10. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompilacje bez błędów.  
  
## <a name="testing-the-wizard"></a>Testowanie Kreatora  
 Teraz można przystąpić do testowania kreatora. Najpierw należy uruchomić debugowanie rozwiązania SiteColumnProjectItem w eksperymentalne wystąpienie programu Visual Studio. Następnie należy przetestować Kreator projektu kolumn witryny w eksperymentalne wystąpienie programu Visual Studio. Na koniec Skompiluj i uruchom projekt, aby sprawdzić, czy kolumna lokacji działa zgodnie z oczekiwaniami.  
  
#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania  
  
1.  Uruchom ponownie program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie SiteColumnProjectItem.  
  
2.  W projekcie ProjectTemplateWizard, otwórz plik kodu SiteColumnProjectWizard, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `RunStarted` metody.  
  
3.  Na pasku menu wybierz **debugowania**, **wyjątki**.  
  
4.  W **wyjątki** okna dialogowego upewnij się, że **wyrzuconych** i **nieobsługiwanych przez użytkownika** pól wyboru dla **wspólnego języka środowiska uruchomieniowego wyjątki**zostaną wyczyszczone, a następnie wybierz **OK** przycisku.  
  
5.  Rozpocznij debugowanie, wybierając **F5** klucza lub, w menu pasek wybierania **debugowania**, **Rozpocznij debugowanie**.  
  
     Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Element projektu przetestujesz, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Aby przetestować kreatora w programie Visual Studio  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Rozwiń węzeł **Visual C#** węzła lub **Visual Basic** rozwiń węzeł (w zależności od języka obsługującego szablon projektu), **SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.  
  
3.  Na liście szablony projektów, wybierz **kolumny witryny**, nazwij projekt **SiteColumnWizardTest**, a następnie wybierz pozycję **OK** przycisku.  
  
4.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `RunStarted` metody.  
  
5.  Kontynuuj debugowanie projektu przez wybranie **F5** klucza lub, w menu pasek wybierania **debugowania**, **Kontynuuj**.  
  
6.  W **Kreator dostosowania programu SharePoint**, wprowadź adres URL witryny, która ma być używany na potrzeby debugowania, a następnie wybierz pozycję **dalej** przycisku.  
  
7.  W drugiej stronie **Kreator dostosowania programu SharePoint**, wybierz następujące opcje:  
  
    -   W **typu** wybierz **logiczna**.  
  
    -   W **grupy** wybierz **kolumn Yes/No niestandardowy**.  
  
    -   W **nazwa** wprowadź **Moje kolumny Yes/No**, a następnie wybierz pozycję **Zakończ** przycisku.  
  
     W **Eksploratora rozwiązań**, pojawi się nowy projekt i zawiera element projektu o nazwie **pole1**, i Visual Studio otworzy plik Elements.xml projektu w edytorze.  
  
8.  Sprawdź, czy Elements.xml zawiera wartości, które zostały określone w kreatorze.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Aby przetestować kolumny witryny w programie SharePoint  
  
1.  W eksperymentalnym wystąpieniu programu Visual Studio wybierz klawisz F5.  
  
     Kolumny witryny zostaje spakowany i wdrożyć do programu SharePoint witryny **adres URL witryny** określa właściwości projektu. Przeglądarki sieci web zostanie otwarty na domyślną stronę tej lokacji.  
  
    > [!NOTE]  
    >  Jeśli **wyłączenia debugowania skryptu** zostanie wyświetlone okno dialogowe, wybierz **tak** przycisk, aby kontynuować debugowanie projektu.  
  
2.  Na **Akcje witryny** menu, wybierz **ustawienia lokacji**.  
  
3.  Na stronie Ustawienia lokacji w obszarze **galerie**, wybierz **kolumny witryny** łącza.  
  
4.  Na liście kolumn witryn, upewnij się, że **kolumn Yes/No niestandardowy** grupa zawiera kolumny o nazwie **Moje kolumny Yes/No**, a następnie zamknij przeglądarkę sieci web.  
  
## <a name="cleaning-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim  
 Po zakończeniu testowania elementu projektu, należy usunąć szablon projektu z eksperymentalne wystąpienie programu Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić na komputerze deweloperskim  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **kolumny witryny**, a następnie wybierz pozycję **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisk, aby potwierdzić, że chcesz odinstalować rozszerzenia, a następnie wybierz pozycję **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.  
  
4.  Zamknij zarówno eksperymentalne wystąpienie programu Visual Studio i wystąpienia, w którym rozwiązania CustomActionProjectItem jest otwarty.  
  
     Aby uzyskać informacje o sposobie wdrażania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia, zobacz [wysyłania rozszerzenia dla programu Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie elementu projektu kolumn witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Definiowanie typów elementów projektu SharePoint niestandardowych](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Instrukcje: korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  