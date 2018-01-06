---
title: "Szablony Visual Studio dla projektów i pliki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3959b01fdfc0ff77bdd5a3ffa0c96366b9da87d7
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="project-and-item-templates"></a>Szablony projektów i elementów

Szablony projektu i elementu zapewniają klas zastępczych wielokrotnego użytku, które zapewniają użytkownikom niektóre podstawowe kodu i struktury, które można dostosowywać do własnych celów.

## <a name="visual-studio-templates"></a>szablony Visual Studio

Wiele wstępnie zdefiniowanych projekt oraz szablony elementów są zainstalowane z programem Visual Studio. Na przykład Visual Basic i C# **aplikacji formularzy systemu Windows** i **biblioteki klas** szablonów, które są wyświetlane w **nowy projekt** okno dialogowe są szablony projektów. Szablony elementów są wyświetlane w **Dodaj nowy element** okna dialogowego pole i obejmują elementy, takie jak pliki kodu, pliki XML, stron HTML i arkuszy stylów.

Te szablony stanowią punkt wyjścia dla użytkowników, aby rozpocząć tworzenie projektów ani rozszerzyć istniejących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Szablony elementów może należeć do zakresu złożonością z pojedynczego pusty plik zawierający określone rozszerzenie pliku, do elementów wielu plików, który zawiera, na przykład, pliki kodu źródłowego, których szkieletu kodu plików projektanta informacje i zasoby osadzone.

Oprócz zainstalowanych szablonów w **nowy projekt** i **Dodaj nowy element** okien dialogowych, można tworzyć własne szablony, lub pobierania i użyj tworzone przez społeczność. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu

Wszystkie szablony projektów i elementów, czy zainstalowane z programem Visual Studio lub utworzone przez użytkownika, funkcji przy użyciu tych samych zasad i mieć spisu treści. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Dotyczy to plików kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.

- Jeden plik .vstemplate. Ten plik zawiera metadanych, który zawiera informacje potrzebne do wyświetlenia szablonu w **nowy projekt** i **Dodaj nowy element** okien dialogowych i utworzyć projektu lub elementu z szablonu. Aby uzyskać więcej informacji na temat plików .vstemplate zobacz [parametrów szablonu](../ide/template-parameters.md).

Jeśli te pliki są skompresowane w pliku .zip i umieszcza w prawidłowym folderze, Visual Studio automatycznie wyświetli je w następujących miejscach:

- Szablony projektu są wyświetlane w **nowy projekt** okno dialogowe.

- Szablony elementów są wyświetlane w **Dodaj nowy element** okno dialogowe.

Aby uzyskać więcej informacji o folderach szablonów, zobacz [porady: lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Zestawy początkowe

Zestawy startowe są rozszerzone przez szablony, które mogą być współużytkowane z innymi członkami społeczności. Zestaw startowy zawiera przykłady kodu, które kompilują, dokumentację i inne zasoby, aby pomóc użytkownikom poznać nowe narzędzia i techniki programowania, podczas tworzenia użytecznych, rzeczywistych aplikacji. Podstawowe zawartości i procedury zestawu startowego są identyczne z tymi szablonami. Aby uzyskać więcej informacji, zobacz [porady: tworzenie Starter Kit](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Zobacz także

[Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)  
[Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)  
[Parametry szablonu](../ide/template-parameters.md)  
[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[Pakiety NuGet w szablony programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)