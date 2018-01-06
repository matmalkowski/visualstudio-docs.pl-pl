---
title: Menu Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 58b948e7ec420442eae839cd4eeefbccbe6b509d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="menu-element"></a>Menu Element
Definiuje jeden element menu. Są to sześć menu: kontekstu, Menu MenuController, MenuControllerLatched, narzędzi i ToolWindowToolbar.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikator GUID/identyfikator polecenia.|  
|identyfikator|Wymagany. Identyfikator GUID/identyfikator identyfikator polecenia.|  
|priorytet|Opcjonalny. Wartość liczbowa, która określa względne położenie menu w grupy menu.|  
|ToolbarPriorityInBand|Opcjonalny. Wartość liczbowa, który określa względne położenie paska narzędzi w przedziale, gdy okno jest zadokowany.|  
|— typ|Opcjonalny. Wartość wyliczenia, która określa rodzaj elementu.<br /><br /> Jeśli nie istnieje, domyślnym typem jest Menu.<br /><br /> Kontekst<br /> Menu skrótów, które jest wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy okna. Menu skrótów ma następującą charakterystykę:<br /><br /> -Nie używa pola nadrzędne i priorytet, gdy menu ma być wyświetlany jako menu skrótów.<br />-Może służyć jako podmenu, a także jako menu skrótów. W takim przypadku zarówno Identyfikatora grupy, jak i priorytet pola są przestrzegane.<br />— Nie jest zawsze dostępna.<br /><br /> Menu skrótów jest wyświetlana tylko wtedy, gdy są spełnione następujące warunki:<br /><br /> Zostanie wyświetlone okno, udostępniającym go.<br />-Obsługi myszy w pakiecie VSPackage wykrywa, kliknij prawym przyciskiem myszy w oknie, a następnie wywołuje metodę, która obsługuje polecenie.<br />-Menu skrótów wyświetlony po wywołaniu <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> — metoda (zalecane podejście) lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metody.<br /><br /> Menu<br /> Udostępnia menu rozwijanego. Menu rozwijane ma następującą charakterystykę:<br /><br /> -Względem elementu nadrzędnego w jego definicji.<br />-Musi mieć grupę nadrzędną lub CommandPlacement do grupy.<br />— Może być podmenu w dowolny inny rodzaj menu.<br />— Automatycznie jest wyświetlane zawsze, gdy zostanie wyświetlone menu jej nadrzędnej.<br />— Nie wymaga wykonania dowolnego kodu pakiet VSPackage, aby była wyświetlana.<br /><br /> MenuController<br /> Udostępnia menu rozwijanego przycisku podziału, która zwykle jest używana na paskach narzędzi. MenuController menu ma następującą charakterystykę:<br /><br /> -Musi być zawarty w innym menu za pomocą nadrzędnej lub CommandPlacement.<br />-Względem elementu nadrzędnego w jego definicji.<br />-Mogą mieć dowolny rodzaj menu jako klasy nadrzędnej.<br />-Jest automatycznie udostępniane zawsze, gdy zostanie wyświetlone menu jej nadrzędnej.<br />— Nie wymaga wsparcia programowego, aby wyświetlić menu.<br /><br /> Polecenia menu przycisku podziału jest wyświetlany na przycisku menu. Polecenie wyświetlane ma jeden z następujących właściwości:<br /><br /> -Jest ostatnie polecenie, które zostało użyte, jeśli polecenie jest nadal wyświetlana.<br />-Jest pierwsze polecenie wyświetlane.<br /><br /> MenuControllerLatched<br /> Udostępnia menu rozwijanego przycisku podziału, dla którego polecenia można określić jako domyślny wybór oznaczając polecenie jako zablokowane.<br /><br /> Polecenie zamknięcia jest polecenie, które jest oznaczony w menu jako wybrany, zwykle za pomocą wyświetlania znacznik wyboru. Polecenie może być oznaczony jako zablokowane, jeśli ma ona OLECMDF_LATCHED Flaga na niej w celu wykonania `QueryStatus` metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. MenuControllerLatched menu ma następującą charakterystykę:<br /><br /> -Musi być zawarty w innym menu za pośrednictwem grupy nadrzędnej lub CommandPlacement.<br />-Względem elementu nadrzędnego w jego definicji.<br />-Mogą mieć dowolny rodzaj menu jako klasy nadrzędnej.<br />-Staje się dostępny, gdy zostanie wyświetlone menu jej nadrzędnej.<br />— Nie wymaga wsparcia programowego, aby wyświetlić menu.<br /><br /> Polecenia menu przycisku podziału jest wyświetlany na przycisku menu. Polecenie wyświetlane ma jeden z następujących właściwości:<br /><br /> -Jest pierwsze polecenie wyświetlane jest zablokowane.<br />-Jest pierwsze polecenie wyświetlane.<br /><br /> Pasek narzędzi<br /> Udostępnia pasek narzędzi. Pasek narzędzi o następujących cechach:<br /><br /> -Ignoruje elementu nadrzędnego w jego definicji.<br />-Nie można wprowadzić podmenu żadnej grupy nie nawet przy użyciu CommandPlacement.<br />-Zawsze można wyświetlić, klikając **paski narzędzi** na **widoku** menu.<br />— Można wyświetlić przy użyciu [VisibilityItem](../extensibility/visibilityitem-element.md).<br />— Nie wymaga żadnego kodu, aby go utworzyć. Na przykład dotyczących sposobu tworzenia paska narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Udostępnia narzędzi, który jest dołączony do określonej okno tak samo, jak paska narzędzi jest dołączony do środowiska projektowego.<br /><br /> -Ignoruje elementu nadrzędnego w jego definicji.<br />-Nie można wprowadzić podmenu żadnej grupy nie nawet przy użyciu CommandPlacement.<br />-Jest wyświetlana tylko wtedy, gdy jest wyświetlana okna narzędzia, która obsługuje pasku narzędzi i pakiet VSPackage jawnie dodaje pasek narzędzi okna narzędzia. Jest to zazwyczaj wykonywane podczas tworzenia okna narzędzia, uzyskując właściwości hosta paska narzędzi (reprezentowany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfejsu) z ramki okna narzędzia, a następnie wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metody.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Opcjonalny. Element nadrzędny elementu menu.|  
|CommandFlag|Wymagany. Zobacz [polecenia Element flagi](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag Menu są następujące:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -tej flagi nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **DontCache**<br />-   **DynamicVisibility** -tej flagi nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Ciągi|Wymagany. Zobacz [ciągi elementu](../extensibility/strings-element.md). Obiekt podrzędny `ButtonText` musi być zdefiniowany element.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakiet VSPackage.|  
  
## <a name="example"></a>Przykład  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)