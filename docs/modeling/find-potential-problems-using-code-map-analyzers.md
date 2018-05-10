---
title: Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e300603280b6c0b57d7397699786f2d3c6ff8317
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu

Uruchom analizatorów na map kodu do określania kodu, który może być zbyt skomplikowane lub które mogą wymagać poprawy jakości. Na przykład można użyć tych analizatorów:

|**Aby znaleźć kod, który ma**|**Sprawdź tych obszarów, aby sprawdzić, czy**|
|-------------------------------|--------------------------------------------|
|Pętle lub zależności cykliczne|Możesz uprościć i należy wziąć pod uwagę, czy można przerwać te cykle.|
|Zbyt wiele zależności|Działają one zbyt wiele funkcji lub w celu określenia wpływu zmiany tych obszarów. Mapy kodu poprawnie sformułowanym wyświetli minimalnej liczbie zależności. Aby ułatwić kodu Obsługa, zmienić, przetestować i ponownie wykorzystać, należy wziąć pod uwagę czy Refaktoryzuj tych obszarów, aby dokładniej zdefiniowano lub czy można scalać kodu, który wykonuje podobne funkcje.|
|Brak zależności|Ich użycie jest konieczne, lub czy należy usunąć ten kod.|

## <a name="analyze-code-maps"></a>Analizowanie mapy kodu

Na pasku narzędzi mapy, wybierz **układu** > **analizatorów**, a następnie analizatora, które chcesz uruchomić:

|**Analyzer**|**Aby zidentyfikować węzłów który**|
|------------------|--------------------------------|
|**Analizator odwołania cykliczne**|Zależności cyklicznych są od siebie wzajemnie. **Uwaga:** zależności cykliczne, które znajdują się w **ogólne** grupy nie są wyświetlane na mapie, gdy rozwiń grupę.|
|**Znajdź analizatora koncentratory**|Znajdują się w górnej 25% węzły połączone wysokiej<br /><br /> **Aby ukryć wszystkie węzły na mapie**<br /><br /> -Otwórz menu skrótów mapy, wybierz pozycję **zaawansowane**, **wybierz**, **Ukryj niezaznaczone**.<br />     Mapy ukrywa niezaznaczone węzłów i analizatora identyfikuje nowe węzły jako koncentratorów.|
|**Analizator węzłów bez odwołań**|Nie masz odwołania z innych węzłów. **Uwaga:** Sprawdź każdy z tych przypadkach przed przy założeniu, że kod nie jest używany. Niektórych zależności, takich jak zależności XAML i środowiska wykonawczego zależności nie można odnaleźć statycznie w kodzie.|

Analizatorów mapy kodu będzie nadal działać po ich zainstalowaniu. Jeśli zmienisz mapy analizatorów zastosowane zostanie automatycznie ponownie przetworzyć zaktualizowanej mapy. Zatrzymał analizatora na pasku narzędzi mapy, wybierz **układu** > **analizatorów**. Wyłącz wybrane analizatora.

> [!TIP]
> Jeśli masz bardzo dużych mapy uruchamiania analizatora może spowodować wyjątek braku pamięci. Jeśli ten problem wystąpi, Edytuj mapę, aby zmniejszyć jej zakres lub wygenerować mniejszy, a następnie uruchom analizatora.

## <a name="see-also"></a>Zobacz także

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
