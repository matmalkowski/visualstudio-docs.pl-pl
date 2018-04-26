---
title: 'Porady: należy użyć funkcji wyszukiwania w Projektancie przepływów pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4b5dfdd4b4d05969406f93801bcf87880949e41a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Porady: należy użyć funkcji wyszukiwania w Projektancie przepływów pracy

W celu ułatwienia tworzenia większych i bardziej skomplikowanych przepływów pracy, wyszukiwania można w Projektancie przepływów pracy można znaleźć elementów według słów kluczowych. Należy pamiętać, że projektant nie obsługuje Zamień. Wyszukiwanie znajdziesz następujące w Projektancie:

## <a name="quick-find"></a>Szybkie wyszukiwanie

Szybkie find znajduje następujące w Projektancie:

-   Właściwości <xref:System.Activities.Activity> obiektów, <xref:System.Activities.Statements.FlowNode> obiektów, <xref:System.Activities.Statements.State> obiektów, przejścia i inne elementy niestandardowe sterowanie przepływem.

-   Zmienne

-   Argumenty

-   Wyrażenia

### <a name="using-quick-find"></a>Używanie szybkiego wyszukiwania

1.  Otwórz projektanta przepływów pracy naciśnij **Ctrl + F**, lub wybierz **Edytuj**, **Znajdź i Zamień**, **szybkiego wyszukiwania**.

2.  Wprowadź wyszukiwany termin do **Znajdź** pole tekstowe i kliknij przycisk **Znajdź następny**.

3.  Wyszukiwany termin będą znajdować się w bieżącym przepływu pracy. Poniższy zrzut ekranu przedstawia nazwę wyświetlaną działania znajdujących się w projektancie.

     ![Wyniki wyszukiwania w Projektancie przepływów pracy](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Znajdź w plikach

Używanie wyszukiwania w plikach zlokalizuje ciągów w pliki przepływu pracy, w tym plików XAML.

### <a name="using-find-in-files"></a>Używanie wyszukiwania w plikach

1.  W programie Visual Studio, naciśnij klawisz **Ctrl + Shift + F**, lub wybierz **Edytuj**, **Znajdź i Zamień**, **Znajdź w plikach**

2.  Wprowadź szukany element do **Znajdź** pole tekstowe i kliknij przycisk **Znajdź wszystkie**

3.  Wyniki wyszukiwania będą wyświetlane w programie Visual Studio**Znajdź wynik** widoku. Dwukrotne kliknięcie elementu wynik przejdzie do działania, która zawiera dopasowania w Projektancie przepływów pracy.