---
title: 'Porady: Tworzenie skojarzenia między typami (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b27530abeec1c01b5537fd91bfbe3e0e10448af
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958558"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Porady: Tworzenie skojarzenia między typami w Projektancie klas

Skojarzenie linii w **Projektant klas** Pokaż w jaki sposób są powiązane klasy na diagramie. Linia skojarzenia reprezentuje klasę, która jest typem właściwości lub polem innej klasy w projekcie. Linii skojarzeń zwykle używa się do ilustrowania najważniejszych relacji między klasami w projekcie.

Podczas gdy można wyświetlić wszystkie pola i właściwości jako skojarzenia, więcej sensu ma wyświetlanie tylko ważnych elementów członkowskich jako skojarzeń, w zależności od tego, co zamierzasz podkreślić na diagramie. (Można wyświetlić mniej ważne elementy członkowskie jako zwykłe elementy członkowskie lub je całkowicie ukryć.)

> [!NOTE]
> **Projektant klas** obsługuje tylko jednokierunkowe skojarzenia.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Aby zdefiniować linię skojarzenia na Diagramie klasy

1. W przyborniku w obszarze **Projektant klas**, wybierz pozycję **skojarzenia**.

2. Narysuj linię między dwoma kształtami, które chcesz połączyć przez skojarzenie.

     Nowa właściwość jest tworzona w pierwszej klasie. Ta właściwość służy jako linia skojarzenia, (a nie jako właściwość w ramach przedziału w kształcie) z domyślną nazwą. Jej typ to kształt, na który wskazuje linia skojarzenia.

## <a name="to-change-the-name-of-an-association"></a>Aby zmienić nazwę skojarzenia

Na powierzchni diagramu kliknij etykietę linii skojarzenia i ją wyedytuj.

Alternatywnie wykonaj następujące kroki:

1. Wybierz kształt, który zawiera właściwość, która jest wyświetlana jako skojarzenie.

   Kształt uzyskuje fokus i wyświetlić jej elementów członkowskich w **szczegółów klasy** i **właściwości** systemu windows.

2. W jednym **szczegółów klasy** lub **właściwości** okna, Edytuj pola nazwy dla tej właściwości i naciśnij klawisz **Enter**.

   Nazwa jest aktualizowana w **szczegółów klasy** okna na skojarzenie wiersz w **właściwości** okna, a w kodzie.

## <a name="see-also"></a>Zobacz także

- [Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji](how-to-change-between-member-notation-and-association-notation.md)
