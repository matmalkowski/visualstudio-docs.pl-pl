---
title: Nie można zmienić wartości — okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23a6eb8059d9780e3b7343c6a7864896a0c529c6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="cannot-change-value-dialog-box"></a>Nie można zmienić wartości — okno dialogowe
## <a name="error"></a>Błąd  
 `The value of this variable cannot be changed` &#124;`The name` *nazwa* `does not exist in the current context` &#124; *różne inne komunikaty*  
  
 Ten komunikat zostanie wyświetlony podczas próby zmiany zawartości zmiennej na niedozwoloną wartość okna debugera (windows samochodów, obejrzyj ani lokalnych) lub QuickWatch — okno dialogowe. Na przykład Jeśli spróbujesz ustawić wartość zmiennej liczby całkowitej na ciąg znaków, zostanie wyświetlony ten komunikat.  
  
## <a name="solution"></a>Rozwiązanie  
 Upewnij się, dane wejściowe, można wpisać do okna debugera lub QuickWatch — okno dialogowe reprezentuje dozwoloną wartością zmiennej, którą próbujesz skonfigurować.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)