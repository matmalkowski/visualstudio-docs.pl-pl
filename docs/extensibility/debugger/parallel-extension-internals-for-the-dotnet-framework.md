---
title: Równoległe wewnętrzne rozszerzenia dla programu .NET Framework | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4cc64270cabb3e30ee3c13a1617222349e7b3677
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Wewnętrzne rozszerzenia równoległe dla programu .NET Framework
W tej sekcji opisano wewnętrzne typy metod i pola klasy, które ułatwiają wdrożenie niestandardowych debugera dla rozszerzeń równoległych programu .NET Framework.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)  
 Zawiera opis elementów członkowskich danych wewnętrznych <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy.  
  
 [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Zawiera opis elementów członkowskich danych wewnętrznych <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> klasy.  
  
 [Klasa ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Zawiera opis elementów członkowskich danych wewnętrznych `System.Threading.Tasks.ContingentProperties` klasy.  
  
 [AsyncTaskMethodBuilder Structure](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struktury.  
  
 [AsyncTaskMethodBuilder\<TResult> Structure](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struktury.  
  
 [AsyncVoidMethodBuilder Structure](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programowanie równoległe](/dotnet/standard/parallel-programming/index)