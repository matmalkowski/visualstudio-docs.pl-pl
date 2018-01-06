---
title: "Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1238e092bf1b088ba9ce377aeaf66b1fa953f1bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Porady: wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji
Domyślnie wykluczyć narzędzi profilowania *małe funkcje* z Instrumentacji. Małe funkcje są krótkich funkcji, które nie wprowadzaj żadnych wywołania funkcji. Z wyjątkiem tych małe funkcje zapewnia mniejsze koszty Instrumentacji i w związku z tym ulepszone szybkości instrumentacji. Wyłączenie małe funkcje zmniejsza rozmiar pliku (Vsp) dane profilowania wydajności i czasu, który jest wymagany do analizy. Jeśli małe funkcje zostaną wykluczone, czas, który jest przeznaczony na małe funkcje liczy się od czasu wyłącznego i włącznie z ich funkcji nadrzędnej. Małe funkcje można wykluczyć lub zawarte w Instrumentacji, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji  
  
1.  W **Eksplorator wydajności**, wybierz pozycję **sesji wydajności** , a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
     **Strony właściwości** zostanie wyświetlone okno dialogowe.  
  
2.  W **strony właściwości**, kliknij przycisk **Instrumentacji** właściwości.  
  
3.  Aby wykluczyć krótkich funkcji z Instrumentacji, wybierz **wykluczenie krótkich funkcji z Instrumentacji**. To jest ustawienie domyślne.  
  
     —lub—  
  
     Aby dołączyć krótkich funkcji instrumentacji, wyczyść **wykluczenie krótkich funkcji z Instrumentacji**.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)