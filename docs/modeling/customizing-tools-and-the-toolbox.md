---
title: Dostosowywanie narzędzi i przybornika
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 357101a9430eb8d22aeab39179a0a4f70f0dc1bf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-tools-and-the-toolbox"></a>Dostosowywanie narzędzi i przybornika
Zdefiniuj elementy przybornika dla elementów, które chcesz zezwolić użytkownikom na wprowadzanie do ich modeli. Istnieją dwa rodzaje narzędzia: element narzędzia i połączenia. W Projektancie wygenerowanego użytkownika można wybrać elementu narzędzia przeciągnij kształtów na diagramie, a narzędzie połączenia, aby narysować łącza między kształtami można wybrać. Ogólnie rzecz biorąc narzędzia elementu zezwala użytkownikom na dodawanie wystąpienia klas domeny do ich modeli i narzędzia połączeń daj dodać wystąpienia relacji domeny.

 W tym temacie:

-   [Sposób definiowania przybornika](#ToolboxDef)

-   [Narzędzia dostosowywania elementów](#customizing)

-   [Tworzenie grup elementów za pomocą narzędzia](#groups)

-   [Dostosowywanie narzędzia połączeń](#connections)

##  <a name="ToolboxDef"></a> Sposób definiowania przybornika
 W Eksploratorze DSL rozwiń węzeł edytora i węzłów podrzędnych. Zwykle zobaczysz hierarchii podobny to:

```

Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool

```

 W tej części DSL Explorer można:

-   Utwórz nowe karty. Karty zdefiniować nagłówki sekcji w przyborniku.

-   Utwórz nowe narzędzia.

-   Skopiuj i Wklej narzędzia.

-   Przenieś narzędzia w górę lub w dół na liście.

-   Usunięcie kart i narzędzia.

> [!IMPORTANT]
>  Aby dodać lub wklejanie elementów w Eksploratorze DSL, kliknij prawym przyciskiem myszy ponadnadrzędny nowego węzła. Na przykład, aby dodać narzędzia, kliknij prawym przyciskiem myszy kartę, a nie **narzędzia** węzła. Aby dodać kartę, kliknij prawym przyciskiem myszy **edytor** węzła.

 **Ikonę przybornika** właściwości każdego narzędzia odwołuje się do pliku mapy bitowej 16 x 16. Pliki te są zwykle przechowywane w **Dsl\Resources** folderu.

 **Klasy** właściwość narzędzia elementu odwołuje się do klasy konkretnych domeny. Domyślnie narzędzie utworzy wystąpienia tej klasy. Jednak można napisać kod, aby narzędzie tworzenia grup elementów lub elementy o różnych typach.

 **Konstruktor połączeń** właściwości narzędzia połączenia odwołuje się do konstruktora połączenia, który definiuje, jakie typy elementów narzędzia można połączyć, i jakie relacje tworzy między nimi. Konstruktorzy połączeń są definiowane jako węzły w Eksploratorze DSL. Konstruktorzy połączenia są tworzone automatycznie podczas definiowania relacji domeny, ale można napisać kod, aby dostosować je.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Aby dodać narzędzie do przybornika

1.  Po utworzeniu klasy kształt i mechanizmowi klasą domeny zazwyczaj utworzyć narzędzie elementu.

     Po utworzeniu klasy łącznika i mechanizmowi relacji zazwyczaj utworzenie narzędzia Łącznik.

2.  W Eksploratorze DSL rozwiń **edytor** węzła i **kart z przybornika** węzła.

     Kliknij prawym przyciskiem myszy węzeł karcie przybornika, a następnie kliknij przycisk **Dodaj nowe narzędzie Element** lub **Dodaj nowe narzędzie połączenia**.

3.  Ustaw **ikonę przybornika** właściwości do odwoływania się do mapy bitowej 16 x 16.

     Jeśli chcesz zdefiniować ikonę Nowy, Utwórz plik mapy bitowej w Eksploratorze rozwiązań w **Dsl\Resources** folderu. Ten plik powinien mieć następujące wartości właściwości: **Akcja kompilacji** = **zawartości**; **Kopiuj do katalogu wyjściowego** = **nie należy kopiować**.

4.  **Dla narzędzia elementu:** ustawić **klasy** właściwości narzędzia do odwoływania się do klasy konkretnych domeny, która jest zamapowana do kształtu.

     **Narzędzia connector:** ustawić **Konstruktor połączeń** właściwości narzędzia do jednego z elementów, które są oferowane na liście rozwijanej. Konstruktorzy połączenia są tworzone automatycznie podczas mapowania łącznika do relacji domeny. Jeśli ostatnio po utworzeniu łącznika, zwykle wybierzesz konstruktora skojarzona z połączeniem.

5.  Aby przetestować DSL, naciśnij klawisz F5 lub CTRL + F5 w eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz plik przykładowy model. Nowe narzędzie powinny być wyświetlane w przyborniku. Przeciągnij go na diagramie, aby sprawdzić, czy tworzy nowy element.

     Jeśli nie ma narzędzia, Zatrzymaj eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W oknach **Start** menu, uruchom **zresetować Microsoft Visual Studio 2010 eksperymentalne wystąpienie programu**. Na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**. Następnie ponownie przetestuj DSL.

##  <a name="customizing"></a> Dostosowywanie narzędzia — Element
 Domyślnie narzędzie utworzy jedno wystąpienie określonej klasy, ale można używać różnych kodowań to na dwa sposoby:

-   Należy zdefiniować Element scalania dyrektywy w innych klas, włączenie je, aby zaakceptować nowe wystąpienia tej klasy, a umożliwiając im Utwórz dodatkowe linki, podczas tworzenia nowego elementu. Na przykład można zezwolić użytkownikowi na Dodaj komentarz na inny element, a przez to tworzyć łącza między dwoma.

     Te modyfikacje dotyczy również, co się dzieje, gdy użytkownik wkleja lub przeciąga i porzuca elementu.

     Aby uzyskać więcej informacji, zobacz [Dostosowywanie Element tworzenia i przepływu](../modeling/customizing-element-creation-and-movement.md).

-   Napisać kod, aby dostosować narzędzie, dzięki czemu można tworzyć grupy elementów. Narzędzie jest zainicjowana za pomocą metod ToolboxHelper.cs, którą można zastąpić. Aby uzyskać więcej informacji, zobacz [tworzenia grup z elementów za pomocą narzędzia](#groups).

##  <a name="groups"></a> Tworzenie grup elementów za pomocą narzędzia
 Narzędzie każdy element zawiera prototyp elementów, które powinien zostać utworzony. Domyślnie każdy element narzędzie tworzy pojedynczy element, ale istnieje również możliwość utworzenia grupy obiektów powiązanych z jednego narzędzia. Aby to zrobić, należy zainicjować narzędzie z <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> zawiera elementy powiązane.

 Poniższy przykład pochodzi z DSL, w którym jest typem tranzystor. Każdy tranzystor ma trzy terminale nazwanego. Za pomocą narzędzia elementu tranzystory przechowuje prototyp zawierający cztery elementy modelu i trzy łącza relacji. Gdy użytkownik przeciąga narzędzia na diagramie, prototyp jest utworzyć wystąpienia i połączony z katalogiem głównym modelu.

 Ten kod zastępuje metodę, która jest zdefiniowana w **Dsl\GeneratedCode\ToolboxHelper.cs**.

 Aby uzyskać więcej informacji dotyczących dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }

```

##  <a name="connections"></a> Dostosowywanie narzędzia połączeń
 Zwykle narzędzie elementu można utworzyć podczas tworzenia nowej klasy łącznika. Alternatywnie można przeciążać jedno narzędzie, zezwalając typy punktów końcowych w celu określenia typu relacji. Na przykład można zdefiniować jedno narzędzie połączenia, które można tworzyć relacji osoby osoby oraz relacje miasta osoby.

 Połączenia narzędzia wywołania konstruktorów połączenia. Użyj konstruktorów połączenia, aby określić, jak użytkownicy można połączyć elementy w Projektancie wygenerowany. Konstruktorzy połączenia Określ elementy, które mogą być połączone i typ łącza, który jest tworzony między nimi.

 Konstruktor połączeń jest tworzony automatycznie podczas tworzenia relacji między klasami domeny. Podczas mapowania narzędzia połączenia, można użyć tego konstruktora połączenia. Aby uzyskać więcej informacji o sposobie tworzenia narzędzia połączeń, zobacz [Konfigurowanie przybornika](../modeling/customizing-tools-and-the-toolbox.md).

 Domyślny konstruktor połączenia można zmodyfikować tak, aby można uwzględniać szereg różnych typów źródłowym i docelowym i tworzyć różne typy relacji.

 Można także zapisywać niestandardowy kod konstruktorów połączenia określić klas źródłowych i docelowych dla połączenia, typ połączenia, które ma zostać wykonane oraz wykonywać inne czynności związane z tworzeniem połączenia.

### <a name="the-structure-of-connection-builders"></a>Struktura połączenia konstruktorów
 Połączenia konstruktorów zawiera jeden lub więcej łącze Połącz dyrektywy, które określają relacji domeny i elementy źródłowe i docelowe. Na przykład szablon rozwiązania przepływ zadań zawiera **CommentReferencesSubjectsBuilder** w **DSL Explorer**. Ten konstruktor połączeń zawiera jedno łącze połączyć dyrektywy o nazwie **CommentReferencesSubjects**, która jest mapowana do relacji domeny **CommentReferencesSubjects**. Połącz ten link dyrektywa zawiera dyrektywy roli źródła, który wskazuje `Comment` klasy domeny i wskazujący dyrektywy roli docelowej `FlowElement` klasy domeny.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Przy użyciu połączenia konstruktorów ograniczyć źródła i docelowych ról
 Konstruktorzy połączenia służy do ograniczenia występowania niektórych klas w roli źródłowej lub rola Serwer obiektów docelowych relacji danej domeny. Na przykład może mieć klasy podstawowej domeny, która ma relację domeny do innej domeny, ale nie ma wszystkie klasy pochodnej klasy podstawowej, aby ról w relacji. W rozwiązaniu przepływ zadań są cztery klas konkretnych domeny (**StartPoint**, **punktu końcowego**, **MergeBranch**, i **synchronizacji**) dziedziczyć bezpośrednio klasa abstrakcyjna domeny **FlowElement**, i dwie klasy domeny (**zadań** i **ObjectInState**) który dziedziczy pośrednio go. Istnieje również **przepływ** odwołania relacji, która przyjmuje **FlowElement** klasy domeny w swojej roli źródłowej i rola Serwer obiektów docelowych. Jednak wystąpienia **punktu końcowego** klasy domeny nie powinien być źródła wystąpienia **przepływu** relacji, ani powinien wystąpienia **StartPoint** można klasy docelowego wystąpienia **przepływ** relacji. **FlowBuilder** konstruktora połączenie ma łącze połączyć dyrektywy o nazwie **przepływ** , który określa klas domeny, które można odtwarzać roli źródłowej (**zadań**,  **MergeBranch**, **StartPoint**, i **synchronizacji**) i które można odtwarzać rola Serwer obiektów docelowych (**MergeBranch**,  **Punkt końcowy**, i **synchronizacji**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Konstruktorzy połączenia z wielu łącze połączyć dyrektywy
 Możesz dodać więcej niż jednego połączenia połączyć dyrektywy do konstruktora połączenia. Może to ułatwić ukryć część złożoności modelu domeny od użytkowników i przechowywać **przybornika** zbyt uniknąć. Można dodać łącza połączyć dyrektywy kilka relacji z inną domenę do konstruktora jednego połączenia. Jednak należy łączyć relacje domeny, gdy wykonują tę samą funkcję.

 W rozwiązaniu przepływ zadań **przepływ** narzędzia połączenia jest używany do rysowania wystąpień obu **przepływ** i **przejścia przepływu obiektu** relacji domeny. **FlowBuilder** konstruktora połączenie ma dodatkowo do **przepływ** łącze połączenia dyrektywy opisana wcześniej, łączy dwa połączenia dyrektywy o nazwie **przejścia przepływu obiektu**. Te dyrektywy określić, że wystąpienie **przejścia przepływu obiektu** może być rysowany relacja między wystąpieniami **ObjectInState** klasy domeny lub z wystąpienia **ObjectInState**  na wystąpienie **zadań**, nie między dwa wystąpienia, ale **zadań**, lub z wystąpienia programu **zadań** na wystąpienie **ObjectInState**. Jednak wystąpienia **przepływ** może być rysowany relacji między dwa wystąpienia **zadań**. Jeśli skompilować i uruchomić przepływ zadań rozwiązanie, możesz zobaczyć tego rysunku **przepływ** z wystąpienia **ObjectInState** na wystąpienie **zadań** tworzy wystąpienie **Przejścia przepływu obiektu**, ale rysowania **przepływ** między dwa wystąpienia **zadań** tworzy wystąpienie **przepływ**.

### <a name="custom-code-for-connection-builders"></a>Niestandardowy kod dla konstruktorów połączenia
 Istnieją cztery pola wyboru w interfejsie użytkownika, które definiują różne rodzaje dostosowania konstruktorów połączenia:

-   **zaakceptować niestandardowe** pole wyboru w dyrektywie roli źródłowa lub docelowa

-   **niestandardowe połączenia** pole wyboru w dyrektywie roli źródłowa lub docelowa

-   **używa niestandardowych connect** pole wyboru w dyrektywie connect

-   **jest niestandardowa** właściwości konstruktora połączenia

 Należy podać niektóre kod program, aby te modyfikacje. Aby sprawdzić, jakie kodu, musisz podać, sprawdź jednego z tych pól, kliknij przycisk Przekształć wszystkie szablony, a następnie Skompiluj rozwiązanie. Spowoduje, że raport o błędach. Kliknij dwukrotnie raport o błędach można wyświetlić komentarz, który objaśnia, w jaki kod należy dodać.

> [!NOTE]
>  Aby dodać kod niestandardowy, Utwórz definicji częściowej klasy w pliku kodu niezależnie od plików kodu w folderach GeneratedCode. Aby uniknąć utraty pracy, nie należy edytować pliki wygenerowanego kodu. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Tworzenie połączenia niestandardowego kodu
 W każdym odnośniku połączyć dyrektywy, **źródła dyrektywy roli** kartę definiuje co typów przeciągnąć. Podobnie **celem roli dyrektywy** kartę definiuje co typów przeciągnąć. Dla każdego typu, możesz podać, czy zezwolić na połączenia (dla tego łącza połączenia dyrektywy) przez ustawienie **zaakceptować niestandardowe** Flaga, a następnie podając dodatkowego kodu.

 Można również dostosować co występuje, gdy połączenie zostanie nawiązane. Na przykład można dostosować tylko wielkość liter, w którym przeciągania występuje do lub z określonej klasy, połączyć jednego łącza wszystkich przypadków dyrektywa reguluje, lub całego FlowBuilder połączenia. Dla każdej z tych opcji można ustawić flagi niestandardowe na odpowiednim poziomie. Gdy Przekształć wszystkie szablony i spróbuj skompilować, komunikaty o błędach bezpośrednie do komentarzy, które znajdują się w wygenerowanym kodzie. Te komentarze zidentyfikować, należy podać.

 W przykładowym diagramie składniki konstruktora połączenia dla połączenia relacji domeny jest dostosowana i ograniczyć połączenia, które mogą być pomylone portów. Na poniższej ilustracji pokazano, że połączenia można tworzyć tylko z `OutPort` elementy `InPort` elementów, ale można zagnieżdżać składniki wewnątrz siebie nawzajem.

 **Połączeń przychodzących na OutPort zagnieżdżonych składników**

 ![Konstruktor połączeń](../modeling/media/connectionbuilder_3.png "ConnectionBuilder_3")

 W związku z tym można określić, że połączenia mogą pochodzić z zagnieżdżonych składników do OutPort. Aby określić takie połączenie, należy ustawić **używa niestandardowych zaakceptować** na **InPort** typu rolę źródła i **OutPort** typu jako rola Serwer obiektów docelowych w **szczegóły DSL**  okna, jak pokazano na poniższej ilustracji:

 **Łącze połączyć dyrektywy w Eksploratorze DSL**

 ![Obraz łączenia z konstruktora](../modeling/media/connectionbuilder_4a.png "ConnectionBuilder_4a")

 **Łącze połączenia w oknie Szczegóły DSL — dyrektywa**

 ![](../modeling/media/connectionbuilder_4b.png "ConnectionBuilder_4b")

 Następnie należy podać metod w klasie ConnectionBuilder:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Aby uzyskać więcej informacji dotyczących dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Podobny kod, można użyć na przykład aby uniemożliwić użytkownikom tworzenie pętli z łączami nadrzędny podrzędny. Ograniczenia te są uważane za ograniczenia "twardym", ponieważ użytkownicy nie narusza je w dowolnym momencie. Można również utworzyć sprawdzanie poprawności "soft", które użytkownicy mogą tymczasowo obejść przez utworzenie nieprawidłowy konfiguracje, których nie można zapisać.

### <a name="good-practice-in-defining-connection-builders"></a>Dobrym rozwiązaniem podczas definiowania konstruktorów połączenia
 Należy zdefiniować co konstruktor połączenia, aby utworzyć różne typy relacji tylko wtedy, gdy są one pokrewne. W przykładzie przepływ zadań umożliwia tego samego konstruktora tworzenie przepływów między zadaniami, a także między zadań i obiekty. Jednak może być mylące utworzyć relacje między komentarze i zadań za pomocą tego samego konstruktora.

 W przypadku definiowania konstruktora połączenia dla wielu typów relacje, należy upewnić się, że nie można dopasować więcej niż jeden typ z tej samej pary obiektu źródłowego i docelowego. W przeciwnym razie będą nieprzewidywalne wyniki.

 Zastosować ograniczenia "twardych" za pomocą kodu niestandardowego, ale należy rozważyć, czy użytkownicy powinni mieć tymczasowo nawiązywanie połączeń nieprawidłowy. Jeśli te powinny ograniczenia można zmodyfikować tak, aby połączenia nie są weryfikowane, dopóki użytkownicy próbują zapisać zmiany.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Przykładowe diagramy obwodu DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)