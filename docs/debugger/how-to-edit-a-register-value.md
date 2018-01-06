---
title: "Porady: Edytowanie wartości rejestru | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b9cc839b7829070f5d4c2e9db9da12b6522c21eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-a-register-value"></a>Porady: edytowanie wartości rejestru
Okno rejestrów jest dostępna tylko wtedy, gdy debugowanie poziomie adresu jest włączone w **opcje** okno dialogowe **debugowanie** węzła.  
  
### <a name="to-change-the-value-of-a-register"></a>Aby zmienić wartość rejestru  
  
1.  W **rejestruje** okna, użyj klawisza TAB lub mysz, aby przenieść wstawiania wskaż wartość ma zostać zmieniony. Po rozpoczęciu wpisywania kursor musi znajdować się przed wartością, którą chcesz zastąpić.  
  
2.  Wpisz nową wartość.  
  
    > [!CAUTION]
    >  Zmiana wartości rejestru (szczególnie w rejestrach element EIP i EBP) mogą wpływać na wykonywanie programów.  
  
    > [!CAUTION]
    >  Edytowanie wartości zmiennoprzecinkowych może spowodować pomocnicza nieścisłości z powodu konwersji decimal-binary ułamkowych składników. Nawet pozornie nieszkodliwe edycji może spowodować zmianę niektórych najmniej znaczących bitów w rejestrze zmiennoprzecinkowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)