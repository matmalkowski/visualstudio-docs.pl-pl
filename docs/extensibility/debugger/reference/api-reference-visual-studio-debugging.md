---
title: Dokumentacja interfejsu API (Visual Studio debugowanie) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f6e3110ca4988fcc12e547f3bcd82c1026f3aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="api-reference-visual-studio-debugging"></a>Dokumentacja interfejsu API (debugowania programu Visual Studio)
Ta część zawiera omówienie interfejsu API, przewodnik pokazujący składni i użycia dla wszystkich elementów interfejsu API i gamę przykłady kodu. Wszystkie odwołania alfabetycznym według kategorii.  
  
 W poniższej tabeli przedstawiono typowe `HRESULT` wartości zwracane przez metody.  
  
|Nazwa|Opis|Wartość|  
|----------|-----------------|-----------|  
|S_OK|Powodzenie.|0x00000000|  
|E_UNEXPECTED|Nieoczekiwany błąd.|0x8000FFFF|  
|E_NOTIMPL|Nie jest zaimplementowana.|0x80004001|  
|E_OUTOFMEMORY|Za mało pamięci do ukończenia tej operacji.|0x8007000E|  
|E_INVALIDARG|Jeden lub więcej argumentów są nieprawidłowe.|0x80070057|  
|E_NOINTERFACE|Taki interfejs obsługiwane.|0x80004002|  
|E_POINTER|Nieprawidłowy wskaźnik.|0x80004003|  
|E_HANDLE|Nieprawidłowe dojście.|0x80070006|  
|E_ABORT|Operacja została przerwana.|0x80004004|  
|E_FAIL|Nieoczekiwany błąd.|0x80004005|  
|E_ACCESSDENIED|Ogólny błąd odmowy dostępu.|0x80070005|  
  
> [!NOTE]
>  Gdy [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowania metoda zwraca `S_OK`, zakłada się, że wszystkie limit wskaźniki parametru są poprawne i oznacza to, że weryfikacja nie jest przeprowadzane na limitu wskaźników parametr podczas `S_OK` jest zwracany.  
  
> [!NOTE]
>  Nieprawidłowy lub `NULL` [parametry out] może spowodować awarię IDE.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)