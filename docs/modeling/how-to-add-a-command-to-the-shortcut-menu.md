---
title: "Porady: Dodawanie polecenia do Menu skrótów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: "22"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 70ff75bd3bee039b0c97c35cc7135044e2cff1a6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Porady: dodawanie polecenia do menu skrótów
Polecenia menu można dodać do języka specyficznego dla domeny (DSL), dzięki czemu użytkownicy mogą wykonywać zadania, specyficzne dla użytkownika DSL. Polecenia są wyświetlane w menu kontekstowym (skrót), po kliknięciu prawym przyciskiem myszy na diagramie. Polecenie można zdefiniować i pojawia się tylko z menu w określonych okolicznościach. Na przykład możesz wprowadzić polecenie widoczny tylko wtedy, gdy użytkownik kliknie określonych rodzajów element lub elementy w określone stany.  
  
 Podsumowując kroki są wykonywane w projekcie DslPackage w następujący sposób:  
  
1.  [Deklarowanie polecenia w Commands.vsct](#VSCT)  
  
2.  [Zaktualizuj numer wersji pakietu do Package.tt](#version). Należy to zrobić przy każdej zmianie Commands.vsct  
  
3.  [Zapisywanie metod w klasie element CommandSet](#CommandSet) uwidocznić polecenia i aby zdefiniować, co ma się wykonaj polecenie.  
  
 Aby uzyskać przykłady, zobacz [wizualizacji i modelowania SDK witryny sieci Web](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
> [!NOTE]
>  Można również zmodyfikować zachowanie niektórych istniejących poleceń, takich jak wycinania, Wklej Zaznacz wszystko i drukowania przez zastąpienie metody CommandSet.cs. Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie standardowe polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="defining-a-command-using-mef"></a>Definiowanie polecenia przy użyciu MEF  
 Zarządzane rozszerzenia Framework (MEF) zapewnia alternatywny sposób definiowania polecenia menu w diagramie menu. Jego podstawowym celem jest umożliwienie DSL rozszerzyć przez Ciebie lub innych stron. Użytkownicy, można zainstalować tylko DSL lub można zainstalować DSL i rozszerzenia. Jednak MEF zmniejsza pracy Definiowanie polecenia menu skrótów, po początkowej pracy, aby włączyć MEF na DSL.  
  
 Użyj metody w tym temacie:  
  
1.  Chcesz zdefiniować polecenia menu dla menu niż menu skrótów kliknij prawym przyciskiem myszy.  
  
2.  Chcesz zdefiniować szczególne grupowania poleceń w menu.  
  
3.  Czy chcesz umożliwić innym rozszerzenie DSL z własnych poleceń.  
  
4.  Chcesz zdefiniować jedno polecenie.  
  
 W przeciwnym razie należy wziąć pod uwagę przy użyciu metody MEF do definiowania polecenia. Aby uzyskać więcej informacji, zobacz [rozszerzyć Twoje DSL przy użyciu MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
##  <a name="VSCT"></a>Deklarowanie polecenia w Commands.Vsct  
 Polecenia menu są zadeklarowane w DslPackage\Commands.vsct. Te definicje Określ etykiety elementów menu i gdzie są wyświetlane na pasku menu.  
  
 Plik, który można edytować Commands.vsct, importuje definicje z kilku pliki .h, które znajdują się w katalogu *ścieżka instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc. Obejmuje on też GeneratedVsct.vsct, które są generowane na podstawie definicję DSL.  
  
 Aby uzyskać więcej informacji o plikach vsct, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
#### <a name="to-add-the-command"></a>Aby dodać polecenie  
  
1.  W **Eksploratora rozwiązań**w obszarze **DslPackage** projektu, otwórz Commands.vsct.  
  
2.  W `Commands` elementu, zdefiniuj jednego lub więcej przycisków i grupy. A *przycisk* element menu. A *grupy* jest części menu. Aby zdefiniować te elementy, Dodaj następujące elementy:  
  
    ```  
    <!-- Define a group - a section in the menu -->  
    <Groups>  
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">  
        <!-- These symbols are defined in GeneratedVSCT.vsct -->  
        <Parent guid="guidCmdSet" id="menuidContext" />  
      </Group>  
    </Groups>  
    <!-- Define a button - a menu item - inside the Group -->  
    <Buttons>  
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        priority="0x0100" type="Button">  
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>  
        <!-- If you do not want to place the command in your own Group,   
             use Parent guid="guidCmdSet" id="grpidContextMain".  
             These symbols are defined in GeneratedVSCT.vsct -->  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <Strings>  
          <ButtonText>My Context Menu Command</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
    ```  
  
    > [!NOTE]
    >  Każdy przycisk lub grupa jest identyfikowany przez identyfikator GUID oraz liczby całkowitej. Można utworzyć kilka grup i przycisków z tym samym identyfikatorze GUID. Jednak muszą mieć różne identyfikatory. Do nazw identyfikator GUID i identyfikator są tłumaczone na rzeczywiste identyfikatory GUID oraz identyfikatory numeryczne w `<Symbols>` węzła.  
  
3.  Dodaj ograniczenie widoczności dla polecenia, dzięki czemu jest on załadowany tylko w kontekście języka specyficznego dla domeny. Aby uzyskać więcej informacji, zobacz [VisibilityConstraints elementu](../extensibility/visibilityconstraints-element.md).  
  
     Aby to zrobić, Dodaj następujące elementy w `CommandTable` elementu po `Commands` elementu.  
  
    ```  
    <VisibilityConstraints>  
      <!-- Ensures the command is only loaded for this DSL -->  
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        context="guidEditor"/>  
    </VisibilityConstraints>  
    ```  
  
4.  Zdefiniuj nazwy używane dla identyfikatorów GUID i identyfikatorów. Aby to zrobić, należy dodać `Symbols` element `CommandTable` elementu po `Commands` elementu.  
  
    ```  
    <Symbols>  
      <!-- Substitute a unique GUID for the placeholder: -->  
      <GuidSymbol name="guidCustomMenuCmdSet"  
        value="{00000000-0000-0000-0000-000000000000}" >  
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>  
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>  
      </GuidSymbol>  
    </Symbols>  
    ```  
  
5.  Zastąp `{000...000}` o identyfikatorze GUID, który identyfikuje grup i elementów menu. Aby uzyskać nowy identyfikator GUID, użyj **utworzyć identyfikatora GUID** narzędzia w **narzędzia** menu.  
  
    > [!NOTE]
    >  Jeśli dodasz więcej grup lub elementów menu, można użyć tego samego identyfikatora GUID. Jednak muszą używać nowej wartości `IDSymbols`.  
  
6.  W kodzie skopiowanych z tej procedury Zastąp każde wystąpienie następujących ciągów własne parametry:  
  
    -   `grpidMyMenuGroup`  
  
    -   `cmdidMyContextMenuCommand`  
  
    -   `guidCustomMenuCmdSet`  
  
    -   `My Context Menu Command`  
  
##  <a name="version"></a>Zaktualizuj wersję pakietu w Package.tt  
 Przy dodawaniu lub zmienić polecenie aktualizacji `version` parametr <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> który dotyczy klasy pakietu przed udostępnieniem nowej wersji języka specyficznego dla domeny.  
  
 Ponieważ klasa pakietu jest zdefiniowana w wygenerowanym pliku, należy zaktualizować atrybutu w pliku szablonu tekstowego, który generuje plik Package.cs.  
  
#### <a name="to-update-the-packagett-file"></a>Aby zaktualizować plik Package.tt  
  
1.  W **Eksploratora rozwiązań**w **DslPackage** projektu w **GeneratedCode** folderu, otwórz plik Package.tt.  
  
2.  Zlokalizuj `ProvideMenuResource` atrybutu.  
  
3.  Przyrost `version` parametr atrybutu, który jest drugim parametrem. Jeśli chcesz, możesz zapisywać nazwę parametru, aby jawnie przypomnienia o jej celem. Na przykład:  
  
     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`  
  
##  <a name="CommandSet"></a>Zdefiniuj zachowanie polecenia  
 Twoje DSL ma już niektóre polecenia, które zostały wdrożone w częściowej klasy, która jest zadeklarowana w DslPackage\GeneratedCode\CommandSet.cs. Aby dodać nowe polecenia, można rozszerzyć tę klasę przez tworzenie nowego pliku, który zawiera częściowa deklaracja tego samego rodzaju. Nazwa klasy jest zwykle  *\<YourDslName >*`CommandSet`. Warto rozpocząć od sprawdzenia nazwę klasy i zapoznanie się jego zawartość.  
  
 Jest pochodną klasy zestawu poleceń <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
#### <a name="to-extend-the-commandset-class"></a>Aby rozszerzyć klasy element CommandSet  
  
1.  W Eksploratorze rozwiązań w projekcie DslPackage Otwórz GeneratedCode folder, a następnie sprawdź w obszarze CommandSet.tt i otwórz jej wygenerowanego pliku CommandSet.cs. Należy pamiętać, przestrzeń nazw i nazwę pierwszej klasy, która jest zdefiniowane. Może na przykład, zobacz:  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  W **DslPackage**, Utwórz folder o nazwie **kod niestandardowy**. W tym folderze, Utwórz nowy plik klasy o nazwie `CommandSet.cs`.  
  
3.  W nowym pliku wpisz częściowych deklaracji, która ma taką samą nazwę jak wygenerowanej częściowej klasy i przestrzeni nazw. Na przykład:  
  
     `namespace Company.Language1 /* Make sure this is correct */`  
  
     `{ internal partial class Language1CommandSet { ...`  
  
     **Uwaga** Jeżeli szablonu klasy jest używany podczas tworzenia nowego pliku, należy usunąć zarówno w przestrzeni nazw, jak i nazwę klasy.  
  
### <a name="extend-the-command-set-class"></a>Rozszerzenie klasy zestawu poleceń  
 Kod zestawu poleceń będzie zwykle należy zaimportować następujących przestrzeni nazw:  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Design;   
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Shell;  
```  
  
 Ustawienia przestrzeni nazw i nazwę klasy do odpowiadają wygenerowanego CommandSet.cs:  
  
```  
namespace Company.Language1 /* Make sure this is correct */  
{  
  // Same class as the generated class.  
  internal partial class Language1CommandSet   
  {  
```  
  
 Konieczne jest zdefiniowanie dwóch metod, co ustalenie, kiedy polecenie będzie widoczny w menu kontekstowego, a drugą do wykonania polecenia. Te metody nie są zastąpienia; Zamiast tego należy zarejestrować je w postaci listy poleceń.  
  
### <a name="define-when-the-command-will-be-visible"></a>Definiowanie, kiedy polecenie będzie widoczne  
 Dla każdego polecenia, należy zdefiniować `OnStatus...` metodę, która określa, czy polecenie będzie wyświetlane w menu i czy będzie włączone, czy nieaktywna. Ustaw `Visible` i `Enabled` właściwości `MenuCommand`, jak pokazano w poniższym przykładzie. Ta metoda jest wywoływana w celu skonstruowania menu skrótów za każdym razem, gdy użytkownik kliknie prawym przyciskiem myszy diagram, dlatego musi działać szybko.  
  
 W tym przykładzie polecenie jest widoczny tylko wtedy, gdy użytkownik wybrał określonego typu kształtu i jest włączona tylko wtedy, gdy co najmniej jeden z wybranych elementów w określonym stanie. Przykład jest oparty na szablonie DSL Diagram klas i ClassShape i ModelClass są typy, które są zdefiniowane w DSL:  
  
```  
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  command.Visible = command.Enabled = false;  
  foreach (object selectedObject in this.CurrentSelection)  
  {  
    ClassShape shape = selectedObject as ClassShape;  
    if (shape != null)  
    {  
      // Visibility depends on what is selected.  
      command.Visible = true;  
      ModelClass element = shape.ModelElement as ModelClass;  
      // Enabled depends on state of selection.  
      if (element != null && element.Comments.Count == 0)  
      {  
        command.Enabled = true;  
        return; // seen enough  
} } } }  
```  
  
 Poniższe fragmenty są często przydatne w metodach OnStatus:  
  
-   `this.CurrentSelection`., Kształt będący użytkownik kliknął prawym przyciskiem myszy zawsze znajduje się na tej liście. Gdy użytkownik kliknie pustą część diagramu, Diagram jest jedynym członkiem listy.  
  
-   `this.IsDiagramSelected()` - `true`Jeśli użytkownik kliknął pustą część diagramu.  
  
-   `this.IsCurrentDiagramEmpty()`  
  
-   `this.IsSingleSelection()`— użytkownik nie wybrał wielu obiektów  
  
-   `this.SingleSelection`-kształtu lub diagram, który użytkownik kliknął prawym przyciskiem myszy  
  
-   `shape.ModelElement as MyLanguageElement`-element modelu reprezentowanego przez kształtu.  
  
 Generalnie, wprowadź `Visible` są zależne od wybranej właściwości i upewnij `Enabled` właściwości są zależne od stan wybranych elementów.  
  
 Metoda OnStatus nie należy zmieniać stanu magazynu.  
  
### <a name="define-what-the-command-does"></a>Zdefiniuj, jak działa polecenie  
 Dla każdego polecenia, należy zdefiniować `OnMenu...` metodę, która wykonuje akcję wymagane, gdy użytkownik kliknie przycisk polecenia menu.  
  
 Jeśli wprowadzisz zmiany do elementów modelu, należy to zrobić wewnątrz transakcji. Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie standardowe polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
 W tym przykładzie `ClassShape`, `ModelClass`, i `Comment` typów zdefiniowanych w DSL, pochodzącej z szablonu DSL diagramu klas.  
  
```  
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  Store store = this.CurrentDocData.Store;  
  // Changes to elements and shapes must be performed in a Transaction.  
  using (Transaction transaction =  
       store.TransactionManager.BeginTransaction("My command"))  
  {  
    foreach (object selectedObject in this.CurrentSelection)  
    {  
      // ClassShape is defined in my DSL.  
      ClassShape shape = selectedObject as ClassShape;  
      if (shape != null)  
      {  
        // ModelClass is defined in my DSL.  
        ModelClass element = shape.ModelElement as ModelClass;  
        if (element != null)  
        {  
          // Do required action here - for example:  
  
          // Create a new element. Comment is defined in my DSL.  
          Comment newComment = new Comment(element.Partition);  
          // Every element must be the target of an embedding link.  
          element.ModelRoot.Comments.Add(newComment);  
          // Set properties of new element.  
          newComment.Text = "This is a comment";  
          // Create a reference link to existing object.  
          element.Comments.Add(newComment);  
        }  
      }  
    }  
    transaction.Commit(); // Don't forget this!  
  }  
}  
```  
  
 Aby uzyskać więcej informacji o tym, jak można przejść z obiektu do obiektu w modelu oraz o sposobie tworzenia obiektów i łączy, zobacz [porady: modyfikowanie standardowe polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="register-the-command"></a>Zarejestruj polecenie  
 Powtórz w języku C# deklaracje wartości Identyfikator GUID i identyfikator wprowadzone w sekcji symbole CommandSet.vsct:  
  
```  
private Guid guidCustomMenuCmdSet =   
    new Guid("00000000-0000-0000-0000-000000000000");  
private const int grpidMyMenuGroup = 0x01001;  
private const int cmdidMyContextMenuCommand = 1;  
```  
  
 Użyj tej samej wartości identyfikatora GUID jako wstawione w **Commands.vsct**.  
  
> [!NOTE]
>  Jeśli zmienisz sekcji symbole pliku VSCT, należy również zmienić deklaracji do dopasowania. Należy również zwiększenie numeru wersji w Package.tt  
  
 Zarejestruj poleceń menu jako część tego zestawu poleceń. `GetMenuCommands()`jest wywoływana, gdy po zainicjowaniu diagramu:  
  
```  
protected override IList<MenuCommand> GetMenuCommands()  
{  
  // Get the list of generated commands.  
  IList<MenuCommand> commands = base.GetMenuCommands();  
  // Add a custom command:  
  DynamicStatusMenuCommand myContextMenuCommand =  
    new DynamicStatusMenuCommand(  
      new EventHandler(OnStatusMyContextMenuCommand),  
      new EventHandler(OnMenuMyContextMenuCommand),  
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));  
  commands.Add(myContextMenuCommand);  
  // Add more commands here.  
  return commands;  
}   
```  
  
## <a name="test-the-command"></a>Polecenie testu  
 Tworzenie i uruchamianie DSL w eksperymentalne wystąpienie programu Visual Studio. Polecenie powinny być wyświetlane w menu skrótów w sytuacjach, który został określony.  
  
#### <a name="to-exercise-the-command"></a>Wykonywanie polecenia  
  
1.  Na **Eksploratora rozwiązań** narzędzi, kliknij przycisk **Przekształć wszystkie szablony**.  
  
2.  Naciśnij klawisz **F5** ponownie skompiluj rozwiązanie, i Rozpocznij debugowanie języka specyficznego dla domeny w eksperymentalnym kompilacji.  
  
3.  Eksperymentalne kompilacji Otwórz przykładowy diagram.  
  
4.  Kliknij prawym przyciskiem myszy różne elementy na diagramie, aby sprawdzić, czy polecenie jest prawidłowo włączona lub wyłączona i odpowiednio pokazywany lub ukryty, w zależności od wybranego elementu.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 **Polecenie nie jest wyświetlane w menu:**  
  
-   Polecenie będą wyświetlane tylko w przypadku debugowania jego wystąpień programu Visual Studio, dopóki nie zostanie zainstalowany pakiet DSL. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
-   Upewnij się, że eksperymentalne przykładu ma prawidłowe rozszerzenie dla tego DSL. Aby sprawdzić rozszerzenie nazwy pliku, otwórz DslDefinition.dsl w głównym wystąpienie programu Visual Studio. Następnie w Eksploratorze DSL, kliknij prawym przyciskiem myszy węzeł edytor, a następnie kliknij polecenie Właściwości. W oknie właściwości sprawdź właściwość FileExtension.  
  
-   Czy [zwiększenie numeru wersji pakietu](#version)?  
  
-   Ustaw punkt przerwania na początku metodę OnStatus. Powinien on Przerwij po kliknięciu prawym przyciskiem myszy nad dowolną część diagramu.  
  
     **Nie wywołano metody OnStatus**:  
  
    -   Upewnij się, że identyfikatory GUID oraz identyfikatorów w kodzie element CommandSet zgodne z tymi w sekcji symbole Commands.vsct.  
  
    -   Commands.vsct upewnij się, że identyfikator GUID i identyfikator w każdym węźle nadrzędnym zidentyfikować poprawne nadrzędnej grupy.  
  
    -   W wierszu polecenia programu Visual Studio wpisz/devenv/rootsuffix exp Setup. Następnie uruchom ponownie debugowanie wystąpienie programu Visual Studio.  
  
-   Krok za pomocą metody OnStatus można zweryfikować tego polecenia. Visible i polecenia. Włączone jest ustawiony na wartość true.  
  
 **Zostanie wyświetlone menu nieprawidłowy tekst lub polecenia pojawi się w niewłaściwym miejscu**:  
  
-   Upewnij się, że kombinacja identyfikator GUID i identyfikator jest unikatowy dla tego polecenia.  
  
-   Upewnij się, że odinstalowano wcześniejszych wersji pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie kodu, aby dostosować języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Porady: modyfikowanie polecenia standardowe Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)   
 [Wdrażanie rozwiązań języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md)   
 [Przykładowy kod: diagramy obwodu](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
