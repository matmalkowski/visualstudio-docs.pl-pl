---
title: 'Porady: wyświetlanie dziedziczenia pomiędzy typami (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8f44279baea33333c21bfadfd9fec21a2045aea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-view-inheritance-between-types-class-designer"></a>Porady: wyświetlanie dziedziczenia pomiędzy typami (Projektant klas)

Można znaleźć relacji dziedziczenia, jeśli istnieje, między typem bazowym i jego typów pochodnych na diagramie klas w **Projektant klas**. Aby utworzyć relację dziedziczenia, jeśli żadnego nie ma, między dwoma typami, zobacz [porady: Tworzenie dziedziczenia pomiędzy typami](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Aby znaleźć typu podstawowego

1.  Na diagramie klas kliknij typ, dla którego chcesz wyświetlić klasy podstawowej lub interfejsu.

2.  Na **diagramu klas** menu, wybierz **Pokaż klasa podstawowa** lub **Pokaż interfejsy Base**.

     Typ klasy podstawowej lub interfejsu widoczny jako zaznaczony na diagramie. Wszystkie wiersze ukryte dziedziczenia pojawią się między dwoma kształtów.

Można również przyciskiem myszy typ, którego typ podstawowy, które chcesz wyświetlić, a następnie wybierz pozycję **Pokaż klasy podstawowej** lub **Pokaż interfejsach podstawowych**.

## <a name="to-find-the-derived-types"></a>Aby znaleźć typy pochodne

1.  Na diagramie klas kliknij typ, dla którego chcesz wyświetlić interfejsów lub klas pochodnych.

2.  Na **diagramu klas** menu, wybierz **Pokaż klas pochodnych** lub **Pokaż interfejsy pochodnych**.

     Klasy pochodne typu lub interfejsy są wyświetlane na diagramie. Wszystkie wiersze ukryte dziedziczenia pojawią się między kształtami.

Również kliknięciu prawym przyciskiem myszy typ, dla którego chcesz wyświetlić jego typów pochodnych, a następnie wybierz **Pokaż klas pochodnych** lub **Pokaż interfejsy pochodnych**.

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie skojarzenia między typami](how-to-create-associations-between-types.md)
- [Wyświetlanie typów i relacji](viewing-types-and-relationships.md)