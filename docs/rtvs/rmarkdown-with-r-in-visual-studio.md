---
title: R Markdown z R Tools for Visual Studio | Dokumentacja firmy Microsoft
description: "Jak utworzyć R Markdown dokumenty w Visual Studio do tworzenia wysokiej jakości raportów, prezentacji i pulpitów nawigacyjnych."
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 982dc9a2fbcb8e6cb790ec64c07d83f02017c803
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="creating-r-markdown-documents"></a>Tworzenie dokumentów R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) to format dokumentu, który włącza analizę w R do dokumentów wysokiej jakości, raportów, prezentacji i pulpitów nawigacyjnych.

R narzędzi dla programu Visual Studio (RTVS) zawiera szablon elementu R Markdown, Edytor obsługuje (w tym IntelliSense dla kodu języka R w edytorze), możliwości generowania pliku i na żywo w wersji zapoznawczej.

## <a name="using-r-markdown"></a>Przy użyciu języka znaczników Markdown R

1. Zamknij program Visual Studio.
1. (Tylko jeden raz) Zainstaluj `pandoc` z [pandoc.org](http://pandoc.org/installing.html).
1. Uruchom ponownie program Visual Studio, który należy pobrać instalacji pandoc.
1. Zainstaluj `knitr` i `rmarkdown` pakiety, które można wykonać z [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Tworzenie nowego pliku R Markdown, przy użyciu **Plik > Nowy > plik** polecenia menu i wybierając **R > R Markdown** z listy. W kontekście projektu, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz **dodać Markdown R** (lub **Dodaj > Nowy element...**  i wybierając **R Markdown** z listy).

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

## <a name="previews"></a>Wersje zapoznawcze

Visual Studio 2017 wersji 15.5 i nowszych automatycznie udostępnić na żywo Podgląd R Markdown. Aby włączyć funkcję automatycznej synchronizacji między edytorze i podglądu, wybierz **narzędzia R > Markdown > synchronizacji automatycznej** (Ctrl + Shift + Y). Jeśli nie używasz synchronizacji, można odświeżyć przy użyciu podglądu **narzędzia R > Markdown > Podgląd Markdown R Załaduj ponownie**.

Można również wyświetlić podgląd pliku w formacie HTML, PDF, i Microsoft Word formatuje prawym przyciskiem myszy w edytorze i wybierając jedną z **Podgląd** poleceń. Te same polecenia są również dostępne na **narzędzia R > Markdown** menu. (W starszych wersjach programu Visual Studio te polecenia znajdują się na **narzędzia R > Publikuj** menu.)

![Podgląd aktywny RMarkdown i innych poleceń menu podglądu](media/rmarkdown-live-preview.png)
