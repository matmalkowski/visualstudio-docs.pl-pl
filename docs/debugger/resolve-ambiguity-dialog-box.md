---
title: "Okno dialogowe rozwiązywania niejednoznaczności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0050ccdb3a4ccbd2d1d116239ad6fd6aba2032e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="resolve-ambiguity-dialog-box"></a>Rozwiązywania niejednoznaczności — Okno dialogowe
`Resolve Ambiguity` Zostanie wyświetlone okno dialogowe, gdy debuger nie można wybrać lokalizację, aby wyświetlić. Na przykład jeśli korzystasz z szablonów języka C++, można utworzyć wiele funkcji z szablonu jednej funkcji. Jeśli debuger zatrzymuje się w lokalizacji źródłowej, w szablonie i użytkownik wybierze `Go To Disassembly`, debuger ma wiele opcji. Każda funkcja utworzone na podstawie szablonu ma własny kod dezasemblacji i debuger nie może określić, które kodu, który chcesz wyświetlić. `Resolve Ambiguity` — Okno dialogowe można wybrać lokalizację z listy wszystkich odpowiednich lokalizacjach.  
  
 `Choose the specific location`  
 Wyświetla listę wszystkich lokalizacji odpowiadający polecenia.  
  
 `Address`  
 Pokazuje adresów pamięci dla każdej funkcji.  
  
 `Function`  
 Zawiera nazwę każdej funkcji.  
  
 `Module`  
 Pokazuje modułu (plik EXE lub DLL) zawierającego kod obiektu dla tej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)