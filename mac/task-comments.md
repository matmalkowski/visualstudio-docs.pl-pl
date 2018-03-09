---
title: "Komentarz do zadań"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 674bae5b22c5b9ecc5d6fda4a9a4e30e4fcd1660
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="task-comments"></a>Komentarz do zadań

Podczas pisania kodu, jest standardową praktyką jawnie komentarz kod niedokończone lub wątpliwa lub Szybkie rozwiązania z ostrzeżeniami. Tokeny sygnału domyślne, które są dostarczane przez program Visual Studio for Mac to TODO, HACK FIXME i COFNIĘTO. Spersonalizowane tokenów mogą być zdefiniowane w obszarze **programu Visual Studio > Preferencje... > środowiska > zadań**, jak pokazano na poniższej ilustracji:

 ![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz zadań, należy dodać komentarz, który zawiera słowo kluczowe zadania. Na przykład:

```
//TODO: Finish this for all properties.
```

Visual Studio for Mac koncentrują się na te znaczniki przez wyróżnianie je w konsoli do listy zadań, które można wyświetlić, przechodząc do **Widok > konsole > zadań**:

![Konsola listy zadań](media/source-editor-image11.png)