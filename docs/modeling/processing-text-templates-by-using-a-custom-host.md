---
title: Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e4546c75f424f5091a22e9acd6cceb72f5d8038c
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567093"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego

*Przekształcenia szablonu tekstu* przetwarzanie trwa *szablon tekstowy* pliku jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. Można wywołać aparat przekształcenia tekstu z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia, lub z samodzielnej aplikacji uruchomionej na komputerze, na którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany. Jednakże, należy podać *hosta szablonów tekstowych*. Ta klasa łączy szablon ze środowiskiem, znajdując zasoby, takie jak zestawy i dołączane pliki, oraz zajmując się obsługą danych wyjściowych i komunikatów o błędach.

> [!TIP]
> Jeśli piszesz pakiet lub rozszerzenie, która jest uruchamiana w ramach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], rozważ użycie usługi szablonów tekstowych zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Nie zaleca się używania przekształceń szablonu tekstu w aplikacjach serwerowych. Zaleca się używanie przekształceń szablonu tekstu tylko w pojedynczych wątkach. Jest to spowodowane tym, że aparat szablonów tekstowych ponownie używa pojedynczego elementu AppDomain do tłumaczenia, skompilowania i wykonania szablonów. Przetłumaczony kod nie jest odporny na wielowątkowość. Aparat jest przeznaczony do przetwarzania plików pojedynczo, ponieważ są one [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu w czasie projektowania.
>
> Dla aplikacji środowiska wykonawczego, należy wziąć pod uwagę przy użyciu szablonów tekstowych wstępnie przetworzony: zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Jeśli aplikacja używa zestawu szablonów, które są ustalane w czasie kompilacji, łatwiej jest używać wstępnie przetworzonych szablonów tekstowych. Można również użyć tego podejścia, jeśli aplikacja jest uruchamiana na komputerze, na którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest zainstalowany. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Wykonywanie szablonu tekstu w aplikacji

Aby wykonać szablon tekstowy, wywołaj metodę ProcessTemplate <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Aplikacja musi znaleźć i dostarczyć szablon oraz musi obsłużyć dane wyjściowe.

 W `host` parametrów, należy podać klasę, która implementuje <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Jest to wywoływane zwrotnie przez aparat.

 Host musi mieć możliwość rejestrowania błędów, rozpoznawania odwołań do zestawu i dołączania plików, podawania domeny aplikacji, w której można wykonać szablon, a także wywoływania odpowiednich procesorów dla każdej dyrektywy.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> jest zdefiniowany w **Microsoft.VisualStudio.TextTemplating.\*. 0 Biblioteka dll**, i <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> jest zdefiniowany w **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0 Biblioteka dll**.

## <a name="in-this-section"></a>W tej sekcji
 [Wskazówki: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md) dowiesz się, jak utworzyć niestandardowego hosta szablonu tekstu, dzięki której poza dostępne funkcje szablonu tekstu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="reference"></a>Tematy pomocy
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>Sekcje pokrewne

- [Proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md) w tym artykule opisano, jak działa Transformacja tekstu i które części można dostosować.
- [Tworzenie procesorów dyrektywy szablonu tekstowego T4 niestandardowe](../modeling/creating-custom-t4-text-template-directive-processors.md) zawiera omówienie tekstu procesorów dyrektyw szablonu.