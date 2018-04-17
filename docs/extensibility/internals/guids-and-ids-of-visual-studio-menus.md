---
title: Identyfikatory GUID oraz identyfikatory menu programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 163f7b81295468a69cfb28959f608a21f94a4a99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Identyfikatory GUID oraz identyfikatory menu programu Visual Studio
W tym temacie wylicza wartości Identyfikator GUID i identyfikator menu i grup na pasku menu programu Visual Studio. Te wartości są definiowane w vsct pliki, które są instalowane jako część programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [IDE-Defined polecenia, menu oraz grup](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Aby uzyskać więcej informacji na temat pracy z obiektami środowiska (IDE) zintegrowanego rozwoju, które są zdefiniowane w plikach vsct, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
 Menu i grupy na pasku menu programu Visual Studio Użyj identyfikatora GUID `guidSHLMainMenu`. Pasek menu ma identyfikator równy `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupy na pasku Menu programu Visual Studio  
 Aby dodać menu do paska menu, należy ustawić jedną z tych grup jak jego obiekt nadrzędny.  
  
|Grupa|ID|  
|-----------|--------|  
|Plik/Edit/widok|IDG_VS_MM_FILEEDITVIEW|  
|Refaktoryzacja|IDG_VS_MM_REFACTORING:|  
|Projekt|IDG_VS_MM_PROJECT|  
|Kompilacja|IDG_VS_MM_BUILDDEBUGRUN|  
|Format/narzędzia|IDG_VS_MM_TOOLSADDINS|  
|Społeczność okna/pomocy|IDG_VS_MM_WINDOWHELP|  
|Dodatki|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu na pasku Menu programu Visual Studio  
 Aby dodać grupę do istniejącego menu programu Visual Studio, należy ustawić jedną z następujących menu jako klasy nadrzędnej. Na tej liście nie znajdują się podmenu.  
  
|Menu|ID|  
|----------|--------|  
|Plik|IDM_VS_MENU_FILE|  
|Edytowanie|IDM_VS_MENU_EDIT|  
|Widok|IDM_VS_MENU_VIEW|  
|Refaktoryzacja|IDM_VS_MENU_REFACTORING|  
|Projekt|IDM_VS_MENU_PROJECT|  
|Kompilacja|IDM_VS_MENU_BUILD|  
|Format|IDM_VS_MENU_FORMAT|  
|Narzędzia|IDM_VS_MENU_TOOLS|  
|Okno|IDM_VS_MENU_WINDOW|  
|Dodatki|IDM_VS_MENU_ADDINS|  
|Społeczność|IDM_VS_MENU_COMMUNITY|  
|Pomoc|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Grupy menu programu Visual Studio  
 Przedstawiono następujące grupy, które jest elementem podrzędnym elementu bezpośrednio z menu na pasku menu programu Visual Studio. Najszybszym sposobem na dodawanie polecenia do menu programu Visual Studio jest wartość dla jednego z tych grup jako element nadrzędny. Grupy, które jest elementem podrzędnym elementu podmenu nie są wyświetlane w tej sekcji.  
  
### <a name="file-menu-groups"></a>Grupy Menu Plik  
  
|Grupa|ID|  
|-----------|--------|  
|Nowy otworzyć|IDG_VS_FILE_FILE|  
|Dodaj|IDG_VS_FILE_ADD|  
|Rozwiązanie|IDG_VS_FILE_SOLUTION|  
|Różne|IDG_VS_FILE_MISC|  
|Zapisanie|IDG_VS_FILE_SAVE|  
|Zmień nazwę|IDG_VS_FILE_RENAME|  
|Przeglądarka|IDG_VS_FILE_BROWSER|  
|Drukuj|IDG_VS_FILE_PRINT|  
|Ostatnio używane|IDG_VS_FILE_MRU|  
|Przenieś|IDG_VS_FILE_MOVE|  
|Zakończ|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Edytowanie grupy Menu  
  
|Grupa|ID|  
|-----------|--------|  
|Cofnij/ponów|IDG_VS_EDIT_UNDOREDO|  
|Wycinanie/kopiowanie/wklejanie|IDG_VS_EDIT_CUTCOPY|  
|Wybierz|IDG_VS_EDIT_SELECT|  
|Przejdź do|IDG_VS_EDIT_GOTO|  
|Znajdź|IDG_VS_EDIT_FIND|  
|Obiekty|IDG_VS_EDIT_OBJECTS|  
|Zlecenia OLE|IDG_VS_EDIT_OLEVERBS|  
|Polecenie również|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Refaktoryzuj grupy Menu  
  
|Grupa|ID|  
|-----------|--------|  
|Wspólne|IDG_REFACTORING_COMMON|  
|Zaawansowane|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Grupy Menu Widok  
  
|Grupa|ID|  
|-----------|--------|  
|Kod formularza|IDG_VS_VIEW_FORMCODE|  
|Przeglądarka|IDG_VS_VIEW_BROWSER|  
|Definiowanie widoków|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|Architekta systemu Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Organizacja systemu Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|Kod przeglądarki|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Deweloperów systemu Windows|IDG_VS_VIEW_DEV_WINDOWS|  
|Paski narzędzi|IDG_VS_VIEW_TOOLBARS|  
|Symbole|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Przejdź|IDG_VS_VIEW_NAVIGATE|  
|Małe przejdź|IDG_VS_VIEW_SMALLNAVIGATE|  
|Przeglądarka obiektów|IDG_VS_VIEW_OBJBRWSR|  
|Polecenie również|IDG_VS_VIEW_COMMANDWELL|  
|Strony właściwości|IDG_VS_VIEW_PROPPAGES|  
|Odśwież|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Grupy Menu projektu  
  
|Grupa|ID|  
|-----------|--------|  
|Różne Dodaj|IDG_VS_PROJ_MISCADD|  
|Dodaj|IDG_VS_PROJ_ADD|  
|Folder|IDG_VS_PROJ_FOLDER|  
|Zwolnienie/Załaduj ponownie|IDG_VS_PROJ_UNLOADRELOAD|  
|Tematy pomocy|IDG_VS_PROJ_REFERENCE|  
|Opcje|IDG_VS_PROJ_OPTIONS|  
|Ustawienia|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Tworzenie grupy Menu  
  
|Grupa|ID|  
|-----------|--------|  
|Rozwiązanie|IDG_VS_BUILD_SOLUTION|  
|Wybór|IDG_VS_BUILD_SELECTION|  
|Optymalizacja sterowana profilem|IDG_VS_PGO_SELECTION|  
|Różne|IDG_VS_BUILD_MISC|  
|Anuluj|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Grupy Menu narzędzia  
  
|Grupa|ID|  
|-----------|--------|  
|Wiersz polecenia|IDG_VS_TOOLS_CMDLINE|  
|Wstawki kodu programu|IDG_VS_TOOLS_SNIPPETS|  
|Podzbiór obiektów|IDG_VS_TOOLS_OBJSUBSET|  
|Opcje|IDG_VS_TOOLS_OPTIONS|  
|Inne 2|IDG_VS_TOOLS_OTHER2|  
|Narzędzia zewnętrzne|IDG_VS_TOOLS_EXT_TOOLS|  
|Dostosowywanie zewnętrznych|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Grupy Menu okna  
  
|Grupa|ID|  
|-----------|--------|  
|New|IDG_VS_WINDOW_NEW|  
|Zamknij/doku.|IDG_VS_DOCKCLOSE|  
|Ukryj/doku.|IDG_VS_DOCKHIDE|  
|Rozmieść|IDG_VS_WINDOW_ARRANGE|  
|Nawigacji|IDG_VS_WINDOW_NAVIGATION|  
|Lista|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Grupy Menu Pomoc  
  
|Grupa|ID|  
|-----------|--------|  
|Przykłady|IDG_VS_HELP_SAMPLES|  
|Obsługa|IDG_VS_HELP_SUPPORT|  
|Informacje|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Podmenu menu programu Visual Studio  
 Następująca hierarchia zawiera podmenu, które są skojarzone z menu na pasku menu programu Visual Studio. Ponieważ tylko grupa może mieć menu, jak jego obiekt nadrzędny, co podmenu musi elementem podrzędnym elementu z grupy menu, zamiast bezpośrednio z menu. Aby uzyskać więcej informacji na temat relacji między menu, grup i podmenu, zobacz [dodawanie do Menu podmenu](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Nazwy menu na pasku menu programu Visual Studio są oddzielnie niewidoczne w tej hierarchii ponieważ one nie można wywnioskować z konwencji nazewnictwa grup w IDE w następujący sposób: IDG_VS_*nazwy Menu*_*Nazwa grupy*.  
  
|Grupy nadrzędnej|Podmenu|Grupy podrzędne|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1... 6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>Zobacz też  
 [Identyfikatory GUID oraz identyfikatory pasków narzędzi Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)