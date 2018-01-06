---
title: "Błędy FxCopCmd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: "12"
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 48b082f5b00f260d2f8e2519a4551fab23dc1011
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="fxcopcmd-errors"></a>FxCopCmd — Błędy
Fxcopcmd — nie należy wziąć pod uwagę wszystkie błędy jako krytyczny. Jeśli FxCopCmd informacji wystarczających do wykonania częściowej analizy, wykonuje błędy analizy i raporty, które wystąpiły. Kod błędu, który jest 32-bitową liczbę całkowitą, zawiera bitowe połączenie wartości liczbowe odpowiadające błędy.  
  
 W poniższej tabeli opisano kody błędów zwróconych przez FxCopCmd:  
  
|Błąd|Wartość liczbowa|  
|-----------|-------------------|  
|Bez błędów|0x0|  
|Błąd analizy|0x1|  
|Wyjątki reguł|0x2|  
|Błąd ładowania projektu|0x4|  
|Błąd ładowania zestawu|0x8|  
|Błąd ładowania biblioteki reguły|0x10|  
|Błąd ładowania raportu importu|0x20|  
|Błąd wyjścia|0x40|  
|Błąd przełącznika wiersza polecenia|0x80|  
|Błąd podczas inicjowania|0x100|  
|Błąd odwołania do zestawu|0x200|  
|BuildBreakingMessage|0x400|  
|Nieznany błąd|0x1000000|  
  
 Błędy krytyczne, zwracany jest błąd analizy. Wskazuje on, że nie można wykonać analizy. W razie potrzeby, kod błędu zawiera także podstawową przyczyną błędu krytycznego. Poniższe warunki generować błędy krytyczne:  
  
-   Analiza nie można wykonać spowodowane przez niewystarczające dane wejściowe.  
  
-   Analiza zgłosiła wyjątek, który nie jest obsługiwany przez FxCopCmd.  
  
-   Plik projektu nie można odnaleźć lub jest uszkodzony.  
  
-   Nie określono opcji output lub nie można zapisać pliku.  
  
    > [!NOTE]
    >  FxCopCmd kod powrotu "Odwołań do zestawów błąd" 0x200 samodzielnie jest ostrzeżenie, a nie błąd. Kod powrotu wskazuje znaleziono brakujących odwołań pośrednie, ale że FxCopCmd mógł je obsłużyć. Jest to ostrzeżenie, że istnieje możliwość, że niektóre wyniki analizy mogą zabezpieczenia mogły zostać naruszone. Należy wziąć pod uwagę kod powrotny "Odwołań do zestawów błąd" jako błąd w połączeniu z innymi kodu powrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy zgłaszane przez aplikację do analizy kodu](../code-quality/code-analysis-application-errors.md)