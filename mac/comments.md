---
title: Komentarze
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 0d49896a3c265dfdc5a25c46e80de498adfffb07
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
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
