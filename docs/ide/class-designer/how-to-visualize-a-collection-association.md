---
title: 'Porady: wizualizacja skojarzeń kolekcji (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24dc8b21fbdacb5da2795b215cd8503b08cf3449
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Porady: wizualizacja skojarzeń kolekcji w Projektancie klas

Właściwości i pola, które są kolekcjami innych typów mogą być wyświetlane na diagramie klas jako kolekcję skojarzeń. W odróżnieniu od skojarzenie regularne Wyświetla pole lub właściwość jako wiersz łączenie klasa będąca właścicielem z typem pola, skojarzeń kolekcji jest wyświetlany jako wiersz łączenia klasa będąca właścicielem typu modułu zbierającego.

## <a name="to-create-a-collection-association"></a>Aby utworzyć skojarzenie kolekcji

1.  W kodzie należy utworzyć właściwości lub pola, którego typ jest kolekcją jednoznacznie.

2.  Na diagramie klas rozwiń klasy tak, aby właściwości i pola.

3.  W klasie, kliknij prawym przyciskiem myszy pole lub właściwość, a następnie wybierz pozycję **wyświetlić jako kolekcję skojarzeń**.

Właściwość lub pole jest wyświetlany jako linia asocjacji połączenie typu modułu zbierającego.

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie skojarzenia między typami](how-to-create-associations-between-types.md)
- [Projektowanie klas i typów](designing-and-viewing-classes-and-types.md)
- [Wyświetlanie typów i relacji](viewing-types-and-relationships.md)
