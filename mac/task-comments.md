---
title: "Komentarz do zadań"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="task-comments"></a>Komentarz do zadań

Podczas pisania kodu, jest standardową praktyką jawnie komentarz kod niedokończone lub wątpliwa lub Szybkie rozwiązania z ostrzeżeniami. Tokeny sygnału domyślne dostarczane przez program Visual Studio for Mac są TODO, HACK FIXME i COFNIĘTO, chociaż spersonalizowane tokenów mogą być zdefiniowane w obszarze **programu Visual Studio > Preferencje... > środowiska > zadań**, które przedstawiono poniżej:

 ![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz zadań, należy dodać komentarz, który zawiera słowo kluczowe zadania. Na przykład:

```
//TODO: Finish this for all properties.
```

Visual Studio for Mac koncentrują się na te znaczniki przez wyróżnianie je w konsoli do listy zadań, które można wyświetlić, przechodząc do **Widok > konsole > zadań**:

![Konsola listy zadań](media/source-editor-image11.png)