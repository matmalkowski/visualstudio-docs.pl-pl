---
title: 'Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdb4f28fc367b309a015a3faa8f749e2512db879
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957804"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji w Projektancie klas

W **Projektant klas**, można zmienić sposób diagramu klas reprezentuje relację skojarzenia między dwoma typami z notacją członka skojarzenie notacji i na odwrót. Elementy członkowskie wyświetlane linie asocjacji często stanowi przydatne wizualizację, w jaki sposób są powiązane typy.

> [!NOTE]
> Relacje skojarzenie może być reprezentowana jako element członkowski właściwości lub pola. Aby zmienić skojarzenie notacji notacją członka, jeden typ musi mieć członkiem innego typu. Aby zmienić skojarzenie notacji notacją członka, dwa typy musi być dołączony do linia skojarzenia. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie skojarzenia typów bBetween](how-to-create-associations-between-types.md). Jeśli projekt zawiera wiele diagramów klas, zmiany wprowadzone w sposób diagram przedstawia relacje skojarzenia wpływa na tylko tego diagramu. Aby zmienić sposób innego diagramu zawiera relacje skojarzenia, Otwórz lub wyświetlić ten diagram i wykonaj następujące kroki.

## <a name="to-change-member-notation-to-association-notation"></a>Aby zmienić notacją członka skojarzenie notacji

1.  W węźle projekt w Eksploratorze rozwiązań Otwórz plik diagramu (.cd) klasy.

2.  Typ kształtu na diagramie klas, kliknij prawym przyciskiem myszy element członkowski właściwości lub pola reprezentujący skojarzenie, a następnie wybierz pozycję **Pokaż jako skojarzenie**.

    > [!TIP]
    > Jeśli nie właściwości lub pola są widoczne w kształcie typu, może zostać zwinięty przedziałów w kształcie. Aby rozszerzyć kształtu typu, kliknij dwukrotnie nazwę przedziału lub kształtu typu prawym przyciskiem myszy i wybierz **rozwiń**.

    Element członkowski zniknie z przedziału kształtu typu i linia asocjacji wydaje się połączyć z dwóch typów. Linia asocjacji jest oznaczony nazwę właściwości lub pola.

## <a name="to-change-association-notation-to-member-notation"></a>Aby zmienić skojarzenie notacji Notacja członka

Na diagramie klas, kliknij prawym przyciskiem myszy linię skojarzenia, a następnie wybierz pozycję **Pokaż jako właściwość** lub **Pokaż jako pole** odpowiednio. Linia asocjacji znika, a właściwość wyświetla w odpowiedni przedział w jego typ kształtu na diagramie.

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie dziedziczenia pomiędzy typami](how-to-create-inheritance-between-types.md)
- [Porady: wyświetlanie dziedziczenia pomiędzy typami](how-to-view-inheritance-between-types.md)
- [Wyświetlanie typów i relacji](viewing-types-and-relationships.md)
- [Porady: wizualizacja skojarzeń kolekcji](how-to-visualize-a-collection-association.md)