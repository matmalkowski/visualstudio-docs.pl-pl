---
title: Kontynuowanie wykonania po wyjątkach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b26fe427ba83eea9e989e492fde89ade498a114
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466182"
---
# <a name="continuing-execution-after-an-exception"></a>Kontynuowanie wykonania po wyjątkach
Debuger przerywa wykonywanie z powodu wyjątku, zobaczysz **pomocnika wyjątków**, domyślnie. Jeśli zostało wyłączone **pomocnika wyjątków** w **opcje** zobaczysz okno dialogowe **Asystenta wyjątków** (C# lub Visual Basic) lub **wyjątku**  okno dialogowe (C++).  
  
 Gdy **pomocnika wyjątków** pojawia się, można spróbować rozwiązać ten problem, który spowodował wyjątek.
  
## <a name="managed-and-native-code"></a>Kodu zarządzanego i natywnego  
 W kodu zarządzanego i natywnego można kontynuować wykonywania w tym samym wątku po wystąpieniu nieobsługiwanego wyjątku. **Pomocnika wyjątków** cofa stosu wywołań do punktu, w której wystąpił wyjątek.
  
## <a name="mixed-code"></a>Kod mieszany  
 Jeśli naciśniesz nieobsługiwany wyjątek podczas debugowania mieszanych kodu natywnego i zarządzanego ograniczenia systemu operacyjnego zapobiec odwijanie stosu wywołań. Jeśli spróbujesz przewijanie stos wywołań za pomocą menu skrótów, komunikat o błędzie wyjaśniono, że debuger nie może wykonać odwinięcia z nieobsługiwanego podczas debugowania kodu mieszany, z wyjątkiem.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)