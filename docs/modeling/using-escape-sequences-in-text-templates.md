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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b8e92a4bbd149d96b6db710daf32dc72024d57da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950390"
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