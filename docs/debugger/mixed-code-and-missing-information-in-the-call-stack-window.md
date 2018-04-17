---
title: Mieszane kodu i brakujące informacje w oknie stosu wywołań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 580fc3b87173a120480f708e8b349fbb6942bbdb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Kod mieszany i brakujące informacje w oknie stosu wywołań
Z powodu różnic między stosy wywołań do kodu zarządzanego i natywnego debuger zawsze nie można wyświetlić stosu wywołań pełną, gdy mieszane typy kodu. Gdy natywny kod wywołuje kod zarządzany, możesz zauważyć następujące rozbieżności w **stos wywołań** okno:  
  
-   Może brakować natywną bezpośrednio nad kodu zarządzanego z **stos wywołań** okna. Aby uzyskać więcej informacji, zobacz [porady: wychodzenia z kodu zarządzanego gdy ramek natywnych brakuje oknie stosu wywołań](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Do uruchomienia poza debugerem, aplikacje w trybie mieszanym **stos wywołań** okna mogą wyświetlać tylko kod zarządzany, a żaden z ramek natywnych nie będzie widoczna.  
  
 Obu przypadkach są stosunkowo rzadko. W najbardziej macierzystych wywołań do kodu zarządzanego stosy wywołań są wyświetlane poprawnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)