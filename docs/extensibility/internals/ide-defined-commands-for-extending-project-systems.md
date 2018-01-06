---
title: "Zdefiniowane IDE poleceń do rozszerzania systemów projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3b450a55de29e112d158cb783ad366eb4fbcaca7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Definicja IDE poleceń do rozszerzania systemów projektów
Gdy chcesz rozszerzyć systemów projektów, można użyć poleceń i polecenia grup dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Poniższe sekcje zawierają listę elementów polecenia, które są szczególnie użyteczne w przypadku rozszerzania systemów projektów.  
  
## <a name="command-menus"></a>Polecenia menu  
 W poniższej tabeli przedstawiono menu poleceń, które są przydatne w lokalizacji można umieścić polecenia wysokiego poziomu, które wywołują rozszerzeń projektu.  
  
|Polecenia menu|Opis|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**Projektu** menu najwyższego poziomu.|  
|IDM_VS_TOOL_PROJWIN|**Eksploratora rozwiązań** paska narzędzi.|  
  
## <a name="shortcut-menus"></a>Menu skrótów  
 W poniższej tabeli przedstawiono menu skrótów, które są stosowane po wybraniu jednego węzła w **Eksploratora rozwiązań**, lub gdy występują jednorodnego wielokrotny w **Eksploratora rozwiązań**, czyli gdy wszystkie wybrane węzły są tego samego typu.  
  
|Menu skrótów|Opis|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Stosuje się po wybraniu węzła projektu.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Ma zastosowanie w przypadku wybrania pliku.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Ma zastosowanie w przypadku wybrania folderu.|  
|IDM_VS_CTXT_WEBREFFOLDER|Stosuje przy wybraniu folderu odwołania sieci Web.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Ma zastosowanie w przypadku wybrania odwołań do węzła głównego o nazwie "Odwołuje się do".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Ma zastosowanie, gdy wybrano węzłów odwołania; należą do zestawu COM i tylko odwołania do projektu. Nie ma odwołań sieci Web.|  
  
 W poniższej tabeli przedstawiono menu skrótów, które są stosowane podczas wyboru w **Eksploratora rozwiązań** obejmuje wielu hierarchii  
  
|Menu skrótów|Opis|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Ma zastosowanie, gdy bieżące zaznaczenie zawiera węzeł rozwiązania i węzłów głównych projektu.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera elementy węzła i projektu rozwiązania.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Ma zastosowanie, gdy bieżące zaznaczenie składa się z wielu głównego projektu tylko węzłów.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera mieszane węzłów głównych projektów i elementów projektu. Ponadto zaznaczenie może zawierać węzeł rozwiązania.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera elementy projektu z wielu projektów w rozwiązaniu lub po wybraniu elementów różnych typów w tym samym projekcie.|  
  
## <a name="command-groups"></a>Polecenie grup  
 W poniższej tabeli przedstawiono grupy poleceń, które można używać podczas rozszerzania projektów i dostępnej za pośrednictwem <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu skrótów.  
  
|Polecenie grupy|Opis|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Polecenia służące do tworzenia, ponowne tworzenie i wdrażanie projektu.|  
|IDG_VS_CTXT_COMPILELINK|Polecenia kompilowanie i łączenie projektu.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Polecenia, które ustawienia konfiguracji projektu i kolejność kompilowania.|  
|IDG_VS_CTXT_PROJECT_ADD|Polecenia, które umożliwia dodanie elementów do projektu.|  
|IDG_VS_CTXT_PROJECT_START|Polecenia, które Ustaw projekt startowy skojarzone z klawisz F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Polecenia zapisywania elementów projektu.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Polecenia do debugowania.|  
|IDG_VS_CTXT_PROJECT_SCC|Polecenia służące do kontroli źródła.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Polecenia Wytnij, operacje kopiowania i wklejania.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Polecenia, które zapewniają dostęp do **właściwości projektu** okno dialogowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md)