---
title: Komentarze do zadania
description: Dodawanie zadań komentarzy w kodzie
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 44d82becfbf3a16ccd2158ac05e171e8530cd721
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42624334"
---
# <a name="task-comments"></a>Komentarze do zadania

Podczas pisania kodu jest standardową praktyką, aby jawnie dodać komentarz niedokończone lub wątpliwe kodu lub szybkiego rozwiązania problemu z ostrzeżeniami. Tokeny sygnału domyślne, które są dostarczane przez program Visual Studio dla komputerów Mac to TODO, HACK, FIXME i UNDONE. Spersonalizowane tokenów można zdefiniować pod **programu Visual Studio > Preferencje... > środowisko > zadania**, jak pokazano na poniższej ilustracji:

 ![Preferencje listy zadań](media/source-editor-image10.png)

Aby dodać nowy komentarz do zadania, należy dodać komentarz, który zawiera słowo kluczowe zadania. Na przykład:

```csharp
//TODO: Finish this for all properties.
```

Program Visual Studio for Mac koncentrują się na te znaczniki przez wyróżnianie je w konsoli do listy zadań, które można wyświetlić, przechodząc do **Widok > okienka > zadanie**:

![Konsola listy zadań](media/source-editor-image11.png)