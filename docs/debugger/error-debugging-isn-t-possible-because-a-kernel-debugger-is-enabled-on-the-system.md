---
title: "Błąd: Debugowanie nie jest &#39; t, możliwe, ponieważ debuger jądra jest włączone w systemie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: kernel debugger
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0841b6e6d592a8b09b85e744d693f0b356fcbf9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Błąd: Debugowanie nie jest &#39; t, możliwe, ponieważ debuger jądra jest włączone w systemie
Podczas debugowania kodu zarządzanego, mogą pojawić się następujący komunikat o błędzie:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Ten komunikat jest wyświetlany podczas debugowania kodu zarządzanego:  
  
-   na [!INCLUDE[win7](../debugger/includes/win7_md.md)] lub [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]system, który został uruchomiony w trybie debugowania.  
  
-   Aplikacja używa wersji środowiska CLR CLR 2.0, 3.0 lub 3.5.  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem  
  
-   Uaktualnienie aplikacji umożliwiająca użycie CLR w wersji 4.0 lub 4.5  
  
     —lub—  
  
-   Wyłącz debugowanie jądra i debugowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     —lub—  
  
-   Debugowanie za pomocą debugera jądra zamiast [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     —lub—  
  
-   Za pomocą debugera jądra Wyłącz wyjątki trybu użytkownika.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Aby wyłączyć debugowanie jądra w bieżącej sesji  
  
-   W wierszu polecenia wpisz polecenie:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Aby wyłączyć debugowanie jądra do wszystkich sesji (system Windows Vista i Windows 7)  
  
1.  W wierszu polecenia wpisz polecenie:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Uruchom ponownie komputer.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Aby wyłączyć debugowanie jądra do wszystkich sesji (inne systemy operacyjne Windows)  
  
1.  Zlokalizuj plik boot.ini na dysku systemowym (zazwyczaj C:\\). Plik boot.ini mogą być ukryte i tylko do odczytu. W związku z tym należy użyć następującego polecenia go wyświetlać:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Otwórz plik boot.ini za pomocą Notatnika i Usuń następujące opcje:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Uruchom ponownie komputer.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Aby debugować z debuger jądra  
  
1.  Jeśli debuger jądra jest podłączony, zobaczysz komunikat z pytaniem, czy chcesz kontynuować debugowanie. Kliknij przycisk, aby kontynuować.  
  
2.  Może spowodować, że `User break exception(Int 3).` Jeśli ten problem wystąpi, wpisz następujące polecenie debuger jądra do kontynuowania debugowania:  
  
     `gn`  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)