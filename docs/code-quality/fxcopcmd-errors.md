---
title: Błędy FxCopCmd | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a53f8810331a678cb84958e1a1269767064b478
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="fxcopcmd-tool-errors"></a>Błędy FxCopCmd narzędzia

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

**Błąd analizy** są zwracane do błędy krytyczne. Wskazuje on, że nie można wykonać analizy. W razie potrzeby, kod błędu zawiera także podstawową przyczyną błędu krytycznego. Poniższe warunki generować błędy krytyczne:

- Nie można wykonać analizy ze względu na niewystarczające dane wejściowe.

- Analiza zgłosiła wyjątek, który nie jest obsługiwany przez FxCopCmd.

- Plik projektu nie można odnaleźć lub jest uszkodzony.

- Nie określono opcji output lub nie można zapisać pliku.

> [!NOTE]
> Kod powrotu FxCopCmd **błąd odwołań do zestawów** 0x200 samodzielnie jest ostrzeżenie, a nie błąd. Tego kodu powrotnego wskazuje, że zawierają odwołania pośrednie, ale ten FxCopCmd mógł je obsłużyć. To ostrzeżenie oznacza, że istnieje możliwość, że niektóre wyniki analizy mogą zabezpieczenia mogły zostać naruszone. Traktuj **błąd odwołań do zestawów** jako błąd w połączeniu z innymi kodu powrotnego.

## <a name="see-also"></a>Zobacz także

- [Błędy zgłaszane przez aplikację do analizy kodu](../code-quality/code-analysis-application-errors.md)