---
title: MenuCommands Vs. OleMenuCommands | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 
manager: douge
ms.openlocfilehash: 0465057549543d8e07742e3b3806ebdcab28eb28
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands Vs. OleMenuCommands
Można utworzyć polecenia menu wynikających z <xref:System.ComponentModel.Design.MenuCommand> lub <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiekt i impementling obsługi zdarzeń odpowiednie. W większości przypadków można użyć <xref:System.ComponentModel.Design.MenuCommand>, ponieważ jest pakiet VSPackage szablon projektu, ale może od czasu do czasu może być konieczne użycie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 Można ich używać poleceń, że pakiet VSPackage udostępnianych do środowiska IDE programu musi być widoczne i włączone przed użytkownikiem. Polecenia są tworzone w pliku vsct za pomocą szablonu projektu pakietu Visual Studio, są widoczne i włączone domyślnie. Ustawienie flagi niektórych poleceń, takich jak `DynamicItemStart`, można zmienić domyślne zachowanie. Widoczność, stan włączony i inne właściwości polecenia można także zmienić kodu w czasie wykonywania uzyskując dostęp do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiekt, który jest skojarzony z poleceniem.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Lokalizacje szablonów dla szablonu pakietu programu Visual Studio  
 Można znaleźć szablonu pakietu Visual Studio w **nowy projekt** , okno dialogowe **Visual Basic / rozszerzalności**, **C# / rozszerzalności**, lub **innych Typy projektów / rozszerzalności**.  
  
## <a name="creating-a-command"></a>Tworzenie polecenia  
 Wszystkie polecenia, grup polecenia menu, paski narzędzi i okien narzędzi są zdefiniowane w pliku vsct. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Jeśli tworzysz pakiet VSPackage za pomocą szablonu pakietu, wybierz **polecenie** do tworzenia pliku vsct i definiowanie polecenia menu domyślne. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Aby dodać polecenia do środowiska IDE  
  
1.  Otwórz plik vsct.  
  
2.  W `Symbols` sekcji, Znajdź [GuidSymbol](../extensibility/guidsymbol-element.md) element, który zawiera grupy i polecenia.  
  
3.  Utwórz [IDSymbol](../extensibility/idsymbol-element.md) elementu dla każdego menu, grupy lub polecenia, które chcesz dodać, jak pokazano w poniższym przykładzie.  
  
     <!--FIXME [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  -->
    ```xaml  
    <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
      <IDSymbol name="MyMenuGroup" value="0x1020" />
      <IDSymbol name="cmdidMyCommand" value="0x0100" />
    </GuidSymbol>
    ```  
  
    `name` Atrybuty `GuidSymbol` i `IDSymbol` elementy Podaj pary GUID:ID dla każdego nowego menu, grupy lub polecenie. `guid` Reprezentuje zestaw poleceń, który jest zdefiniowany dla VSPackage. Można zdefiniować wiele zestawów polecenia. Każda para GUID:ID musi być unikatowa.  
  
4.  W [przyciski](../extensibility/buttons-element.md) sekcji, Utwórz [przycisk](../extensibility/button-element.md) element, aby określić polecenie, jak pokazano w poniższym przykładzie.  
  
     <!--FIXME [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  -->
    ```xaml  
    <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```  
  
    1.  Ustaw `guid` i `id` pól do dopasowania GUID:ID nowego polecenia.  
  
    2.  Ustaw `priority` atrybutu.  
  
         `priority` Atrybut jest używany przez vsct w celu określenia lokalizacji przycisku wśród innych obiektów w jego grupie nadrzędnej.  
  
         Polecenia, które mają niższe wartości priorytetu są wyświetlane powyżej lub po lewej, polecenia, które mają wyższe wartości priorytetu. Priorytet zduplikowane wartości są dozwolone, ale względne położenie polecenia, które mają taki sam priorytet jest określana przez kolejność, w którym VSPackages są przetwarzane w czasie wykonywania, a kolejności nie może być wcześniej.  
  
         Pominięcie `priority` atrybut ustawia jego wartość na 0.  
  
    3.  Ustaw `type` atrybutu. W większości przypadków będzie jego wartość `"Button"`. Opisy innych typów prawidłowy przycisk znajdują się [Button Element](../extensibility/button-element.md).  
  
5.  W definicji przycisku Utwórz [ciągów](../extensibility/strings-element.md) element, który zawiera [ButtonText](../extensibility/buttontext-element.md) element zawierać nazwy menu, pojawiającą się w środowisku IDE, a [CommandName](../extensibility/commandname-element.md) Element zawierać nazwy polecenia, które umożliwia dostęp do menu w **polecenia** okna.  
  
     Jeśli przycisk ciąg tekstowy zawiera znak "&", użytkownik może otworzyć menu, naciskając klawisz ALT plus to od razu następuje znak "&".  
  
     Dodawanie `Tooltip` zawartych w niej tekst wyświetlany, gdy użytkownik znajduje się wskaźnik na przycisku spowoduje, że element.  
  
6.  Dodaj [ikona](../extensibility/icon-element.md) elementu, aby wybrać ikonę, jeśli istnieją, aby można wyświetlić za pomocą polecenia. Ikony są wymagane w przypadku przycisków, na paskach narzędzi, ale nie dla elementów menu. `guid` i `id` z `Icon` elementu musi być zgodny z regułami [mapy bitowej](../extensibility/bitmap-element.md) elementu zdefiniowanego w `Bitmaps` sekcji.  
  
7.  Dodaj polecenie flagi, zgodnie z potrzebami zmienić wygląd i zachowanie przycisku. Aby to zrobić, należy dodać [CommandFlag](../extensibility/command-flag-element.md) elementu w definicji menu.  
  
8.  Ustaw grupę nadrzędną polecenia. Grupy nadrzędnej może być utworzona grupa, grupę z innym pakietem lub grupy z IDE. Na przykład, aby dodać polecenia do narzędzi edycji programu Visual Studio, obok pozycji **komentarz** i **Usuń komentarz** przyciski ustawioną guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT obiektu nadrzędnego. Jeśli element nadrzędny jest grupą zdefiniowane przez użytkownika, jego musi być elementem podrzędnym menu, paska narzędzi lub okna narzędzia, która pojawia się w środowisku IDE.  
  
     Można to zrobić na dwa sposoby, w zależności od projektu:  
  
    -   W `Button` elementu, Utwórz [nadrzędnej](../extensibility/parent-element.md) element i ustaw jej `guid` i `id` pól Identyfikator Guid i identyfikator grupy, który będzie obsługiwał polecenia, znanej także jako *grupy nadrzędnej lokalizacji głównej*.  
  
         W poniższym przykładzie zdefiniowano polecenia, która będzie wyświetlana w menu zdefiniowane przez użytkownika.  
  
         <!--FIXME [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  -->
        ```xaml  
        <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
          <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
          <Icon guid="guidImages" id="bmpPic1" />
          <Strings>
            <CommandName>cmdidTestCommand</CommandName>
            <ButtonText>Test Command</ButtonText>
          </Strings>
        </Button>
        ```  
  
    -   Może pominąć `Parent` elementu, jeśli polecenie ma zostać umieszczony za pomocą polecenia umieszczania. Utwórz [CommandPlacements](../extensibility/commandplacements-element.md) element przed `Symbols` , a następnie dodaj [CommandPlacement](../extensibility/commandplacement-element.md) element, który ma `guid` i `id` polecenia `priority`i element nadrzędny, jak pokazano w poniższym przykładzie.  
  
         <!-- FIXME [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)] -->  
        ```xaml  
        <CommandPlacements>
          <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
            <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
          </CommandPlacement>
        </CommandPlacements>
        ```  
  
         Tworzenie wielu rozmieszczanie polecenia, które mają tego samego GUID:ID i ma różnych elementów nadrzędnych powoduje, że menu mają być widoczne w wielu lokalizacjach. Aby uzyskać więcej informacji, zobacz [CommandPlacements](../extensibility/commandplacements-element.md) elementu.  
  
     Aby uzyskać więcej informacji o grupach polecenia i element nadrzędny, zobacz [tworzenie wielokrotnego użytku grup przycisków](../extensibility/creating-reusable-groups-of-buttons.md).  
  
 W tym momencie polecenie będą widoczne w środowisku IDE, ale nie odniesie żadnych funkcji. Jeśli polecenie zostało utworzone przez szablon pakietu, domyślnie jej obsługi kliknięcia, który zostanie wyświetlony komunikat.  
  
## <a name="handling-the-new-command"></a>Obsługa nowego polecenia  
 Większość używanych poleceń w kodzie zarządzanym mogą być obsługiwane przez Framework zarządzane pakietu (MPF) można skojarzyć polecenie z <xref:System.ComponentModel.Design.MenuCommand> obiektu lub <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu i wdrażanie jej obsługi zdarzeń.  
  
 Kod, który używa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs bezpośrednio do obsługi polecenia, musisz zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu oraz metod jej. Są dwie metody najważniejszych <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Pobierz <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> wystąpienie, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[ButtonGroup#21](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  Utwórz <xref:System.ComponentModel.Design.CommandID> obiektu, który ma jako parametry jego identyfikator GUID i identyfikator polecenia do obsługi, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[ButtonGroup#22](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     Szablon pakietu Visual Studio udostępnia dwie kolekcje `GuidList` i `PkgCmdIDList`, do przechowywania identyfikatorów GUID i identyfikatory poleceń. Te są wypełniane automatycznie poleceń, które są dodawane przez szablon, ale dla poleceń, które można dodać ręcznie, musisz również dodać identyfikator wpisu do `PkgCmdIdList` klasy.  
  
     Alternatywnie można wypełnić <xref:System.ComponentModel.Design.CommandID> obiektu przy użyciu wartości nieprzetworzony ciąg identyfikatora GUID i wartość całkowita identyfikatora.  
  
3.  Utwórz wystąpienie albo <xref:System.ComponentModel.Design.MenuCommand> lub <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiekt, który określa metodę, która obsługuje polecenie razem z <xref:System.ComponentModel.Design.CommandID>, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[ButtonGroup#23](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     <xref:System.ComponentModel.Design.MenuCommand> Jest odpowiednia dla polecenia statycznych. Wyświetla element menu dynamiczne wymagają obsługi zdarzeń QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Dodaje <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> zdarzenie, które występuje, gdy menu hosta polecenia jest otwarty i innych właściwości, takich jak <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Polecenia utworzone przez szablon pakietu są przekazywane, aby domyślnie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu w `Initialize()` metody klasy pakietu.  
  
4.  <xref:System.ComponentModel.Design.MenuCommand> Jest odpowiednia dla polecenia statycznych. Wyświetla element menu dynamiczne wymagają obsługi zdarzeń QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Dodaje <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> zdarzenie, które występuje, gdy menu hosta polecenia jest otwarty i innych właściwości, takich jak <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Polecenia utworzone przez szablon pakietu są przekazywane, aby domyślnie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu w `Initialize()` metody klasy pakietu. Kreator programu Visual Studio implementuje `Initialize` metody przy użyciu `MenuCommand`. Dla Wyświetla element menu dynamiczne, należy zmienić na `OleMenuCommand`, jak to pokazano w następnym kroku. Ponadto aby zmienić tekst elementu menu, należy dodać flagę polecenia TextChanges do przycisku polecenia menu w pliku vsct pokazany w następującym przykładzie  
  
     <!--FIXME [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]-->  
    ```xaml  
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
  
5.  Nowe polecenie w celu przekazania <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metoda <xref:System.ComponentModel.Design.IMenuCommandService> interfejsu. Jest to osiągane przez domyślny dla polecenia utworzone przez szablon pakietu, jak pokazano w poniższym przykładzie  
  
     [!code-csharp[ButtonGroup#24](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  Implementuje metody, która obsługuje polecenie.  
  
#### <a name="to-implement-querystatus"></a>Aby zaimplementować QueryStatus  
  
1.  Zdarzenie QueryStatus występuje przed wyświetleniem polecenia. Dzięki temu właściwości tego polecenia można ustawić zdarzeń programu obsługi przed jego użytkownika. Tylko polecenia, które są dodawane jako <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiekty mogą uzyskiwać dostęp do tej metody.  
  
     Dodaj `EventHandler` do obiektu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> zdarzenia w <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiekt, który służy do obsługi polecenia, jak pokazano w poniższym przykładzie (`menuItem` jest <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> wystąpienie).  
  
     [!code-csharp[MenuText#14](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
     [!code-vb[MenuText#14](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
     `EventHandler` Obiektu podano nazwę metody, które jest wywoływane, gdy stan polecenia menu jest poddawany kwerendzie.  
  
2.  Implementuje metody obsługi stanu zapytania dla polecenia. `object` `sender` Parametru mogą być rzutowane na <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu, który jest używany do ustawiania różnych atrybutów polecenia menu, w tym tekst. W poniższej tabeli przedstawiono właściwości na <xref:System.ComponentModel.Design.MenuCommand> klasy (który klasy MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> pochodną) odpowiadające <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> flagi.  
  
    |Właściwość MenuCommand|Flaga OLECMDF|  
    |--------------------------|------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
     Aby zmienić tekst polecenia, użyj <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> właściwość <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[MenuText#11](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
     [!code-vb[MenuText#11](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
 MPF obsługuje automatycznie w przypadku grup nieobsługiwana lub nieznana. Jeśli polecenie został dodany do <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> przy użyciu <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metoda, polecenie nie jest obsługiwana.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Obsługa poleceń za pomocą iolecommandtarget — interfejs  
 Kod, który używa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu bezpośrednio, pakiet VSPackage musi implementować zarówno <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Jeśli pakiet VSPackage implementuje hierarchii projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu powinny być implementowane w zamian.  
  
 Zarówno <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody zostały zaprojektowane do odbierania pojedynczy zestaw `GUID` i tablicę identyfikatorów poleceń jako dane wejściowe. Zaleca się, że VSPackages obsługują w pełni koncepcji wiele identyfikatorów w jednym wywołaniu. Jednak tak długo, jak pakiet VSPackage nie jest wywoływany z inne pakiety VSPackage, można założyć tablicy polecenia zawiera tylko jeden identyfikator polecenia, ponieważ <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody są wykonywane w dobrze zdefiniowanej kolejności. Aby uzyskać więcej informacji o routingu, zobacz [Routing poleceń w VSPackages](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Kod, który używa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs bezpośrednio do obsługi polecenia, musisz zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody w pakiecie VSPackage w następujący sposób w celu obsługi poleceń.  
  
##### <a name="to-implement-the-querystatus-method"></a>Aby zaimplementować metody QueryStatus  
  
1.  Zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> dla prawidłowych poleceń.  
  
2.  Ustaw `cmdf` elementu `prgCmds` parametru.  
  
     Wartość `cmdf` element jest połączeniem logicznym wartości z <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> wyliczenie połączone przy użyciu operatora logicznego OR (`|`) operatora.  
  
     Użyj odpowiedniej wyliczenia, na podstawie stanu polecenia:  
  
    -   Jeśli polecenie jest obsługiwana:  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Jeśli polecenie ma być niewidoczna w tej chwili:  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Jeśli polecenie jest włączone na i wydaje się kliknięto:  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         W przypadku przetwarzania poleceń, które znajdują się w menu typu `MenuControllerLatched`, pierwsze polecenie zostało oznaczone przez `OLECMDF_LATCHED` flaga jest wyświetlany w menu rozruchu polecenie domyślne. Aby uzyskać więcej informacji na temat `MenuController` menu, zobacz [Menu Element](../extensibility/menu-element.md).  
  
    -   Jeśli polecenie jest aktualnie włączone:  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Jeśli polecenie jest częścią menu skrótów i jest domyślnie ukryty:  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
    -   Jeśli polecenie używa `TEXTCHANGES` Flaga, ustaw `rgwz` elementu `pCmdText` parametru na nowy tekst polecenia i zestaw `cwActual` elementu `pCmdText` parametru do rozmiaru ciąg polecenia.  
  
     Dla warunków błędu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody musi obsługiwać następujących przypadkach błąd:  
  
    -   Jeśli identyfikator GUID jest nieznany lub nie jest obsługiwany, `OLECMDERR_E_UNKNOWNGROUP`.  
  
    -   Jeśli jest znany identyfikator GUID, ale identyfikator polecenia jest nieznany lub nie jest obsługiwany, zwróć `OLECMDERR_E_NOTSUPPORTED`.  
  
 Implementacja pakiet VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody musi także zwracać kodów błędu, w zależności od tego, czy polecenie jest obsługiwana i określa, czy polecenie zostało obsłużone pomyślnie.  
  
##### <a name="to-implement-the-exec-method"></a>Aby zaimplementować Exec — metoda  
  
-   Jeśli polecenie `GUID` jest nieznany, zwróć `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Jeśli `GUID` jest znany, ale polecenie identyfikator jest nieznany, zwraca `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Jeśli `GUID` i polecenia Identyfikatora odpowiada pary GUID:ID, który jest używany przez polecenia w pliku vsct, należy wykonać kod, który jest skojarzony z poleceń i przywracać <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu VSCT XML](../extensibility/vsct-xml-schema-reference.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)