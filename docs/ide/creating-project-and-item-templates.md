---
title: Szablony Visual Studio dla projektów i plików
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62e51a5a03011874acc723eaf159e3f7130d1340
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573261"
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektu i elementu zapewniają klas zastępczych wielokrotnego użytku, które zapewniają użytkownikom niektóre podstawowe kodu i struktury, które można dostosowywać do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

Wiele wstępnie zdefiniowanych projekt oraz szablony elementów są zainstalowane z programem Visual Studio. Na przykład Visual Basic i C# **aplikacji formularzy systemu Windows** i **biblioteki klas** szablonów, które są wyświetlane w **nowy projekt** okno dialogowe są szablony projektów. Element Pokaż szablony w **Dodaj nowy element** okna dialogowego pole i obejmują elementy, takie jak pliki kodu, pliki XML, stron HTML i arkuszy stylów.

Te szablony stanowią punkt wyjścia dla użytkowników, aby rozpocząć tworzenie projektów ani rozszerzyć istniejących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablony elementów można dostosować w zakresie rozwiązania od jednego pusty plik zawierający określone rozszerzenie pliku, wielu plików kodu źródłowego z kodem stub plików projektanta informacje i zasoby osadzone.

Za pomocą szablonów zainstalowanych w **nowy projekt** i **Dodaj nowy element** okien dialogowych, tworzyć własne szablony, lub pobranie i użycie szablony utworzone przez społeczność. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektów i elementów, czy zainstalowane z programem Visual Studio lub utworzone przez użytkownika, funkcji przy użyciu tych samych zasad i mieć spisu treści. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Te pliki zawierają pliki kodu źródłowego, zasoby osadzone, pliki projektu i tak dalej.

- Jeden *.vstemplate* zawierający metadane wymagane do wyświetlenia szablonu w **nowy projekt** i **Dodaj nowy element** okien dialogowych i tworzenia projektu lub elementu z szablon. Aby uzyskać więcej informacji na temat *.vstemplate* plików, zobacz [parametrów szablonu](../ide/template-parameters.md).

Jeśli te pliki są skompresowane w *.zip* plików i umieścić w prawidłowym folderze, Visual Studio automatycznie wyświetli je w następujących miejscach:

- Szablony projektu są wyświetlane w **nowy projekt** okno dialogowe.

- Szablony elementów są wyświetlane w **Dodaj nowy element** okno dialogowe.

Aby uzyskać więcej informacji o folderach szablonów, zobacz [porady: lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Pakiety NuGet w szablony programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)