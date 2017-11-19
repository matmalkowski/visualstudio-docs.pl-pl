---
title: 'Debugowanie F # | Dokumentacja firmy Microsoft'
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
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51eaed204db7b50e75a18dfac104a00546770abc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-f"></a>Debugowanie F#
Debugowanie F # jest podobny do debugowania dowolnego języka zarządzanych, z pewnymi wyjątkami:  
  
-   **Automatycznych** okna nie są wyświetlane zmienne F #.  
  
-   Edytuj i Kontynuuj nie jest obsługiwane w F #. Edytowanie kodzie języka F # podczas sesji debugowania jest możliwe, ale należy unikać. Ponieważ zmiany kodu nie są stosowane podczas sesji debugowania, Edycja kodzie języka F # podczas debugowania spowoduje, że niezgodność między kodu źródłowego i kod debugowany.  
  
-   Debuger nie może rozpoznać wyrażenia F #. Aby wprowadzić wyrażenie okna debugera lub okna dialogowego podczas debugowania F #, musi translacji wyrażenia w C# składni. Podczas tłumaczenia wyrażenia F # w języku C#, upewnij się, że należy pamiętać, że C# używa == jako operator porównania równości i że F # używa pojedynczego =.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
