---
title: "Generowanie zastąpienia - generowania kodu (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 622c05f51d0dc32739f5d27b75aec31c69ee4d87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="generate-an-override-in-c"></a>Generowanie zastąpienia w języku C# #

**Co:** umożliwia natychmiast generowania kodu dla dowolnej metody, która może być zastąpiona z klasy podstawowej.

**Kiedy:** chcesz zastąpić metodę klasy podstawowej i automatycznie generowania podpisu.

**Dlaczego:** można napisać podpis metody samodzielnie, jednak ta funkcja zostanie automatycznie generowania podpisu.

**Jak:**

1. Typ **zastąpienia** — słowo kluczowe, spację, którym chcesz wstawić podpis przesłoniętej metody i pojawi się lista rozwijana IntelliSense.

   ![Zastąpienie IntelliSense](media/override_intellisense.png)

1. Wybierz metodę, aby przesłonić od klasy podstawowej, klikając go za pomocą myszy lub przejdź do niego przy użyciu klawiatury i naciskając klawisz **Enter**.

   >[!TIP]
   >* Użyj ikony właściwości ![Ikona właściwości](media/override_property.png) Aby wyświetlić lub ukryć właściwości na liście.
   >* Użyj ikony — metoda ![Ikona — Metoda](media/override_method.png) Aby wyświetlić lub ukryć metod na liście.

1. Wybrana metoda lub właściwość zostanie dodany do klasy jako przesłonięcie, gotowy do zaimplementowania.

   ![Zastąpienie wyników](media/override_result.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu (C#)](../code-generation-csharp.md)
