---
title: Komentarze
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: cb44dc755721f6095c9a07ad3e6fec1f6849e149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="comments"></a>Komentarze

Podczas debugowania lub eksperymentowanie z kodem, może być przydatne dodać komentarz bloki kodu albo tymczasowo lub długoterminowych. 

Aby przekształcić w komentarz cały blok kodu:

* Wybierz kod, a następnie wybierz **Przełącz wiersz komentarze** z menu kontekstowego

LUB

* Użyj `cmd + /` keybinding w zaznaczonym kodzie.

Te metody mogą służyć do komentarzy i Usuń komentarz fragmentów kodu. W plikach języka C# mogą być dodawane dodatkowe poziomy wiersz komentarze, co pozwala regionów kody komentarze i uncommented podczas nadal zachowania komentarze rzeczywiste: 

 ![wielopoziomowa komentarzy](media/source-editor-image8.png)

Komentarze są również przydatne w przypadku dokumentowanie kodu dla przyszłych deweloperów, które mogą korzystać z niego. Te zwykle są wykonywane w formie komentarzy wiele wierszy, które są dodawane w następujący sposób w każdym z tych języków:

**C#**

``` cs
/*
 This is a multi-line
 comment in C#
*/
```
**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```
