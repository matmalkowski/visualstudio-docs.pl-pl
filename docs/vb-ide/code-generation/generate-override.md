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
ms.openlocfilehash: e8a7658ff8e2f573f2da6ff3197b6a11f3b3a0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-visual-basic"></a>Generowanie zastąpienia w języku Visual Basic
**Co:** umożliwia natychmiast generowania kodu dla dowolnej metody, która może zostać zastąpiona po klasie podstawowej. 

**Kiedy:** chcesz zastąpić metodę klasy podstawowej i automatycznie generowania podpisu.  

**Dlaczego:** można napisać podpis metody samodzielnie, jednak ta funkcja zostanie automatycznie generowania podpisu. 

**Jak:**

1. Typ **zastępuje** — słowo kluczowe, spację, którym chcesz wstawić podpis przesłoniętej metody i pojawi się lista rozwijana IntelliSense.

   ![Zastąpienie IntelliSense](media/override_intellisense.png)

1. Wybierz metodę, aby przesłonić od klasy podstawowej, klikając go za pomocą myszy lub przejdź do niego przy użyciu klawiatury i naciskając klawisz **Enter**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. Wybrana metoda lub właściwość zostanie dodany do klasy jako przesłonięcie, gotowy do zaimplementowania.

   ![Zastąpienie wyników](media/override_result.png)

## <a name="see-also"></a>Zobacz też  
[Generowanie kodu (Visual Basic)](../code-generation-vb.md) 