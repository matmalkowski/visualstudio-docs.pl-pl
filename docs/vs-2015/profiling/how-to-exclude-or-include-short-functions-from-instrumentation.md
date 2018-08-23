---
title: 'Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f02e34e9fdb399aa8078342d3a8441f077a60f66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680530"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Porady: wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: wykluczyć lub uwzględnić krótkich funkcji z Instrumentacji](https://docs.microsoft.com/visualstudio/profiling/how-to-exclude-or-include-short-functions-from-instrumentation).  
  
Domyślnie, narzędzia profilowania wykluczyć *małe funkcje* z Instrumentacji. Małe funkcje są krótkich funkcji, których nie należy wprowadzać wszelkie wywołania funkcji. Te małe funkcje z wyjątkiem zapewnia mniejsze koszty Instrumentacji i w związku z tym zwiększona szybkość instrumentacji. Wyłączenie małych funkcji zmniejsza rozmiar pliku (Vsp) dane profilowania wydajności i czasu, który jest wymagany do analizy. Jeśli małe funkcje zostaną wykluczone, czasu spędzonego w małych funkcji zmniejsza wyłącznych i całkowity czas ich funkcji nadrzędnej. Małe funkcje mogą być wyłączone lub objęte instrumentacji, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji  
  
1.  W **Eksplorator wydajności**, wybierz opcję **sesji wydajności** a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
     **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
2.  W **stron właściwości**, kliknij przycisk **Instrumentacji** właściwości.  
  
3.  Aby wykluczyć krótkich funkcji z Instrumentacji, należy wybrać **wykluczenie krótkich funkcji z Instrumentacji**. To jest ustawienie domyślne.  
  
     —lub—  
  
     Aby dołączyć krótkich funkcji instrumentacji, należy wyczyścić **wykluczenie krótkich funkcji z Instrumentacji**.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)



