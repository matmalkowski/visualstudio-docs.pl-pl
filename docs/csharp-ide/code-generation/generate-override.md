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
ms.openlocfilehash: d2972cfe2ea4481ab8f5eab6284277615d1d64a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-c"></a>Generowanie zastąpienia w języku C# #
**Co:** umożliwia natychmiast generowania kodu dla dowolnej metody, która może zostać zastąpiona po klasie podstawowej. 

**Kiedy:** chcesz zastąpić metodę klasy podstawowej i automatycznie generowania podpisu.  

**Dlaczego:** można napisać podpis metody samodzielnie, jednak ta funkcja zostanie automatycznie generowania podpisu. 

**Jak:**

1. Typ **zastąpienia** — słowo kluczowe, spację, którym chcesz wstawić podpis przesłoniętej metody i pojawi się lista rozwijana IntelliSense.

   ![Zastąpienie IntelliSense](media/override_intellisense.png)

1. Wybierz metodę, aby przesłonić od klasy podstawowej, klikając go za pomocą myszy lub przejdź do niego przy użyciu klawiatury i naciskając klawisz **Enter**.

   >[!TIP]
   >* Użyj ikony właściwości ![Ikona właściwości](media/override_property.png) Aby wyświetlić lub ukryć właściwości na liście.
   >* Użyj ikony — metoda ![Ikona właściwości](media/override_method.png) Aby wyświetlić lub ukryć metod na liście.

1. Wybrana metoda lub właściwość zostanie dodany do klasy jako przesłonięcie, gotowy do zaimplementowania.

   ![Zastąpienie wyników](media/override_result.png)

## <a name="see-also"></a>Zobacz też  
[Generowanie kodu (C#)](../code-generation-csharp.md)  
