---
title: "Generowanie zastąpienia - generowania kodu (Visual Basic) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="generate-an-override-in-visual-basic"></a>Generowanie zastąpienia w języku Visual Basic
**Co:** umożliwia natychmiast generowania kodu dla dowolnej metody, która może zostać zastąpiona po klasie podstawowej. 

**Kiedy:** chcesz zastąpić metodę klasy podstawowej i automatycznie generowania podpisu.  

**Dlaczego:** można napisać podpis metody samodzielnie, jednak ta funkcja zostanie automatycznie generowania podpisu. 

**Jak:**

1. Typ **zastępuje** — słowo kluczowe, spację, którym chcesz wstawić podpis przesłoniętej metody i pojawi się lista rozwijana IntelliSense.

   ![Zastąpienie IntelliSense](media/override-intellisense-vb.png)

1. Wybierz metodę, aby przesłonić od klasy podstawowej, klikając go za pomocą myszy lub przejdź do niego przy użyciu klawiatury i naciskając klawisz **Enter**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. Wybrana metoda lub właściwość zostanie dodany do klasy jako przesłonięcie, gotowy do zaimplementowania.

   ![Zastąpienie wyników](media/override-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md) 