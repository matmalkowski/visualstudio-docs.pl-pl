---
title: Mieszane kodu i brakujące informacje w oknie stosu wywołań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 7f0a0822dc99eccea4ddd621ae622a112e0909bb
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151989"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Kod mieszany i brakujące informacje w oknie stosu wywołań
Ze względu na różnice stosy wywołań dla kodu zarządzanego i natywnego debuger zawsze nie można wyświetlić pełny stos wywołań, gdy kod wpisuje mieszanego. Gdy kod natywny wywołuje kod zarządzany, możesz zauważyć poniższe niezgodności w **stos wywołań** okna:  
  
-   Ramka natywna bezpośrednio nad kod zarządzany może być brak **stos wywołań** okna. Aby uzyskać więcej informacji, zobacz [porady: wychodzenia z kodu zarządzanego, gdy ramek natywnych brakuje oknie stosu wywołań](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Dla aplikacji w trybie mieszanym uruchomiony poza debugerem **stos wywołań** okno może być wyświetlany tylko kodu zarządzanego i Brak ramek natywnych będą widoczne.  
  
 Oba przypadki są stosunkowo rzadkie. W najbardziej macierzystych wywołań do kodu zarządzanego stosy wywołań są poprawnie wyświetlane.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)