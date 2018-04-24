---
title: Wstawki kodu dla języka R
description: Wstawki kodu dla języka R w programie Visual Studio Podaj skróty do szybkiego wstawiania bloki kodu o dowolnej długości pomaga uniknąć samodzielnego przepisywania podobny kod.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 0ce8e2ea6ec0cb0d2d70cfab36687f108dd73e82
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="code-snippets"></a>Wstawki kodu

Wstawki kodu programu Visual Studio Podaj skróty do szybkiego wstawiania bloki kodu o dowolnej długości pomaga uniknąć samodzielnego przepisywania podobny kod. R narzędzi dla programu Visual Studio (RTVS) Dodaj dziesiątki fragmentów R przydatne do kolekcji programu Visual Studio.

Aby wstawić fragment, typ skróconą nazwę fragment kodu (IntelliSense pod warunkiem), naciśnij klawisz Tab, aby wstawić.

Proste przykłady:

- Typ `=` następnie karcie i RTVS powiększa go do `<-` operator przypisania.
- Typ `>` następnie karcie i RTVS rozszerza on `%>%` operator potoku.

Wstawki kodu programu może być znacznie więcej niż tylko znak zakończenia znaków. Fragment do odczytywania z pliku CSV `read.csv` funkcji, na przykład można zwalnia Cię z trzeba pamiętać nazwy i parametry:

![Animacja Wstawianie wywołania do read.csv przy użyciu wstawek kodu](media/code-snippet-expansion.gif)

W takim przypadku podczas wpisywania `readc`, IntelliSense wyświetla listę uzupełniania. Wybranie tego zakończenia w listy rozwijanej, a naciśnięcie wybiera kartę `readc`, a naciśnięcie klawisza Tab ponownie rozszerza fragment kodu. (Dlatego rozszerzenia fragment jest często traktować jako "typ fragment kodu i naciśnij dwa razy klawisz TAB"). W większości przypadków pierwszej karcie kończy wybór IntelliSense i drugą kartę wyzwala rozszerzenia.

Aby wyświetlić wszystkie dostępne fragmenty kodu, otwórz **Narzędzia > Menedżerze fragmentów kodu...**  okno dialogowe (Ctrl + K, B) i wybierz **R** dla **języka**. Rozwiń grupy i wybrać poszczególne fragmenty kodu, opis i skrót:

![Okno dialogowe wstawki kodu dla języka R](media/code-snippet-dialog.png)

Aby utworzyć wstawki kodu niestandardowego, wykonując instrukcje wyświetlone na [wskazówki: tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md). Ostatecznie fragment kodu jest tylko plik XML. Na przykład następujący kod to fragment kodu dla tej operacji potoku (skrót `>`):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Pliki XML wszystkie fragmenty kodu są instalowane z RTVS; **lokalizacji** w **Menedżerze fragmentów kodu** Określa ścieżkę. Można również znaleźć w kodzie źródłowym RTVS w witrynie GitHub pod [src/pakietu/Impl/wstawki](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
