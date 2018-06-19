---
title: Dyrektywa T4 CleanUpBehavior
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 44d1dc61b1330b344b333b62c30308fdb65494d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946042"
---
# <a name="t4-cleanupbehavior-directive"></a>Dyrektywa T4 CleanUpBehavior

Aby usunąć element appDomain po przetworzeniu szablonu tekstu, należy umieścić następujący wiersz:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Szablony tekstowe są przetwarzane w elemencie appDomain, który jest oddzielony od procesu hosta. W większości przypadków, po przetworzeniu jednego szablonu tekstu element appDomain jest używany ponownie, aby przetworzyć następny szablon. Ale jeśli określisz CleanupBehavior, element appDomain zostanie usunięty, a kolejny szablon zostanie przetworzony w nowym elemencie appDomain.

To spowalnia przetwarzanie tekstu, ale może być przydatne, aby się upewnić, że zasoby są usunięte.

Ta dyrektywa działa tylko w hoście Visual Studio.