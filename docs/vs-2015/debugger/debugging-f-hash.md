---
title: 'Debugowanie F # | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5790b81eedb1a1bb9dc65b7ce053089c3bc1470
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633197"
---
# <a name="debugging-f"></a>Debugowanie F# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [debugowanie F #](https://docs.microsoft.com/visualstudio/debugger/debugging-f-hash).  
  
Debugowanie F # jest podobne do debugowania jakiegokolwiek języka zarządzanego, z pewnymi wyjątkami:  
  
-   **Autos** okna nie są wyświetlane zmienne F #.  
  
-   Edytuj i Kontynuuj nie jest obsługiwane w języku F #. Edytowanie kodu F # podczas sesji debugowania jest możliwe, ale należy unikać. Ponieważ zmiany w kodzie nie są stosowane podczas sesji debugowania, edytowanie F # kodu podczas debugowania spowoduje niezgodność między kodem źródłowym i debugowany kod.  
  
-   Debuger nie może rozpoznać wyrażeń języka F #. Aby wprowadzić wyrażenie w oknie debugera lub okno dialogowe podczas debugowania F #, wykonuje translację wyrażenia w języku C# składni. Podczas tłumaczenia jest wyrażenie F # do języka C#, upewnij się, że należy pamiętać, że C# używa == jako operator porównania dla równości i że F # używa pojedynczego =.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)



