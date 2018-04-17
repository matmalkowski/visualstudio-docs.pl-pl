---
title: 'Porady: modyfikowanie polecenia standardowe Menu języka specyficznego dla domeny | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 19d555f770802044b88e6a446932596176baa9fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Porady: modyfikowanie standardowego polecenia menu w języku specyficznym dla domeny
Można zmodyfikować zachowanie niektórych standardowych poleceń, które są automatycznie zdefiniowane w Twojej DSL. Na przykład można zmodyfikować **Wytnij** tak, aby nie obejmuje informacji poufnych. Aby to zrobić, można zastąpić metody w klasie zestawu poleceń. Te klasy są zdefiniowane w pliku CommandSet.cs w projekcie DslPackage i pochodne <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
 Podsumowanie, aby zmodyfikować polecenie:  
  
1.  [Odnajdywanie, jakie polecenia, można zmodyfikować](#what).  
  
2.  [Utwórz częściowa deklaracja klasy zestawu odpowiednie polecenie](#extend).  
  
3.  [Przesłaniaj metody ProcessOnStatus i ProcessOnMenu](#override) dla polecenia.  
  
 W tym temacie opisano tę procedurę.  
  
> [!NOTE]
>  Jeśli chcesz utworzyć własne polecenia menu, zobacz [porady: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
##  <a name="what"></a> Jakie polecenia można zmodyfikować?  
  
#### <a name="to-discover-what-commands-you-can-modify"></a>Aby dowiedzieć się, co należy polecenia można modyfikować  
  
1.  W `DslPackage` otwarciu projektu `GeneratedCode\CommandSet.cs`. W Eksploratorze rozwiązań można znaleźć tego pliku C# za oddział `CommandSet.tt`.  
  
2.  Znajdź klas w tym pliku, których nazwy kończą się z "`CommandSet`", na przykład `Language1CommandSet` i `Language1ClipboardCommandSet`.  
  
3.  W każdej klasie zestaw poleceń, wpisz "`override`" spację. IntelliSense wyświetli listę metod, które można zastąpić. Każde polecenie ma pary metod, których nazwy zaczynają się "`ProcessOnStatus`"i"`ProcessOnMenu`".  
  
4.  Zwróć uwagę, które polecenia Ustaw klasy zawiera polecenie, które chcesz zmodyfikować.  
  
5.  Zamknij plik bez zapisywania dokonanych zmian.  
  
    > [!NOTE]
    >  Zwykle nie należy edytować pliki, które zostały wygenerowane. Wszelkie zmiany zostaną utracone pliki są generowane przy następnym uruchomieniu.  
  
##  <a name="extend"></a> Rozszerzenie klasy zestawu odpowiednie polecenie  
 Utwórz nowy plik zawierający z częściowa deklaracja klasy zestawu poleceń.  
  
#### <a name="to-extend-the-command-set-class"></a>Aby rozszerzyć polecenia Set — klasa  
  
1.  W Eksploratorze rozwiązań w projekcie DslPackage Otwórz GeneratedCode folder, a następnie sprawdź w obszarze CommandSet.tt i otwórz jej wygenerowanego pliku CommandSet.cs. Należy pamiętać, przestrzeń nazw i nazwę pierwszej klasy, która jest zdefiniowane. Może na przykład, zobacz:  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  W **DslPackage**, Utwórz folder o nazwie **kod niestandardowy**. W tym folderze, Utwórz nowy plik klasy o nazwie `CommandSet.cs`.  
  
3.  W nowym pliku wpisz częściowych deklaracji, która ma taką samą nazwę jak wygenerowanej częściowej klasy i przestrzeni nazw. Na przykład:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Design;  
    namespace Company.Language1 /* Make sure this is correct */  
    { internal partial class Language1CommandSet { ...  
    ```  
  
     **Uwaga** Jeżeli plik szablonu klasy jest używany podczas tworzenia nowego pliku, należy usunąć zarówno w przestrzeni nazw, jak i nazwę klasy.  
  
##  <a name="override"></a> Przesłaniaj metody polecenia  
 Większość używanych poleceń ma dwie metody skojarzone: metodę o nazwie, takich jak `ProcessOnStatus`... określa, czy polecenie powinno być widoczne i włączone. Jest wywoływana, gdy użytkownik kliknie prawym przyciskiem myszy diagram i powinna wykonać szybko i nie wprowadzać zmian. `ProcessOnMenu`... jest wywoływane, gdy użytkownik klika polecenie i należy wykonać funkcja polecenia. Można zastąpić jedną lub obie te metody.  
  
### <a name="to-change-when-the-command-appears-on-a-menu"></a>Aby zmienić polecenie pojawi się w menu  
 Zastąpienie ProcessOnStatus... metody. Tej metody należy ustawić widoczne i włączone właściwości jej parametr MenuCommand. Zazwyczaj polecenia wygląda na to. CurrentSelection, aby określić, czy polecenie ma zastosowanie do wybranych elementów i może również sprawdzić ich właściwości, aby określić, czy polecenie może odnosić się w jego bieżącym stanie.  
  
 Ogólne wskazówki należy określić właściwość Visible przez elementy są wybrane. Właściwość "Enabled", która określa, czy polecenie jest wyświetlany czarny lub szary menu, powinien zależą od bieżącego stanu zaznaczenia.  
  
 Poniższy przykład powoduje wyłączenie elementu menu Usuń, gdy użytkownik zaznaczy więcej niż jeden kształt.  
  
> [!NOTE]
>  Ta metoda nie ma wpływu na czy polecenie ma być dostępny za pośrednictwem naciśnięcie klawisza. Na przykład wyłączenie elementu menu Usuń nie uniemożliwia polecenie wywoływany przez klawisz Delete.  
  
```  
/// <summary>  
/// Called when user right-clicks on the diagram or clicks the Edit menu.  
/// </summary>  
/// <param name="command">Set Visible and Enabled properties.</param>  
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)  
{  
  // Default settings from the base method.  
  base.ProcessOnStatusDeleteCommand(command);  
  if (this.CurrentSelection.Count > 1)  
  {  
    // If user has selected more than one item, Delete is greyed out.  
    command.Enabled = false;  
  }  
}  
```  
  
 Należy dobrze postępowania w przypadku wszystkich przypadków i ustawienia, które nie jest niezbędne, aby najpierw wywołać metodę podstawową.  
  
 Metoda ProcessOnStatus nie należy utworzyć, usunąć ani zaktualizować elementów w magazynie.  
  
### <a name="to-change-the-behavior-of-the-command"></a>Aby zmienić zachowanie polecenia  
 Zastąpienie ProcessOnMenu... metody. Poniższy przykład uniemożliwia użytkownikowi usunięcie więcej niż jeden element jednocześnie, nawet przy użyciu klawisz Delete.  
  
```  
/// <summary>  
/// Called when user presses Delete key   
/// or clicks the Delete command on a menu.  
/// </summary>  
protected override void ProcessOnMenuDeleteCommand()  
{  
  // Allow users to delete only one thing at a time.  
  if (this.CurrentSelection.Count <= 1)  
  {  
    base.ProcessOnMenuDeleteCommand();  
  }  
}  
```  
  
 Jeśli kod dokonuje zmian w magazynie, takie jak tworzenie, usuwanie lub aktualizowanie elementów lub łącza, należy to zrobić wewnątrz transakcji. Aby uzyskać więcej informacji, zobacz [sposobu tworzenia i aktualizacji elementów modelu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Pisanie kodu metody  
 Poniższe fragmenty są często przydatne w przypadku tych metod:  
  
-   `this.CurrentSelection`. Kształt, że użytkownik kliknął prawym przyciskiem myszy zawsze znajduje się lista łączników i kształtów. Gdy użytkownik kliknie pustą część diagramu, Diagram jest jedynym członkiem listy.  
  
-   `this.IsDiagramSelected()` - `true` Jeśli użytkownik kliknął pustą część diagramu.  
  
-   `this.IsCurrentDiagramEmpty()`  
  
-   `this.IsSingleSelection()` — użytkownik nie wybrał wielu kształtów  
  
-   `this.SingleSelection` -kształtu lub diagram, który użytkownik kliknął prawym przyciskiem myszy  
  
-   `shape.ModelElement as MyLanguageElement` -element modelu reprezentowanego przez kształtu.  
  
 Aby uzyskać więcej informacji o sposobie przejścia elementu element i o sposobach tworzenia obiektów i łączy, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.Design.MenuCommand>   
 [Pisanie kodu, aby dostosować języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Porady: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)   
 [Jak VSPackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Odwołanie do schematu VSCT XML](../extensibility/vsct-xml-schema-reference.md)   
 [VMSDK — przykład diagramy obwodu. Dostosowywanie szeroką gamę DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)   
 [Przykładowy kod: diagramy obwodu](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
