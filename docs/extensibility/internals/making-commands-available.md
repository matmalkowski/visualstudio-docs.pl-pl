---
title: "Udostępnianie poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e9644353430fa70d6876ab3210ad340ac30312d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="making-commands-available"></a>Udostępnianie poleceń
Po wielu VSPackages są dodawane do programu Visual Studio, interfejs użytkownika (UI) może stać się przepełniona za pomocą polecenia. Można programów pakietu w celu ograniczenia tego problemu w następujący sposób:  
  
-   Program pakietu, dzięki czemu jest on załadowany tylko wtedy, gdy użytkownik wymaga go.  
  
-   Program pakietu, dzięki czemu jego poleceń są wyświetlane tylko wtedy, gdy mogą być wymagane w kontekście bieżącego stanu zintegrowane środowisko programistyczne (IDE).  
  
## <a name="delayed-loading"></a>Opóźnienie załadowanie  
 Typowy sposób włączania jest opóźnione ładowanie do projektowania pakiet VSPackage, dzięki czemu jego poleceń są wyświetlane w interfejsie użytkownika, ale sam pakiet nie został załadowany, dopóki użytkownik kliknie jedno z poleceń. Aby to osiągnąć, w pliku vsct, Utwórz polecenia, które mają żadnych flag polecenia.  
  
 Poniższy przykład przedstawia definicję polecenia menu z pliku vsct. To polecenie, które są generowane przez szablon do pakietu programu Visual Studio po **polecenie** wybrano opcję w szablonie.  
  
```xml  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 W tym przykładzie Jeśli grupy nadrzędnej `MyMenuGroup`, jest elementem podrzędnym elementu menu najwyższego poziomu, takich jak **narzędzia** menu polecenie będzie widoczne w tym menu, ale pakiet, który wykonuje polecenie nie zostanie załadowany, dopóki nie zostanie kliknięty polecenia przez użytkownika. Jednak przez polecenie, aby zaimplementować programowania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, można włączyć pakiet, który ma być ładowane, gdy najpierw rozwijane menu, który zawiera polecenie.  
  
 Zwróć uwagę, że opóźnionego ładowania także może zwiększyć wydajność rozruchu.  
  
## <a name="current-context-and-the-visibility-of-commands"></a>Bieżący kontekst i widoczności poleceń  
 Można programu pakiet VSPackage poleceń, aby być widoczne czy ukryte, w zależności od bieżącego stanu danych pakiet VSPackage lub akcje, które są obecnie istotne. Można włączyć pakiet VSPackage można ustawić stanu polecenia, zwykle za pomocą implementacja <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, ale wymaga pakiet VSPackage do załadowania przed umożliwia wykonanie kodu. Zamiast tego zaleca się włączenie IDE w celu zarządzania widoczności poleceń bez ładowania pakietu. W tym celu w pliku vsct kojarzenie poleceń z co najmniej jeden kontekst specjalne interfejsu użytkownika. Te konteksty interfejsu użytkownika są identyfikowane przez identyfikator GUID znany jako *kontekst polecenia GUID*.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]monitoruje zmiany wynikające z działania użytkownika, takie jak ładowania projektu lub edytowanie zamierza budynku. Wygląd IDE automatycznie są modyfikowane w chwili wystąpienia zmian. W poniższej tabeli przedstawiono cztery główne kontekstach IDE zmienić [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitorów.  
  
|Typ kontekstu|Opis|  
|---------------------|-----------------|  
|Typ aktywnego projektu|Dla większości typów projektów to `GUID` wartość jest taki sam jak identyfikator GUID pakiet VSPackage, który implementuje projektu. Jednak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów Użyj typu projektu `GUID` jako wartość.|  
|Aktywne okno|Zazwyczaj jest to okno aktywnego dokumentu ostatniego ustanawia bieżącego kontekstu interfejsu użytkownika dla powiązania klucza. Jednak może również być okna narzędzia, która zawiera tabelę powiązania klucza podobny wewnętrznej przeglądarce sieci Web. Dla okna z wieloma kartami dokumentów, takich jak edytor HTML, co karta ma kontekstu inne polecenie `GUID`.|  
|Usługa Active języka|Usługa języka skojarzonego z plikiem, który jest aktualnie wyświetlany w edytorze tekstów.|  
|Aktywnego okna narzędzi|Okno narzędzia, który jest otwarty i ma fokus.|  
  
 Piąty obszar głównych kontekstu jest stan interfejsu użytkownika IDE. Konteksty interfejsu użytkownika są identyfikowane za pomocą aktywny kontekst polecenia `GUID`s, w następujący sposób:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 Te identyfikatory GUID są oznaczone jako aktywny lub nieaktywny, w zależności od bieżącego stanu środowiska IDE. Wielu kontekstów interfejsu użytkownika mogą być aktywne w tym samym czasie.  
  
### <a name="hiding-and-displaying-commands-based-on-context"></a>Ukrywanie i wyświetlanie poleceń na podstawie kontekstu  
 Można wyświetlenie lub ukrycie polecenie pakietu w IDE bez ładowania pakietu, do samej siebie. W tym celu należy określić polecenie w pliku vsct pakietu przy użyciu `DefaultDisabled`, `DefaultInvisible`, i `DynamicVisibility` polecenia flagi i dodać co najmniej jeden [VisibilityItem](../../extensibility/visibilityitem-element.md) elementy [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sekcji. Gdy w kontekście określonego polecenia `GUID` staje się aktywny, polecenia zostanie wyświetlony bez ładowania pakietu.  
  
### <a name="custom-context-guids"></a>Identyfikatory GUID kontekstu niestandardowych  
 Jeśli kontekst odpowiednie polecenia, którego identyfikator GUID nie jest już zdefiniowany, można zdefiniować w VSPackage i następnie program to być aktywne lub nieaktywne zgodnie z wymaganiami, aby kontrolować widoczności poleceń. Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi do:  
  
-   Zarejestruj identyfikatorów GUID kontekstu (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody).  
  
-   Pobierz stan kontekstu `GUID` (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody).  
  
-   Włącz kontekstu `GUID`s włączać i wyłączać (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody).  
  
    > [!CAUTION]
    >  Upewnij się, że VSPackage nie wpływa na stan dowolnego kontekstu istniejący identyfikator GUID, ponieważ inne pakiety VSPackage może zależeć od nich.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie polecenia pakiet VSPackage pokazano dynamiczne widoczność polecenie, które jest zarządzane przez polecenie kontekstów bez ładowania pakiet VSPackage.  
  
 Polecenie ustawiono włączony i wyświetlane zawsze, gdy rozwiązanie istnieje; oznacza to, że zawsze, gdy jeden z następujących kontekst polecenia identyfikatorów GUID jest aktywna:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 W tym przykładzie należy zauważyć, że każdy flagi polecenia jest oddzielnej [flagi polecenie](../../extensibility/command-flag-element.md) elementu.  
  
```  
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"   
        priority="0x0100" type="Button">  
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <CommandFlag>DefaultDisabled</CommandFlag>  
  <CommandFlag>DefaultInvisible</CommandFlag>  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <CommandName>cmdidMyCommand</CommandName>  
    <ButtonText>My Command name</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 Również powiadomienie, które każdy kontekst interfejsu użytkownika muszą być umieszczone w oddzielnej `VisibilityItem` elementu w następujący sposób.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing poleceń w VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Dynamiczne dodawanie elementów Menu](../../extensibility/dynamically-adding-menu-items.md)