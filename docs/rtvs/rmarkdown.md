---
title: R Markdown z R Tools for Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: e3d9ee899c9ed82cacfd9466412bacfea6b8c5e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-r-markdown-documents"></a>Tworzenie dokumentów R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) to format dokumentu, który włącza analizę w R do dokumentów wysokiej jakości, raportów, prezentacji i pulpitów nawigacyjnych.

R narzędzi dla programu Visual Studio (RTVS) zawiera szablon elementu R Markdown, Edytor pomocy (takie jak IntelliSense dla kodu języka R w edytorze) i możliwości generowania pliku.

Używanie języka znaczników Markdown R:

1. Zamknij program Visual Studio.
1. (Tylko jeden raz) Zainstaluj `pandoc` z [pandoc.org](http://pandoc.org/installing.html).
1. Uruchom ponownie program Visual Studio, który należy pobrać instalacji pandoc.
1. Zainstaluj `knitr` i `rmarkdown` pakiety, które można wykonać z [okna interaktywnego](interactive-repl.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Tworzenie nowego pliku R Markdown za pomocą **Plik > Nowy** polecenia menu i wybierając **R Markdown** z listy lub klikając prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierając **dodać R Markdown** (lub **Dodaj > Nowy element...**  i wybierając **R Markdown** z listy).

1. Domyślna zawartość nowego pliku są następujące:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---
    
    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.
    
    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
    
    ```{r}
    summary(cars)
    ```
    
    You can also embed plots, for example:
    
    ```{r, echo=FALSE}
    plot(cars)
    ```
    
    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
    
    ~~~

1. W dowolnym czasie podczas edytowania, kliknij prawym przyciskiem myszy w edytorze i wybierz **Podgląd**, która zawiera opcje HTML, plików PDF oraz program Microsoft Word. W tej wersji zapoznawczej można zapisać pliku jako odpowiednie dla wybranej formatu.
