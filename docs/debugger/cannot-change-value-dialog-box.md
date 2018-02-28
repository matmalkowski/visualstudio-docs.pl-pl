---
title: "Nie można zmienić wartości — okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7a6b5cc2c1a5317009225d8e86fd497dc4367787
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="cannot-change-value-dialog-box"></a>Nie można zmienić wartości — okno dialogowe
## <a name="error"></a>Błąd  
 `The value of this variable cannot be changed`&#124; `The name` *nazwa* `does not exist in the current context` &#124; *różne inne komunikaty*  
  
 Ten komunikat zostanie wyświetlony podczas próby zmiany zawartości zmiennej na niedozwoloną wartość okna debugera (windows samochodów, obejrzyj ani lokalnych) lub QuickWatch — okno dialogowe. Na przykład Jeśli spróbujesz ustawić wartość zmiennej liczby całkowitej na ciąg znaków, zostanie wyświetlony ten komunikat.  
  
## <a name="solution"></a>Rozwiązanie  
 Upewnij się, dane wejściowe, można wpisać do okna debugera lub QuickWatch — okno dialogowe reprezentuje dozwoloną wartością zmiennej, którą próbujesz skonfigurować.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)