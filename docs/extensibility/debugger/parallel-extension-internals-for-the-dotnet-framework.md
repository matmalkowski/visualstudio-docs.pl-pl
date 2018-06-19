---
title: Równoległe wewnętrzne rozszerzenia dla programu .NET Framework | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4936efe50023ed1e193d0c2ec0d9c3423ac5cc64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100614"
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
  
 [Struktura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struktury.  
  
 [AsyncTaskMethodBuilder\<TResult> Structure](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struktury.  
  
 [Struktura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struktury.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programowanie równoległe](/dotnet/standard/parallel-programming/index)