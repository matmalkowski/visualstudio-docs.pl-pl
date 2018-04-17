---
title: Definicja IDE polecenia, menu i grupy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b65266ad3367df5cebeabc251bc8bceb6cda7075
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ide-defined-commands-menus-and-groups"></a>Definicja IDE polecenia, menu i grupy
Wiele menu poleceń i polecenia grup są już zdefiniowane na potrzeby używania przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Te polecenia są również dostępne do użycia podczas rozszerzania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Znajdowanie poleceń zdefiniowanych w środowisku  
 Polecenia środowiska są zdefiniowane w zestawie cztery pliki vsct:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Te pliki znajdują się w  *\<ścieżki instalacji programu Visual Studio SDK >*\VisualStudioIntegration\Common\Inc\\. Te pliki zawierają definicje i identyfikatory GUID menu i grupy, które można używać w pliku konfiguracji (vsct) tabeli polecenia VSPackage jako kontenery własne menu, grup i poleceń.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Udostępnia wartości identyfikatora GUID i identyfikator menu na pasku menu programu Visual Studio i grup, które zawierają.  
  
 [Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Podano identyfikator GUID i identyfikator wartości pasków narzędzi w programie Visual Studio IDE i grup, które zawierają.  
  
 [Identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Udostępnia wartości Identyfikator GUID i identyfikator polecenia zdefiniowane przez środowiska IDE programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Definicja IDE poleceń do rozszerzania systemów projektów](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)