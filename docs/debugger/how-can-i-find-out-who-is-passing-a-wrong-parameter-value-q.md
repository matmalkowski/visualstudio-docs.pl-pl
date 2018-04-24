---
title: Jak można sprawdzić, kto przekazuje błędną wartość parametru? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a46497e45acb4663822b1a7bc6e4ad5a4f09af11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak można sprawdzić, kto przekazuje błędną wartość parametru?
## <a name="problem-description"></a>Opis problemu  
 Wartość parametru niewłaściwy jest przekazywany do jednej z mojej funkcji. Ta funkcja jest wywoływana z całego miejsca. Jak można znaleźć się, co jest przekazanie jej przez nieprawidłową wartość?  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="to-resolve-this-problem"></a>Aby rozwiązać ten problem  
  
1.  Ustaw punkt przerwania lokalizacji na początku funkcji.  
  
2.  Kliknij prawym przyciskiem myszy punkt przerwania, a następnie wybierz **warunku**.  
  
3.  W **warunku punktu przerwania** okno dialogowe, kliknij przycisk **warunku** pole wyboru. Zobacz [zaawansowane punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Wprowadź wyrażenie, takie jak `Var==3`, w polu tekstowym gdzie `Var` to nazwa parametru, który zawiera Zła wartość i `3` jest zła wartość przekazywana do niego.  
  
5.  Wybierz **ma wartość True** przycisk radiowy, a następnie kliknij przycisk **OK** przycisku.  
  
6.  Teraz ponownie uruchomić program. Punkt przerwania powoduje, że program zatrzymanie na początku funkcji podczas `Var` parametr ma wartość `3`.  
  
7.  Korzystanie z okna stosu wywołań można znaleźć funkcji wywołującej i przejdź do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Punkty przerwania](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)