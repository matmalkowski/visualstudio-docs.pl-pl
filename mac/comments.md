---
title: Komentarze
description: W tym artykule opisano przy użyciu komentarzy w edytorze źródła programu Visual Studio dla komputerów Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 4a7dfd0daaddad9f91d461689a0174469dd253c2
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33865390"
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
