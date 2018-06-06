---
title: 'Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c6234db781925e8c0558513cb7e8bc608b5cfea
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814687"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji
Domyślnie wykluczyć narzędzi profilowania *małe funkcje* z Instrumentacji. Małe funkcje są krótkich funkcji, które nie wprowadzaj żadnych wywołania funkcji. Z wyjątkiem tych małe funkcje zapewnia mniejsze koszty Instrumentacji i w związku z tym ulepszone szybkości instrumentacji. Wyłączenie małe funkcje zmniejsza wydajność pliku danych profilowania (. *Vsp*) rozmiaru i czasu, który jest wymagany do analizy. Jeśli małe funkcje zostaną wykluczone, czas, który jest przeznaczony na małe funkcje liczy się od czasu wyłącznego i włącznie z ich funkcji nadrzędnej. Małe funkcje można wykluczyć lub zawarte w Instrumentacji, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji  
  
1.  W **Eksplorator wydajności**, wybierz pozycję **sesji wydajności** , a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
     **Strony właściwości** zostanie wyświetlone okno dialogowe.  
  
2.  W **strony właściwości**, kliknij przycisk **Instrumentacji** właściwości.  
  
3.  Aby wykluczyć krótkich funkcji z Instrumentacji, wybierz **wykluczenie krótkich funkcji z Instrumentacji**. To jest ustawienie domyślne.  
  
     —lub—  
  
     Aby dołączyć krótkich funkcji instrumentacji, wyczyść **wykluczenie krótkich funkcji z Instrumentacji**.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz także  
 [Kontrola zbierania danych](../profiling/controlling-data-collection.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)