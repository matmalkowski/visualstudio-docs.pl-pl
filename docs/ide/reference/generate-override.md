---
title: "Generowanie zastąpienie metody w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: df0eecdeb2aad15e1da68cef3b125c3c95f57e78
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="generate-an-override-in-visual-studio"></a>Generowanie zastąpienia w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** umożliwia natychmiast generowania kodu dla dowolnej metody, która może być zastąpiona z klasy podstawowej.

**Kiedy:** chcesz zastąpić metodę klasy podstawowej i automatycznie generowania podpisu.

**Dlaczego:** można napisać podpis metody samodzielnie, jednak ta funkcja zostanie automatycznie generowania podpisu.

## <a name="how-to"></a>Porada

1. Typ `override` w języku C# lub `Overrides` w języku Visual Basic, spację, gdzie chcesz wstawić to metoda przesłonięcia.

   - C#:

    ![Zastąpienie IntelliSense C#](media/override-intellisense-cs.png)

   - Visual Basic:

    ![Zastąpienie IntelliSense VB](media/override-intellisense-vb.png)

1. Wybierz metodę, którą chcesz zastąpić od klasy podstawowej.

   > [!TIP]
   > - Użyj ikony właściwości ![Ikona właściwości](media/override-property-cs.png) Aby wyświetlić lub ukryć właściwości na liście.
   > - Użyj ikony — metoda ![Ikona — Metoda](media/override-method-cs.png) Aby wyświetlić lub ukryć metod na liście.

   Wybrana metoda lub właściwość jest dodawana do klasy jako przesłonięcie, gotowy do zaimplementowania.

   - C#:

      ![Zastąpienie wynik C#](media/override-result-cs.png)

   - Visual Basic:

      ![Zastąpienie wynik VB](media/override-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)
