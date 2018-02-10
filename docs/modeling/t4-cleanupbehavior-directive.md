---
title: Dyrektywa T4 CleanUpBehavior | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7df9fb0c4d567e6af4a0ac1ea3d8ab4832ffe5a7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="t4-cleanupbehavior-directive"></a>Dyrektywa T4 CleanUpBehavior
Aby usunąć element appDomain po przetworzeniu szablonu tekstu, należy umieścić następujący wiersz:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Szablony tekstowe są przetwarzane w elemencie appDomain, który jest oddzielony od procesu hosta. W większości przypadków, po przetworzeniu jednego szablonu tekstu element appDomain jest używany ponownie, aby przetworzyć następny szablon. Ale jeśli określisz CleanupBehavior, element appDomain zostanie usunięty, a kolejny szablon zostanie przetworzony w nowym elemencie appDomain.  
  
 To spowalnia przetwarzanie tekstu, ale może być przydatne, aby się upewnić, że zasoby są usunięte.  
  
 Ta dyrektywa działa tylko w hoście Visual Studio.