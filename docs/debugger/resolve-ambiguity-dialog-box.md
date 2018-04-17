---
title: Okno dialogowe rozwiązywania niejednoznaczności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dcd6a9df3fb60dc61a0d9ed2e8586b77ba22e05f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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