---
title: Komentarze
description: W tym artykule opisano, za pomocą komentarzy w edytorze źródła programu Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 28c02f7f6347da67133a82c1d0aa71d44a4309d2
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42624015"
---
# <a name="comments"></a>Komentarze

W przypadku debugowania lub eksperymentowania z kodem, może być przydatne dodać komentarz bloki kodu albo tymczasowo lub długoterminowych. 

Aby przekształcić w komentarz cały blok kodu:

* Wybierz numer kierunkowy, a następnie wybierz pozycję **Przełącz komentarze do wierszy** z menu kontekstowego

LUB

* Użyj `cmd + /` powiązanie klawiszy w zaznaczonym kodzie.

Metody te można dodać komentarz, a następnie usuń komentarz z fragmentów kodu. Pliki C# dodatkowe poziomy wiersz komentarze może być dodana, co pozwala regionów kodów się nadal przy zachowaniu komentarze rzeczywiste komentarzem i pozbawionym znaków komentarza wierszu, podczas: 

 ![Wielopoziomowe komentarze](media/source-editor-image8.png)

Komentarze są także przydatne do dokumentowania kodu przez przyszłych programistów, które mogą korzystać z niego. Są one zazwyczaj wykonywane w formie wielowierszowe komentarze, które są dodawane w następujący sposób w każdym języku:

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
