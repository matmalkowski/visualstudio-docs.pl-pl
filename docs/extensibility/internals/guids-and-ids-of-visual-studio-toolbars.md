---
title: "Identyfikatory GUID oraz identyfikatory pasków narzędzi Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bbb14818cebb35f703ec6f5ade084d96ac383d6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Identyfikatory GUID oraz identyfikatory pasków narzędzi Visual Studio
W tym temacie wylicza wartości Identyfikator GUID i identyfikator pasków narzędzi, które znajdują się w programie Visual Studio zintegrowane środowisko programistyczne (IDE) i grupy mogą zawierać. Te wartości są definiowane w vsct pliki, które są instalowane jako część programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [IDE-Defined polecenia, menu oraz grup](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Wiele pasków narzędzi dostępnych dla programu Visual Studio nie są zdefiniowane przez program Visual Studio i ich identyfikatorów GUID i identyfikator wartości nie są publicznie udostępniane. W tym temacie wymieniono tylko paski narzędzi, które są zdefiniowane w Visual Studio SDK vsct plików.  
  
 Aby uzyskać więcej informacji na temat pracy z obiektami IDE, które są zdefiniowane w plikach vsct, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
 Domyślne paski narzędzi dostarczonych przez środowiska IDE programu Visual Studio Użyj identyfikatora GUID `guidSHLMainMenu`, z wyjątkiem inaczej przy użyciu składni GUID:ID.  
  
## <a name="ide-toolbars"></a>Paski narzędzi IDE  
 Następujące paski narzędzi są dostarczane przez środowiska IDE programu Visual Studio. Paski narzędzi można wyświetlić, wybierając je na **paski narzędzi** podmenu **narzędzia** menu. Paski narzędzi w systemie windows narzędzia nie znajdują się w tej sekcji.  
  
 Tylko grupy można elementem podrzędnym elementu bezpośrednio pasków narzędzi. Aby dodać grupę, ustaw jego element nadrzędny identyfikator GUID i identyfikator paska narzędzi. Aby dodać przycisku paska narzędzi, należy ustawić nadrzędnego do grupy na pasku narzędzi.  
  
|Pasek narzędzi|ID|  
|-------------|--------|  
|Standard|IDM_VS_TOOL_STANDARD|  
|Kompilacja|IDM_VS_TOOL_BUILD|  
|Edytor tekstu|IDM_VS_TOOL_TEXTEDITOR|  
|Debugowanie|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Lokalizacja debugowania|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Specjalne paski narzędzi  
 Te paski narzędzi są definiowane przez środowiska IDE programu Visual Studio, ale służą funkcje specjalne i nie obsługują polecenia grup.  
  
|Pasek narzędzi|ID|  
|-------------|--------|  
|Polecenie Add|IDM_VS_TOOL_ADDCOMMAND|  
|Niezdefiniowana|IDM_VS_TOOL_UNDEFINED|  
|schemat XML|IDM_VS_TOOL_SCHEMA|  
|Dane XML|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Grupy na paskach narzędzi IDE  
 Aby dodać przycisk na standardowym pasku narzędzi, należy ustawić jedną z następujących grup jako klasy nadrzędnej. Grupy są sortowane według nadrzędne paska narzędzi.  
  
### <a name="standard-toolbar-groups"></a>Grupy na standardowym pasku narzędzi  
  
|Nazwa|ID|  
|----------|--------|  
|Zapisywanie i otwieranie|IDG_VS_TOOLSB_SAVEOPEN|  
|Wytnij/Kopiuj|IDG_VS_TOOLSB_CUTCOPY|  
|Cofnij/ponów|IDG_VS_TOOLSB_UNDOREDO|  
|Uruchom/kompilacji|IDG_VS_TOOLSB_RUNBUILD|  
|Wyszukaj|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|Nowe okno|IDG_VS_TOOLSB_NEWWINDOWS|  
|Ładowanie/zapisywanie|IDG_VS_WINDOWUI_LOADSAVE|  
|Miernika|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Tworzenie grup paska narzędzi  
  
|Nazwa|ID|  
|----------|--------|  
|Pasek kompilacji|IDG_VS_BUILDBAR|  
|Anuluj|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Grupy paska narzędzi edytora tekstu  
  
|Nazwa|ID|  
|----------|--------|  
|Zakończenie|IDM_VS_TOOL_TEXTEDITOR|  
|Wcięcie|IDG_VS_EDITTOOLBAR_INDENT|  
|Komentarz|IDG_VS_EDITTOOLBAR_COMMENT|  
|Zakładki|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Debugowanie grup paska narzędzi  
  
|Nazwa|ID|  
|----------|--------|  
|Wykonanie|IDM_DEBUG_TOOLBAR|  
|Wykonywanie krok po kroku|IDG_DEBUG_TOOLBAR_STEPPING|  
|Czujki|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Lokalizacja grupy narzędzi debugowania  
  
|Nazwa|ID|  
|----------|--------|  
|Lokalizacja debugowania|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Paski narzędzi okna narzędzi  
 Paski narzędzi mogą być wyświetlane bezpośrednio w IDE lub okna narzędzi takich jak **Eksploratora rozwiązań**. Ponieważ narzędzia systemu windows nie są zdefiniowane w plikach vsct, paski narzędzi okna narzędzi nie mają zdefiniowanych obiektów nadrzędnych. Zamiast tego są umieszczane w kodzie. W poniższej tabeli przedstawiono paski narzędzi, które znajdują się w narzędzia systemu windows w środowisku IDE i grup polecenia, które zawierają.  
  
> [!NOTE]
>  Paski narzędzi i grup, użyj identyfikatora GUID `guidSHLMainMenu`, z wyjątkiem inaczej przy użyciu składni GUID:ID. W przypadku, gdy określono identyfikator GUID dla paska narzędzi, ma również zastosowanie do grup, które jest elementem podrzędnym elementu w pasku narzędzi.  
  
|Okna narzędzi|Pasek narzędzi|Grupy|  
|-----------------|-------------|------------|  
|Eksplorator rozwiązań|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|Server Explorer|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Właściwości|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Widok klas|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Widok klas|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Przeglądarka obiektów|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Przeglądarka obiektów|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Dane wyjściowe|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Znajdź i zamień|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Znajdź wyniki 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Znajdź wyniki 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|fragment kodu|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Zakładki|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Lista zadań|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Zadania użytkownika|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Lista błędów|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Wywołanie przeglądarki|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Punkty przerwania|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Dezasemblacji|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Pamięć 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|Procesy|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie kontrolera Menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Dodawanie do okna narzędzi paska narzędzi](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)