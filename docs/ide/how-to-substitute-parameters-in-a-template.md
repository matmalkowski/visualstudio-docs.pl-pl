---
title: "Porady: parametry zastępcze w szablonie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6e13e704502443c371021c515c7a9578497f829
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Porady: parametry zastępcze w szablonie
Można zastąpić parametry szablonu, takie jak nazwy klas i utworzeniu przestrzeni nazw, gdy plik na podstawie szablonu. Aby uzyskać pełną listę parametrów szablonu, zobacz [parametrów szablonu](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Procedura  
 Zawsze, gdy tworzony jest projekt na podstawie tego szablonu można zastąpić parametry w plikach szablonu. Ta procedura wyjaśnia sposób tworzenia szablonu, który zastępuje nazwę przestrzeni nazw nazwa projektu bezpieczne podczas tworzenia nowego projektu z szablonem.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Aby użyć parametru należy zastąpić nazwą przestrzeni nazw nazwa projektu  
  
1.  Wstaw parametr w co najmniej jeden z plików kodu w szablonie. Na przykład:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Parametry szablonu są zapisywane w formacie $*parametru*$.  
  
2.  W pliku .vstemplate szablonu, Znajdź `ProjectItem` element, który zawiera ten plik.  
  
3.  Ustaw `ReplaceParameters` atrybutu `true` dla `ProjectItem` elementu. Na przykład:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Projectitem — Element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)