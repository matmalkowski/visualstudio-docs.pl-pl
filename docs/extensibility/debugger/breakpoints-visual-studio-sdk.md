---
title: Punkty przerwania (Visual Studio SDK) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: be8f0b36ebe57041e9d36b8f606bd5bddd0601bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoints-visual-studio-sdk"></a>Punkty przerwania (Visual Studio SDK)
Istnieją trzy typy punktów przerwania: Oczekujące powiązaną i błędów.  
  
 **A oczekujących punktu przerwania:**  
  
-   Jest klasą abstrakcyjną, która zawiera wszystkie informacje wymagane do powiązania punktu przerwania do co najmniej jeden kontekst kodu w jednej lub wielu programów. Za każdym razem program debugowany kod przyczyny załadować, aparat debugowania sprawdza wszystkie punkty przerwania oczekujące, aby zobaczyć, czy może być powiązana.  
  
     Oczekującym punktem przerwania się nigdy nie wiąże kodu, ale raczej zbiera i ma zawierać wszystkie powiązane punktów przerwania, które generuje.  
  
-   Jest reprezentowana przez [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsu.  
  
 **Powiązania punktu przerwania:**  
  
-   Jest skojarzony z abstrakcję dla punktu przerwania lub powiązane z kontekstem pojedynczy kod. Każdego powiązania punktu przerwania jest generowany w odpowiedzi na oczekującym punktem przerwania. Oczekującym punktem przerwania, można wygenerować więcej niż jednego powiązania punktu przerwania.  
  
     Jeśli kod jest zwolniony, powiązania punktu przerwania może być niepowiązany i odrzucone.  
  
-   Jest reprezentowana przez [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfejsu.  
  
 **Błąd punktu przerwania:**  
  
-   To Abstrakcja opisu wystąpił błąd podczas próby powiązania oczekującym punktem przerwania kontekstu kodu. Błąd punktu przerwania w tym artykule opisano albo wystąpił błąd w lokalizacji lub wyrażenia punktu przerwania. Aby uzyskać więcej informacji, zobacz [wiązania punktów przerwania](../../extensibility/debugger/binding-breakpoints.md).  
  
     Błąd przerwania może być błąd lub ostrzeżenie.  
  
-   Jest reprezentowana przez [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)