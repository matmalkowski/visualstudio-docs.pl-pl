---
title: "Gdzie można sprawdzić kody błędów Win32? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 508b741dcac0662d41e58b37ecaf177a2245010f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Gdzie można sprawdzić kody błędów Win32?
POWIODŁO SIĘ.. H w katalogu INCLUDE domyślnej instalacji systemu zawiera definicje kod błędu dla funkcji Win32 API.  
  
 Kod błędu można wyszukiwać, wpisując kod w **czujki** okna lub **QuickWatch** okno dialogowe. Na przykład:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)