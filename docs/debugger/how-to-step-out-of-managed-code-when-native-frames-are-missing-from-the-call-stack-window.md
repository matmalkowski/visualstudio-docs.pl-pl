---
title: "Porady: wychodzenia z kodu zarządzanego gdy ramek natywnych brakuje oknie stosu wywołań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7599c99c9375cda7b5f24432db8c137c5c4357df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Porady: wychodzenia z kodu zarządzanego gdy w oknie stosu wywołań brakuje ramek natywnych
Jeśli kod ma ramek natywnych, które nie są widoczne w **stos wywołań** okna, wykonywanie krok po kroku z kodu zarządzanego może spowodować nieoczekiwane wyniki. Jako rozwiązanie alternatywne można użyć zamiast punkt przerwania **Wyjdź**.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Do wychodzenia z kodu zarządzanego gdy wyświetlania stosu wywołań brakuje ramek natywnych  
  
1.  W kodzie natywnym należy ustawić punkt przerwania lokalizacji po wywołaniu kodu zarządzanego.  
  
2.  Na **debugowania** menu, wybierz **Kontynuuj**.  
  
     Po zakończeniu wywołania zarządzanego, wykonanie zatrzyma się na punkt przerwania w kodzie natywnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)