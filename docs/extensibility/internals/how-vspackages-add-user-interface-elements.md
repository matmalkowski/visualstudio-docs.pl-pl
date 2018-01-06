---
title: "Jak dodać elementy interfejsu użytkownika w VSPackages | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 142e2a24f866db7e3ae20217b60b1ea0c201c749
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-vspackages-add-user-interface-elements"></a>Jak VSPackages dodać elementy interfejsu użytkownika
Pakiet VSPackage można dodawać elementów interfejsu użytkownika, na przykład menu Paski narzędzi i narzędzia systemu windows dla programu Visual Studio za pomocą pliku vsct.  
  
 Elementy interfejsu użytkownika w można znaleźć zaleceń dotyczących projektowania [dotyczące środowiska użytkownika w usłudze Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>Architektura tabeli polecenia programu Visual Studio  
 Jak wspomniano, architektura tabeli polecenia obsługuje powyższych zasad architektury. Zasady za abstrakcje struktury danych i narzędzia architektury tabeli polecenia są następujące:  
  
-   Istnieją trzy typy podstawowe elementy: menu, poleceń i grup. Menu może być udostępniany w interfejsie użytkownika jako menu i podmenu, pasków narzędzi albo okna narzędzi. Polecenia są procedur, które użytkownik może zostać uruchomiony w środowisku IDE, a ich może być udostępniany jako elementy menu, przycisków, pól listy lub inne formanty. Grupy są kontenerami dla menu i poleceń.  
  
-   Każdy element jest określany przez definicję opisujące element, jego priorytetu względem innych elementów i flag, które modyfikują zachowanie.  
  
-   Każdy element ma umieszczania, opisujący elementu nadrzędnego. Element może mieć wielu elementów nadrzędnych, dzięki czemu może występować w wielu lokalizacjach w interfejsie użytkownika.  
  
     Każde polecenie musi mieć grupę jako własny element nadrzędny, nawet jeśli jest ona tylko podrzędny w tej grupie. Co standardowe menu również musi mieć grupę nadrzędną. Paski narzędzi i okien narzędzi pełnienie własnych elementów nadrzędnych. Grupa może mieć nadrzędnego głównym pasku menu programu Visual Studio lub dowolnego menu, paska narzędzi lub okna narzędzia.  
  
### <a name="how-items-are-defined"></a>Sposób definiowania elementów  
 . Vsct pliki są formatowane w kodzie XML. Pliku vsct definiuje elementy interfejsu użytkownika dla pakietu i określa, gdzie te elementy są wyświetlane w IDE. Identyfikator GUID i identyfikator w najpierw przypisano co menu, grupy lub polecenia w pakiecie `Symbols` sekcji. W dalszej części vsct pliku, każdego menu poleceń i grupy jest identyfikowany przez jego identyfikator GUID i identyfikator kombinacji. W poniższym przykładzie przedstawiono typowe `Symbols` sekcji wygenerowane przez szablon pakietu Visual Studio po **polecenie** jest zaznaczona w szablonie.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 Element najwyższego poziomu `Symbols` sekcja jest [GuidSymbol elementu](../../extensibility/guidsymbol-element.md). `GuidSymbol`elementy mapują identyfikatory GUID używane IDE, aby zidentyfikować pakiety i ich części nazwy.  
  
> [!NOTE]
>  Identyfikatory GUID są generowane automatycznie przez szablon pakietu Visual Studio. Unikatowy identyfikator GUID można również tworzyć przez kliknięcie **utworzyć identyfikatora GUID** na **narzędzia** menu.  
  
 Pierwszy `GuidSymbol` elementu "guid [PackageName] Pkg", to identyfikator GUID pakietu. Jest to identyfikator GUID, który jest używany przez program Visual Studio można załadować pakietu. Zazwyczaj nie ma elementów podrzędnych.  
  
 Konwencja, menu i poleceń są zgrupowane w drugiej `GuidSymbol` elementu "guid [PackageName] CmdSet", i map bitowych w innej `GuidSymbol` element, "guidImages". Nie trzeba wykonywać tę Konwencję, ale każdego menu, grupy polecenia i mapy bitowej musi być elementem podrzędnym `GuidSymbol` elementu.  
  
 W ciągu sekundy `GuidSymbol` element, który reprezentuje zestaw poleceń pakietu, jest kilka `IDSymbol` elementów. Każdy [elementu IDSymbol](../../extensibility/idsymbol-element.md) mapuje nazwę na wartość liczbową i może stanowić menu, grupy lub polecenia, który jest częścią zestawu poleceń. `IDSymbol` Elementów w trzecim polu `GuidSymbol` mapy bitowe reprezentuje element, które mogą służyć jako ikony poleceń. Ponieważ identyfikator GUID/pary muszą być unikatowe w aplikacji, a nie dwa elementy podrzędne tego samego `GuidSymbol` element może mieć taką samą wartość.  
  
### <a name="menus-groups-and-commands"></a>Menu, grup i poleceń  
 Gdy menu, grupy lub polecenia ma identyfikator GUID i identyfikator, można dodać go do środowiska IDE programu. Każdy element interfejsu użytkownika musi mieć następujące elementy:  
  
-   A `guid` atrybut, który odpowiada nazwie `GuidSymbol` element, który jest zdefiniowany element interfejsu użytkownika, w obszarze.  
  
-   `id` Atrybut, który odpowiada nazwie skojarzonego `IDSymbol` elementu.  
  
     Razem `guid` i `id` tworzą atrybuty *podpisu* elementu interfejsu użytkownika.  
  
-   A `priority` atrybut, który określa położenie elementu interfejsu użytkownika w jego nadrzędny menu lub grupy.  
  
-   A [elementu nadrzędnego](../../extensibility/parent-element.md) mający `guid` i `id` atrybuty określające podpisu menu nadrzędnej lub grupy.  
  
#### <a name="menus"></a>Menu  
 Każdego menu jest zdefiniowany jako [Menu Element](../../extensibility/menu-element.md) w `Menus` sekcji. Menu musi mieć `guid`, `id`, i `priority` atrybutów, a `Parent` elementu, a także następujących dodatkowych atrybutów i elementów podrzędnych:  
  
-   A `type` atrybut, który określa, czy menu mają być wyświetlane w IDE jako rodzaj menu lub pasek narzędzi.  
  
-   A [Element ciągów](../../extensibility/strings-element.md) zawierający [elementu ButtonText](../../extensibility/buttontext-element.md), w środowisku IDE, który określa tytuł menu i [CommandName elementu](../../extensibility/commandname-element.md), który określa nazwę, która jest używane w **polecenia** okno, aby uzyskać dostęp do menu.  
  
-   Flagi opcjonalne. A [Element Command flagi](../../extensibility/command-flag-element.md) może występować w definicji menu można zmienić jego wygląd i zachowanie w IDE.  
  
 Każdy `Menu` element musi mieć grupę jako klasy nadrzędnej, chyba że jest zadokowane elementu, np. paska narzędzi. Zadokowane menu jest własnego elementu nadrzędnego. Aby uzyskać więcej informacji na temat menu i wartości dla `type` atrybutów, zobacz [Menu Element](../../extensibility/menu-element.md) dokumentacji.  
  
 W poniższym przykładzie przedstawiono menu, która jest wyświetlana na pasku menu programu Visual Studio **narzędzia** menu.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Grupy  
 Grupa jest elementu, który jest zdefiniowany w `Groups` sekcji pliku vsct. Grupy są po prostu kontenerów. Nie podano ich w środowisku IDE, z wyjątkiem jako linię podziału w menu. W związku z tym [elementu grupy](../../extensibility/group-element.md) jest zdefiniowana tylko przez sygnaturę, priorytet i nadrzędnej.  
  
 Grupa może mieć menu, innej grupy lub się jako element nadrzędny. Element nadrzędny jest jednak zwykle menu lub pasek narzędzi. Menu w poprzedniego przykładu jest elementem podrzędnym `IDG_VS_MM_TOOLSADDINS` grup oraz że jest elementem podrzędnym na pasku menu programu Visual Studio. Grupa w poniższym przykładzie jest elementem podrzędnym elementu menu w poprzedniego przykładu.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Ponieważ to część menu tej grupy będą zwykle zawierają polecenia. Jednak może ona także zawierać innych menu. Jest to sposób definiowania podmenu, jak pokazano w poniższym przykładzie.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Polecenia  
 Polecenia, który został dostarczony do środowiska IDE jest zdefiniowany jako [Button Element](../../extensibility/button-element.md) lub [kombi Element](../../extensibility/combo-element.md). Widoczne w menu lub pasek narzędzi, polecenie musi mieć grupę jako klasy nadrzędnej.  
  
##### <a name="buttons"></a>Przyciski  
 Przyciski są zdefiniowane w `Buttons` sekcji. Dowolny element menu, przycisk lub innych elementów, które użytkownik klika do wykonywania pojedynczych poleceń jest traktowany jako przycisk. Niektóre typy przycisk mogą również obejmować funkcjonalność listy. Przyciski mają takie same wymagane i opcjonalne atrybuty, które mają menu, a także mogą mieć [Icon — Element](../../extensibility/icon-element.md) , który określa identyfikator GUID i identyfikator mapy bitowej, która reprezentuje przycisk w IDE. Aby uzyskać więcej informacji na temat przycisków i ich atrybutów, zobacz [Element przycisków](../../extensibility/buttons-element.md) dokumentacji.  
  
 Przycisk w poniższym przykładzie jest elementem podrzędnym grupy w wcześniejszego przykładu i zostanie wyświetlony w IDE jako element menu w menu nadrzędne tej grupy.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Kombinacje  
 Kombinacje są zdefiniowane w `Combos` sekcji. Każdy `Combo` element reprezentuje pole listy rozwijanej w IDE. Pole listy może lub nie może być zapis danych przez użytkowników, w zależności od wartości `type` atrybutu pole kombi. Kombinacje mają te same elementy i zachowanie przyciski mają, a także mogą mieć następujących dodatkowych atrybutów:  
  
-   A `defaultWidth` atrybut, który określa szerokość piksela.  
  
-   `idCommandList` Atrybut, który określa listę, która zawiera elementy, które są wyświetlane w polu listy. Na liście polecenia musi być zadeklarowany w tym samym `GuidSymbol` węzła, który zawiera pole kombi.  
  
 W poniższym przykładzie zdefiniowano element kombi.  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>Mapy bitowe  
 Polecenia, które będą wyświetlane razem z ikony musi zawierać `Icon` element, który odwołuje się do mapy bitowej przy użyciu jego identyfikator GUID i identyfikator. Każdy mapy bitowej jest zdefiniowany jako [mapy bitowej elementu](../../extensibility/bitmap-element.md) w `Bitmaps` sekcji. Wymagane tylko atrybuty `Bitmap` definicji są `guid` i `href`, który wskazuje plik źródłowy. Jeśli plik źródłowy jest pasek zasobów **usedList** atrybut jest również wymagane, aby wyświetlić listę dostępnych obrazów na pasku. Aby uzyskać więcej informacji, zobacz [mapy bitowej elementu](../../extensibility/bitmap-element.md) dokumentacji.  
  
### <a name="parenting"></a>Elementy nadrzędne  
 Następujące reguły określają, jak element może wywołać inny element jako klasy nadrzędnej.  
  
|Element|Zdefiniowany w tej sekcji tabela polecenia|Mogą znajdować się (jako elementu nadrzędnego, lub umieszczania w `CommandPlacements` sekcji lub obie)|Może zawierać (określanych jako element nadrzędny)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Grupa|[Grupuje elementu](../../extensibility/groups-element.md), IDE, inne pakiety VSPackage|Menu, grupą, elementu|Menu, grup i poleceń|  
|Menu|[Element menu](../../extensibility/menus-element.md), IDE, inne pakiety VSPackage|od 1 do  *n*  grup|0, aby  *n*  grup|  
|Pasek narzędzi|[Element menu](../../extensibility/menus-element.md), IDE, inne pakiety VSPackage|Elementu|0, aby  *n*  grup|  
|Element menu|[Przyciski elementu](../../extensibility/buttons-element.md), IDE, inne pakiety VSPackage|od 1 do  *n*  grup elementu|-0, aby  *n*  grup|  
|Przycisk|[Przyciski elementu](../../extensibility/buttons-element.md), IDE, inne pakiety VSPackage|od 1 do  *n*  grup elementu||  
|Kombi|[Element kombinacje](../../extensibility/combos-element.md), IDE, inne pakiety VSPackage|od 1 do  *n*  grup elementu||  
  
### <a name="menu-command-and-group-placement"></a>Menu, polecenie i umieszczania grupy  
 Menu, grupy lub polecenia może występować w więcej niż jedną lokację w IDE. Dla elementu pojawią się w różnych lokalizacjach, musi zostać dodany do `CommandPlacements` sekcji jako [CommandPlacement elementu](../../extensibility/commandplacement-element.md). Wszelkie menu, grupy lub polecenia mogą być dodawane jako położenie polecenia. Jednak paski narzędzi nie może znajdować się w ten sposób, ponieważ nie znajdują się w wielu lokalizacjach kontekstowa.  
  
 Rozmieszczanie polecenia mają `guid`, `id`, i `priority` atrybutów. Identyfikator GUID i identyfikator musi pasują do elementu, który jest ustawiony. `priority` Atrybut decyduje położenie elementu w odniesieniu do innych elementów. Gdy IDE scala dwa lub więcej elementów, które mają ten sam priorytet, ich rozmieszczanie jest nieokreślona, ponieważ IDE nie gwarantuje, że zasoby pakietu są w tej samej kolejności co czas odczytu pakietu korzysta z wbudowanej.  
  
 Jeśli menu lub grupy znajduje się w różnych lokalizacjach, wszystkie elementy podrzędne tego menu lub grupy będą wyświetlane w każdym wystąpieniu.  
  
## <a name="command-visibility-and-context"></a>Polecenie widoczność i kontekstu  
 Po zainstalowaniu wielu VSPackages nadmiaru menu, elementy menu i paski narzędzi mogą zajmowały IDE. Aby uniknąć tego problemu, można kontrolować widoczność poszczególne elementy interfejsu użytkownika przy użyciu *ograniczenia widoczność* i flagi polecenia.  
  
##### <a name="visibility-constraints"></a>Ograniczenia widoczności  
 Ograniczenie widoczności jest ustawiony jako [elementu VisibilityItem](../../extensibility/visibilityitem-element.md) w `VisibilityConstraints` sekcji. Ograniczenie widoczności definiuje konkretnych kontekstów interfejsu użytkownika, w których element docelowy jest widoczny. Menu lub polecenia, który znajduje się w tej sekcji jest widoczny tylko wtedy, gdy jeden z określonych kontekstów jest aktywny. Jeśli menu lub poleceń nie jest wywoływany w tej sekcji, zawsze jest domyślnie widoczne. Ta sekcja nie ma zastosowania do grup.  
  
 `VisibilityItem`elementy muszą mieć trzy atrybuty w następujący sposób: `guid` i `id` elementu interfejsu użytkownika docelowego i `context`. `context` Atrybut określa, kiedy element docelowy będzie widoczny i przyjmuje dowolnego prawidłowego kontekstu interfejsu użytkownika, jako jego wartość. Stałe kontekstu interfejsu użytkownika dla programu Visual Studio są elementami członkowskimi <xref:Microsoft.VisualStudio.VSConstants> klasy. Każdy `VisibilityItem` element może przyjmować wartości tylko jednego kontekstu. Aby zastosować drugi kontekstu, Utwórz drugi `VisibilityItem` element, który wskazuje na ten sam element, jak pokazano w poniższym przykładzie.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>Polecenie flagi  
 Następujące flagi polecenie może mieć wpływ na widoczność menu i poleceń, których dotyczą.  
  
 AlwaysCreate  
 Menu jest tworzony, nawet jeśli go nie ma grup ani przycisków.  
  
 Ważny do:`Menu`  
  
 CommandWellOnly  
 Zastosowanie tej flagi Jeśli polecenie nie jest wyświetlany w menu najwyższego poziomu i chcesz udostępnić powłoki dodatkowe dostosowanie, na przykład powiązanie go z kluczem. Po zainstalowaniu pakietu VSPackage, użytkownik może dostosować te polecenia, otwierając **opcje** okno dialogowe, a następnie edytując położenie polecenia w obszarze **środowiska klawiatury** kategorii. Nie wpływa na umieszczanie w menu skrótów, paski narzędzi, kontrolerów menu i podmenu.  
  
 Dotyczy: `Button`,`Combo`  
  
 DefaultDisabled  
 Domyślnie polecenie jest wyłączona, jeśli pakiet VSPackage, który implementuje polecenia nie został załadowany lub nie wywołano metody QueryStatus.  
  
 Dotyczy: `Button`,`Combo`  
  
 DefaultInvisible  
 Domyślnie polecenie jest niewidoczny, jeśli pakiet VSPackage, który implementuje polecenia nie został załadowany lub nie wywołano metody QueryStatus.  
  
 Powinny być połączone z `DynamicVisibility` flagi.  
  
 Dotyczy: `Button`, `Combo`,`Menu`  
  
 DynamicVisibility  
 Widoczność polecenia można zmienić przy użyciu metody QueryStatus lub identyfikator GUID, który znajduje się w kontekście `VisibilityConstraints` sekcji.  
  
 Ma zastosowanie do poleceń, które są wyświetlane w menu, a nie na paskach narzędzi. Elementów najwyższego poziomu paska narzędzi można wyłączyć, ale nie jest to ukryty, gdy flaga OLECMDF_INVISIBLE jest zwracany z metody QueryStatus.  
  
 W menu ta flaga również oznacza, że go powinny w automatycznie ukryte, gdy jego elementy członkowskie są ukryte. Ta flaga jest zwykle przypisany do podmenu, ponieważ menu najwyższego poziomu już to zachowanie.  
  
 Powinny być połączone z `DefaultInvisible` flagi.  
  
 Dotyczy: `Button`, `Combo`,`Menu`  
  
 NoShowOnMenuController  
 Polecenie, które ma tę flagę znajduje się na kontrolerze menu, polecenia nie są wyświetlane na liście rozwijanej.  
  
 Ważny do:`Button`  
  
 Aby uzyskać więcej informacji o flagach polecenia, zobacz [Element Command flagi](../../extensibility/command-flag-element.md) dokumentacji.  
  
##### <a name="general-requirements"></a>Wymagania ogólne  
 Polecenie musi upłynąć następujące serii testów mogą być wyświetlane i włączone:  
  
-   Polecenie jest ustawiony poprawnie.  
  
-   `DefaultInvisible` Nie ustawiono flagi.  
  
-   Nadrzędny menu lub pasek narzędzi jest widoczny.  
  
-   Polecenie nie jest niewidoczne ze względu na wpis kontekstu w [elementu VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sekcji.  
  
-   Kod pakiet VSPackage, który implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu wyświetla i umożliwia polecenia. Brak kodu interfejs został on przechwycony i podjęło.  
  
-   Po kliknięciu polecenia staje się zgodnie z procedurą opisaną w [routingu algorytmu](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Wywołanie polecenia wstępnie zdefiniowane  
 [Elementu UsedCommands](../../extensibility/usedcommands-element.md) umożliwia VSPackages do dostępu do poleceń, które są udostępniane przez inne pakiety VSPackage lub IDE. W tym celu należy utworzyć [elementu UsedCommand](../../extensibility/usedcommand-element.md) mający identyfikator GUID i identyfikator polecenia do użycia. Dzięki temu, że polecenie zostanie załadowany przez program Visual Studio, nawet jeśli nie jest częścią bieżącej konfiguracji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [UsedCommand elementu](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Wygląd elementu — interfejs  
 Zagadnienia dotyczące wybranie i rozmieszczenia elementów polecenia są następujące:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferuje wiele elementów interfejsu użytkownika, które wyglądać inaczej w zależności od umieszczania.  
  
-   Element interfejsu użytkownika, który jest zdefiniowany przy użyciu `DefaultInvisible` flagi nie będą wyświetlane w IDE, chyba że jest wyświetlany albo przez jej implementacja pakiet VSPackage <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody, lub skojarzone z określonym kontekstem interfejsu użytkownika w `VisibilityConstraints` sekcji.  
  
-   Pomyślnie pozycjonowane polecenie mogą nie być wyświetlane. To jest ponieważ IDE automatycznie ukrywa lub wyświetla niektórych poleceń, w zależności od interfejsów, które pakiet VSPackage ma (lub nie) implementowane. Na przykład pakiet VSPackage wdrożenie niektórych kompilacji interfejsy przyczyny elementów związanych z kompilacją menu ma być wyświetlany automatycznie.  
  
-   Stosowanie `CommandWellOnly` flagi w definicji elementu interfejsu użytkownika oznacza, że polecenie mogą być dodawane tylko przez dostosowania.  
  
-   Polecenia mogą być dostępne tylko w niektórych kontekstach interfejsu użytkownika, na przykład, tylko wtedy, gdy okno dialogowe jest wyświetlane, gdy jest IDE w widoku Projekt.  
  
-   Powoduje określone elementy interfejsu użytkownika, który będzie wyświetlany w IDE, musi implementować jeden lub więcej interfejsów lub pisania kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)