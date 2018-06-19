---
title: Raport dotyczący znaczników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b46cb18e1972d22010ce356f1d9208f391f6d79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31580411"
---
# <a name="markers-report"></a>Raport dotyczący znaczników
Raport dotyczący znaczników wymieniono znaczników w wyświetlany przedział czasu.  Przesuwanie powiększanie lub ukrywanie pasm, może spowodować znaczników lub pojawiania się. Raport zawiera informacje o poszczególnych znaczników:  
  
-   Czas, gdy rozpoczęto, względem początku śledzenia.  
  
-   Jego czas trwania. Czas trwania wynosi zero dla flagi i komunikaty, ponieważ stanowią one natychmiastowe.  
  
-   Identyfikator wątku, który wygenerował go.  
  
-   Dostawca zdarzenia śledzenia zdarzeń systemu Windows (ETW), która go wygenerowała.  
  
-   Seria znacznika, w którym został zapisany.  
  
-   Kategoria zdarzenia, które należy do.  
  
-   Jej poziom ważności.  
  
-   Jego typ (zakres, Flaga lub komunikat).  
  
-   Opis wysokiego poziomu co reprezentuje  
  
 Wybierz **wyeksportować** przycisk, aby zapisać raport dotyczący znaczników do pliku CSV. Dane można użyć w pliku CSV z innych aplikacji lub narzędzi.  
  
> [!NOTE]
>  Raport dotyczący znaczników można wyświetlić 1000 znaczników. Aby wyświetlić wszystkie znaczniki, należy wyeksportować pełny raport do pliku CSV.