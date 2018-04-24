---
title: Korzystanie z sekwencji unikowych w szablonach tekstowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ef3cb58c9352e81fc959dfdd2ddebd354e834fbf
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="using-escape-sequences-in-text-templates"></a>Korzystanie z sekwencji unikowych w szablonach tekstowych
Można użyć sekwencji unikowych w szablonach tekstowych, które mają być Generowanie tagi szablonu tekstu i (C# jedynie w kodzie) specjalne znaków kontrolnych i cudzysłowów.

 Aby wydrukować otwierających i zamykających znaczników dla bloków kodu standardowa do pliku wyjściowego, escape tagów w następujący sposób:

```
\<# ... \#>
```

 Możesz to zrobić taki sam jak inne tekst dyrektywy i kodu bloku znaczniki szablonu.

 Bloku tekstu zawiera ciągi wykorzystywane w celu uniknięcia znaczniki szablonu tekstu, może używać następujących unikowe:

-   Jeśli tekst tag szablonu jest poprzedzony parzystą liczbą escape (\\) znaków szablonu analizatora będzie połowy znaki specjalne obejmują i Dołącz sekwencję jako tag szablonu tekstu. Na przykład jeśli istnieją cztery znaki specjalne w szablonie tekstu, będą istnieć dwa "\\" znaków w wygenerowanym pliku.

-   Jeśli tekst tag szablonu jest poprzedzony nieparzystą liczbę escape (\\) znaków, analizator szablon będzie zawierać połowy "\\" znaki plus samego tagu (\<# lub #>). Tag nie jest uważany za tag szablonu tekstu.

-   Jeśli escape (\\) pojawi się gdziekolwiek w dowolnej kolejności innej niż gdzie specjalne znaków kontrolnych lub cudzysłowu (w języku C# tylko), znak będą dane wyjściowe bezpośrednio.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)