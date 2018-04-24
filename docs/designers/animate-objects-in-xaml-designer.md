---
title: Animowanie obiektów w projektancie XAML
ms.date: 04/11/2018
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 46b08815a320faf7043d860b4cd96f4120409854
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML

Można utworzyć krótkiej animacji, które przenoszenie obiektów lub stopniowe je i wylogowanie.

Aby rozpocząć, Utwórz *scenorysu*. Scenorysu zawiera jeden lub więcej *osi czasu*. Ustaw *klatki* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji Blend interpolacji zmiany właściwości w wyznaczonym okresie czasu. Wynik jest przejścia. Można animować dowolnej właściwości, która należy do obiektu, nawet właściwości niewidoczne.

Na poniższej ilustracji przedstawiono scenorysu o nazwie **MoveUp**. Oś czasu zawiera klatek, który oznacza pozycję X i Y prostokąta. Po uruchomieniu tego animacji prostokąt są przenoszone z jednego miejsca na inny sprawnie.

![MoveUp scenorysu w Projektancie XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)