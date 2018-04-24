---
title: Dodawanie nazwy parametrów do szablonów projektów i elementów w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0439ffd8e7994995dd3eaafed8e0b0fb2a57d282
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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

1. W *.vstemplate* pliku szablonu, Znajdź `ProjectItem` element, który zawiera ten plik.

1. Ustaw `ReplaceParameters` atrybutu `true` dla `ProjectItem` elementu:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Zobacz także

[Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)  
[Parametry szablonu](../ide/template-parameters.md)  
[Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  
[Projectitem — element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)