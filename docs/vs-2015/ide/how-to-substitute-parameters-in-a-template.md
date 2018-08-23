---
title: 'Instrukcje: zastępowanie parametrów w szablonie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7e3fea66b23d86378ff4afb81a7d4f46f5090d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679269"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Porady: parametry zastępcze w szablonie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Zastąp parametry w szablonie](https://docs.microsoft.com/visualstudio/ide/how-to-substitute-parameters-in-a-template).  
  
Można zastąpić parametry szablonu, takich jak nazwy klasy, a przestrzenie nazw, gdy plik na podstawie szablonu zostanie utworzona. Aby uzyskać pełną listę parametrów szablonu, zobacz [parametry szablonu](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Procedura  
 Po każdym utworzeniu projektu na podstawie tego szablonu można zastąpić parametry w plikach szablonu. Ta procedura wyjaśnia, jak utworzyć szablon, który zastępuje nazwę obszaru nazw, bezpieczna Nazwa projektu podczas tworzenia nowego projektu z szablonem.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Aby użyć parametru zastąpić nazwę przestrzeni nazw nazwa projektu  
  
1.  Wstaw parametr w co najmniej jeden z plików kodu w szablonie. Na przykład:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Parametry szablonu są zapisywane w formacie $*parametru*$.  
  
2.  W pliku .vstemplate szablonu zlokalizuj `ProjectItem` element, który zawiera ten plik.  
  
3.  Ustaw `ReplaceParameters` atrybutu `true` dla `ProjectItem` elementu. Na przykład:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)



