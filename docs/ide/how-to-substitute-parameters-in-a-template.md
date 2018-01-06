---
title: "Dodawanie nazwy parametrów do szablonów projektów i elementów w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecdd277a36cb1c074653edb2af7f1882e6d25ede
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Porady: parametry zastępcze w szablonie

Parametry szablonu umożliwiają Zastąp identyfikatory, takie jak nazwy klas i przestrzenie nazw, gdy tworzony jest plik z szablonu. Dodawanie parametrów szablonu do istniejących szablonów lub tworzyć własne szablony z parametrów szablonu.

Parametry szablonu są zapisywane w formacie $*parametru*$. Aby uzyskać pełną listę parametrów szablonu, zobacz [parametrów szablonu](../ide/template-parameters.md).

Poniższej sekcji przedstawiono sposób zmodyfikować szablonu, aby zastąpić nazwę przestrzeni nazw z nazwą"bezpiecznego projektu".

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Aby użyć parametru zastąpić nazwę przestrzeni nazw

1. Wstaw parametr w co najmniej jeden z plików kodu w szablonie. Na przykład:

    ```csharp
    namespace $safeprojectname$
    ```

1. W pliku .vstemplate szablonu, Znajdź `ProjectItem` element, który zawiera ten plik.

1. Ustaw `ReplaceParameters` atrybutu `true` dla `ProjectItem` elementu:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Zobacz także

[Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)  
[Parametry szablonu](../ide/template-parameters.md)  
[Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)