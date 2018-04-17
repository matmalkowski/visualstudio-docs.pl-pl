---
title: 'Debugowanie F # | Dokumentacja firmy Microsoft'
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
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3a2b2651a8fc7f33ec30edc5d080d6d7e66c17e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-f"></a>Debugowanie F#
Debugowanie F # jest podobny do debugowania dowolnego języka zarządzanych, z pewnymi wyjątkami:  
  
-   **Automatycznych** okna nie są wyświetlane zmienne F #.  
  
-   Edytuj i Kontynuuj nie jest obsługiwane w F #. Edytowanie kodzie języka F # podczas sesji debugowania jest możliwe, ale należy unikać. Ponieważ zmiany kodu nie są stosowane podczas sesji debugowania, Edycja kodzie języka F # podczas debugowania spowoduje, że niezgodność między kodu źródłowego i kod debugowany.  
  
-   Debuger nie może rozpoznać wyrażenia F #. Aby wprowadzić wyrażenie okna debugera lub okna dialogowego podczas debugowania F #, musi translacji wyrażenia w C# składni. Podczas tłumaczenia wyrażenia F # w języku C#, upewnij się, że należy pamiętać, że C# używa == jako operator porównania równości i że F # używa pojedynczego =.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
