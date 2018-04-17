---
title: Generowanie zastąpienie metody w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e5900872ab034daa24a28b8b97d96bbb736ae6e3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
