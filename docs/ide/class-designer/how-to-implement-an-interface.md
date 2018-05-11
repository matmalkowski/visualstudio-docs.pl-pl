---
title: 'Porady: implementowanie interfejsu (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8905fe471d022ff7772ded2e5e3e571b1b74968
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Porady: Implementowanie interfejsu w Projektancie klas

W **Projektant klas**, można zaimplementować interfejsu na diagramie klas, łącząc go z klasy, która udostępnia kod dla metody interfejsu. **Projektant klas** generuje implementacji interfejsu i relacji między interfejs i klasa będzie wyświetlany jako relację dziedziczenia. Można zaimplementować interfejs, za pomocą rysowania linii dziedziczenia między interfejs i klasy lub przeciągając je z widoku klasy interfejsu.

> [!TIP]
> Można utworzyć ten sam sposób utworzyć innych typów interfejsów. Jeśli interfejs istnieje, ale nie są wyświetlane na diagramie klas, następnie najpierw go wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md) i [porady: wyświetlanie istniejących typów](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs za pomocą rysowania linii dziedziczenia

1.  Na diagramie klas wyświetlić interfejs i klasy, która będzie implementowany interfejs.

2.  Rysowanie linii dziedziczenia z klasy i interfejsu.

     Jest wyświetlany lizak dołączonego do klasy, a etykieta o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje klas zastępczych dla wszystkich członków interfejsu.

Aby uzyskać więcej informacji, zobacz [porady: Tworzenie dziedziczenia pomiędzy typami](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejsu z okno widoku klas

1.  Na diagramie klas wyświetlanie klasy, która ma zostać zaimplementowany interfejs.

2.  Otwórz **widoku klasy** i Znajdź interfejsu.

    > [!TIP]
    > Jeśli **widoku klasy** nie jest otwarte, otwórz **widoku klasy** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Shift** + **C**.

3.  Przeciągnij węzeł interfejsu klasy kształt na diagramie.

     Jest wyświetlany lizak dołączonego do klasy, a etykieta o nazwie interfejsu identyfikuje relacji dziedziczenia. Visual Studio generuje klas zastępczych dla wszystkich członków interfejsu; w tym momencie zaimplementowano interfejs.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie typów za pomocą Projektanta klas](how-to-create-types.md)
- [Porady: wyświetlanie istniejących typów](how-to-view-existing-types.md)
- [Porady: Tworzenie dziedziczenia pomiędzy typami](how-to-create-inheritance-between-types.md)
- [Refaktoryzacja klas i typów](refactoring-classes-and-types.md)