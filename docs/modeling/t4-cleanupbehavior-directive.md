---
title: Dyrektywa T4 CleanUpBehavior | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f773f04799ec1ec975626699f37089c3c5b59b2d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="t4-cleanupbehavior-directive"></a>Dyrektywa T4 CleanUpBehavior
Aby usunąć element appDomain po przetworzeniu szablonu tekstu, należy umieścić następujący wiersz:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Szablony tekstowe są przetwarzane w elemencie appDomain, który jest oddzielony od procesu hosta. W większości przypadków, po przetworzeniu jednego szablonu tekstu element appDomain jest używany ponownie, aby przetworzyć następny szablon. Ale jeśli określisz CleanupBehavior, element appDomain zostanie usunięty, a kolejny szablon zostanie przetworzony w nowym elemencie appDomain.  
  
 To spowalnia przetwarzanie tekstu, ale może być przydatne, aby się upewnić, że zasoby są usunięte.  
  
 Ta dyrektywa działa tylko w hoście Visual Studio.