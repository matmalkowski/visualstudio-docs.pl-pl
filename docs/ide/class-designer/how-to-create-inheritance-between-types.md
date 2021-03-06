---
title: 'Porady: Tworzenie dziedziczenia pomiędzy typami (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8151020294f4fd5574a1de886509c5b11f0a326
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956682"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Porady: Tworzenie dziedziczenia pomiędzy typami w Projektancie klas

Aby utworzyć relację dziedziczenia między dwoma typami na diagramie klasy przy użyciu **Projektant klas**, Uzyskuj dostęp do typu podstawowego jego pochodny typ lub typy. Może mieć relację dziedziczenia między dwiema klasami, między klasą a interfejsem lub między dwa interfejsy.

## <a name="to-create-an-inheritance-between-types"></a>Aby utworzyć dziedziczenia pomiędzy typami

1.  Z projektu w **Eksploratora rozwiązań**, otwórz plik diagramu (.cd) klasy.

     Jeśli nie masz diagramu klas, należy go utworzyć. Zobacz [porady: Dodawanie diagramów klasy do projektów](how-to-add-class-diagrams-to-projects.md).

2.  W **przybornika**w obszarze **Projektant klas**, kliknij przycisk **dziedziczenia**.

3.  Na diagramie klas Rysowanie linii dziedziczenia pomiędzy typami, które mają, zaczynając od:

    -   Klasa pochodna do klasy podstawowej

    -   Klasa implementująca jak zaimplementowany interfejs

    -   Rozszerzanie interfejs do rozszerzonego interfejsu

4.  Opcjonalnie Jeśli typ pochodny od typu ogólnego, kliknij przycisk linii dziedziczenia. W **właściwości** ustaw **argumentów typu** właściwości pasuje do typu, który ma obowiązywać dla typu ogólnego.

    > [!NOTE]
    > Jeśli nadrzędnej klasy abstrakcyjnej zawiera co najmniej jeden abstrakcyjny element członkowski, wszystkie abstrakcyjne elementy członkowskie są zaimplementowane jako dziedziczące klasy nieabstrakcyjnej.
    >
    >  Mimo że można Wizualizuj istniejące typy ogólne, nie można utworzyć nowych typów ogólnych. Nie można zmienić również parametry typu dla istniejących typów ogólnych.

## <a name="see-also"></a>Zobacz także

- [Dziedziczenie](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Podstawowe informacje o dziedziczeniu](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Porady: wyświetlanie dziedziczenia pomiędzy typami](how-to-view-inheritance-between-types.md)
- [Klasy Visual C++ w Projektancie klas](visual-cpp-classes.md)