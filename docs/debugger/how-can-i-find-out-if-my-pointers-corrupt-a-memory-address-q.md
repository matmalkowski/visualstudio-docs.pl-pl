---
title: "Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci? | Dokumentacja firmy Microsoft"
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
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a57b36fc1d1dd25f439f65fe9d72cec6aab63471
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Jak można sprawdzić, czy wskaźniki uszkadzają adresy pamięci?
## <a name="problem-description"></a>Opis problemu  
 Myślę, że jeden wskaźniki może uszkodzenie pamięci pod adresem 0x00408000. Jak można znaleźć się, co dzieje się?  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="check-for-heap-corruption"></a>Sprawdź, czy uszkodzenie sterty  
  
-   Większość uszkodzenie pamięci jest rzeczywiście z powodu uszkodzenia sterty. Spróbuj użyć globalne flagi narzędzia (gflags.exe) lub pageheap.exe. Zobacz [http://support.microsoft.com/default.aspx?scid=kb;en-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Aby dowiedzieć się, gdzie jest modyfikowany adres pamięci  
  
1.  Ustaw punkt przerwania danych na 0x00408000. Zobacz [Ustaw punkt przerwania zmian danych (tylko C++ natywnego)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Użyj po trafieniu punktu przerwania **pamięci** zawartości okna, aby wyświetlić pamięci, zaczynając od 0x00408000. Aby uzyskać więcej informacji, zobacz [Windows pamięci](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)