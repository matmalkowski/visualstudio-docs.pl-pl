---
title: 'Debugowanie F # | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 2b3bb2a9379dd6cd43bb0398ccda2b031b96d56e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473793"
---
# <a name="debugging-f"></a>Debugowanie F#
Debugowanie F # jest podobny do debugowania dowolnego języka zarządzanych, z pewnymi wyjątkami:  
  
-   **Automatycznych** okna nie są wyświetlane zmienne F #.  
  
-   Edytuj i Kontynuuj nie jest obsługiwane w F #. Edytowanie kodzie języka F # podczas sesji debugowania jest możliwe, ale należy unikać. Ponieważ zmiany kodu nie są stosowane podczas sesji debugowania, Edycja kodzie języka F # podczas debugowania spowoduje, że niezgodność między kodu źródłowego i kod debugowany.  
  
-   Debuger nie może rozpoznać wyrażenia F #. Aby wprowadzić wyrażenie okna debugera lub okna dialogowego podczas debugowania F #, musi translacji wyrażenia w C# składni. Podczas tłumaczenia wyrażenia F # w języku C#, upewnij się, że należy pamiętać, że C# używa == jako operator porównania równości i że F # używa pojedynczego =.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
