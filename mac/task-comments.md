---
title: Komentarz do zadań
description: Dodawanie zadań komentarze w kodzie
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 23ce804476b6495d45e114728b287c1f5f85d1d9
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956640"
---
# <a name="task-comments"></a>Komentarz do zadań

Podczas pisania kodu, jest standardową praktyką jawnie komentarz kod niedokończone lub wątpliwa lub Szybkie rozwiązania z ostrzeżeniami. Tokeny sygnału domyślne, które są dostarczane przez program Visual Studio for Mac to TODO, HACK FIXME i COFNIĘTO. Spersonalizowane tokenów mogą być zdefiniowane w obszarze **programu Visual Studio > Preferencje... > środowiska > zadań**, jak pokazano na poniższej ilustracji:

 ![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz zadań, należy dodać komentarz, który zawiera słowo kluczowe zadania. Na przykład:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio for Mac koncentrują się na te znaczniki przez wyróżnianie je w konsoli do listy zadań, które można wyświetlić, przechodząc do **Widok > konsole > zadań**:

![Konsola listy zadań](media/source-editor-image11.png)