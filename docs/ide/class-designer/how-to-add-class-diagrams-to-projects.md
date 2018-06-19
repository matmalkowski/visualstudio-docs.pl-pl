---
title: 'Porady: dodawanie diagramów klasy do projektu (Projektant klas)'
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94e13d4c1dbda200c2e2660e4b3b44e62ed99496
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33998192"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Porady: Dodawanie diagramów klasy do projektów

Aby projektowanie, edytowanie i Refaktoryzuj klasami i innymi typami, należy dodać diagram klas do projektu C#, VB lub C++. Do wizualizacji różnych części kodu w projekcie, należy dodać wiele diagramów klas do projektu.

Diagramy klas nie można utworzyć z projektów, które mają kod wielu aplikacjom. Aby utworzyć diagramów klas UML, zobacz [UML tworzenie projektów i diagramów modelowania](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="install-the-class-designer-component"></a>Zainstaluj składnik projektanta klas

Jeśli używasz programu Visual Studio 2017 i nie zostały zainstalowane **Projektant klas** składnika, wykonaj następujące kroki, aby go zainstalować.

1. Otwórz **Instalator programu Visual Studio** z menu Start systemu Windows lub wybierając **narzędzia** > **Pobierz narzędzia i funkcje** na pasku menu programu Visual Studio.

   **Instalator programu Visual Studio** otwiera.

1. Wybierz **pojedynczych składników** , a następnie przewiń w dół do **kodu narzędzia** kategorii.

1. Wybierz **Projektant klas** , a następnie wybierz **Modyfikuj**.

   ![Klasy składnika projektanta w Instalator programu Visual Studio](media/class-designer-component.png)

   **Projektant klas** składnika rozpoczyna instalowanie.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Dodaj pusty diagram klas do projektu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. Możesz również nacisnąć klawisz **Ctrl**+**Shift**+**A**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

2. Rozwiń węzeł **wspólne elementy** > **ogólne**, a następnie wybierz **diagramu klas** z listy szablonów. Projekty Visual C++, można znaleźć w **narzędzie** kategorię, aby znaleźć **diagramu klas** szablonu.

   > [!NOTE]
   > Jeśli nie widzisz **diagramu klas** szablonu, [wykonaj kroki](#install-the-class-designer-component) do zainstalowania **Projektant klas** składnika programu Visual Studio.

   Diagram klas zostanie otwarty w Projektancie klas i będzie wyświetlany jako plik, który ma *.cd* rozszerzenia **Eksploratora rozwiązań**. Możesz przeciągać kształty i wiersze do diagramu z **przybornika**.

Aby dodać wiele diagramów klas, powtórz czynności opisane w tej procedurze.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Dodaj do diagramu klas na podstawie istniejących typów

W **Eksploratora rozwiązań**, otwórz menu kontekstowego plików klasy, a następnie wybierz pozycję **widoku diagramu klas**.

—lub—

W **widoku klasy**, otwórz menu kontekstowe przestrzeń nazw lub typ, a następnie wybierz pozycję **widoku diagramu klas**.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Aby wyświetlić zawartość kompletnego projektu na diagramie klas

W **Eksploratora rozwiązań** lub klasy widok, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **widoku**, a następnie wybierz **widoku diagramu klas**.

Utworzono diagramu klas wypełnione automatycznie.

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md)
- [Porady: wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Projektowanie i widoku klas i typów](designing-and-viewing-classes-and-types.md)
- [Wyświetlanie typów i relacji](viewing-types-and-relationships.md)
- [Praca z diagramami klas](working-with-class-diagrams.md)
