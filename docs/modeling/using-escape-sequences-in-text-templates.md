---
title: Korzystanie z sekwencji unikowych w szablonach tekstowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 1806b6aa1b6c6d4ac233e4a9d5785fe903d42221
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 [Instrukcje: Generowanie szablonów z szablonów przy użyciu sekwencji ucieczki](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)