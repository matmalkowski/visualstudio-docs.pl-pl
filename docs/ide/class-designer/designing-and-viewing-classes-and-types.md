---
title: Za pomocą projektanta klas
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4e4cf8e21f3f053783b1f7b70dcc51f2fd4ef2a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447963"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Projektowanie i widoku klas i typów za pomocą projektanta klas

Projektowanie, zwizualizować i Refaktoryzuj klasami i innymi typami w kodzie z **Projektant klas** w programie Visual Studio. Diagramy klas umożliwia tworzenie i edytowanie klas do projektu C#, VB lub C++. Diagramy klas umożliwia również struktury projektu na lepsze zrozumienie lub zreorganizować kodu.

## <a name="what-you-can-do-with-class-diagrams"></a>Co można zrobić przy użyciu diagramów klasy

- **Projekt**: edytowanie kodu projektu, edytując diagramu klas. Dodawanie nowych elementów i usuń niepożądane. Zmiany są odzwierciedlane w kodzie.

- **Wizualizuj**: zrozumienie struktury projektu, wyświetlając klas w projekcie na diagramie. Dostosowywanie diagramu, dzięki czemu można skupić się na szczegółami projektu, które najbardziej interesujących Cię. Zapisz diagramu do użycia w przyszłości dla celów demonstracyjnych i dokumentacji.

- **Refaktoryzuj**: Przesłaniaj metody, Zmień nazwę identyfikatory Refaktoryzuj parametrów i implementować interfejsów i klas abstrakcyjnych.

## <a name="view-types-and-relationships"></a>Wyświetlanie typów i relacji

Diagramy klas Pokaż szczegóły typów, na przykład ich elementy Członkowskie składające i relacji między nimi. Wizualizacja tych jednostek jest widoku dynamicznego do kodu. Oznacza to, że można edytować typy w Projektancie i sprawdzić, zmiany zostaną uwzględnione w kodzie źródłowym jednostki. Podobnie diagram klas jest synchronizowana z zmiany wprowadzone do plików kodu.

> [!NOTE]
> Jeśli projekt zawiera diagram klas i projekt odwołuje się do typu, który znajduje się w innym projekcie, diagram klas nie są wyświetlane typu występującego w odwołaniu do czasu kompilacji projektu dla tego typu. Podobnie diagram nie są wyświetlane zmiany w kodzie zewnętrznej jednostki do momentu Odbuduj projekt dla tej jednostki.

## <a name="class-diagram-workflow"></a>Klasa diagram przepływu pracy

Diagramy klas mogą pomóc zrozumieć struktura klas projektów. Te projekty mogą tworzone przez innych lub wystarczy odświeżacz utworzony przez siebie projektu. Diagramy klas umożliwia dostosowywanie, udostępniania i prezentować informacje o projekcie z innymi osobami.

Pierwszym etapem prezentować informacje o projekcie ma utworzenia diagramu klas, który wyświetla mają być wyświetlane. Aby uzyskać więcej informacji, zobacz [dodać diagramu klas](how-to-add-class-diagrams-to-projects.md). Możesz utworzyć wiele diagramów klasy dla projektu, który może służyć do wyświetlania różnych widok projektu, podzbiór wybranych typów projektów lub wybrany podzestaw elementów członkowskich typów.

Oprócz Definiowanie Pokazuje każdy diagram klas, możesz również zmienić sposób, że informacje są prezentowane; Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie diagramów klasy](how-to-customize-class-diagrams.md).

Po ma dopracowaniu jeden lub więcej diagramów klasy, możesz skopiować je do dokumentów Microsoft Office i je wydrukować lub wyeksportować je jako pliki obrazów. Aby uzyskać więcej informacji, zobacz [porady: kopiowanie elementów diagramu klasy do dokumentu pakietu Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [porady: drukowanie diagramów klasy](how-to-print-class-diagrams.md) i [porady: eksportowanie diagramów klasy jako obrazów](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Projektant klas nie śledzi lokalizację plików źródłowych, więc zmiany struktury projektu lub przenoszenie plików źródłowych w projekcie może spowodować Projektant klas utratę informacji o tego typu, szczególnie typ źródła jako element typedef, klas podstawowych lub typu powiązania. Może być wyświetlany komunikat o błędzie, takich jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij kod źródłowy zmodyfikowany lub przeniesiono do diagramu klas, aby ją wyświetlić go ponownie.

## <a name="see-also"></a>Zobacz także

- [Funkcje Edytor kodu](../writing-code-in-the-code-and-text-editor.md)
- [Zależności mapy w ramach rozwiązań](../../modeling/map-dependencies-across-your-solutions.md)