---
title: 'Błąd: Uwierzytelnianie Kerberos nie powiodło się. | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed475ecf2ac0bd62dd710832540d599cb367aedc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677964"
---
# <a name="error-kerberos-authentication-failed"></a>Błąd: Uwierzytelnianie Kerberos nie powiodło się
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: nie można przeprowadzić uwierzytelniania Kerberos](https://docs.microsoft.com/visualstudio/debugger/error-kerberos-authentication-failed).  
  
Gdy użytkownik próbuje przeprowadzać debugowanie zdalne, może uzyskać następujący komunikat o błędzie:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos auythentication failed.  
```  
  
 Ten błąd występuje, gdy zdalny Monitor debugowania Visual Studio jest uruchomiony na koncie systemu lokalnego lub usługi sieciowej. W ramach jednego z tych kont debuger zdalny nawiązać połączenie uwierzytelniania Kerberos do komunikacji zwrotnej z komputera hosta debugera programu Visual Studio.  
  
 Uwierzytelnianie Kerberos nie jest dostępne w tych warunkach:  
  
-   Na komputerze docelowym lub debugera komputer-host znajduje się w grupie roboczej, a nie do domeny  
  
     \- lub —  
  
-   Protokołu Kerberos zostało wyłączone na kontrolerze domeny.  
  
 Jeśli uwierzytelnianie Kerberos nie jest dostępna, należy zmienić konto, które jest używane do uruchamiania programu Visual Studio Monitor zdalnego debugowania. Procedury, zobacz [błąd: usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
 Jeśli oba komputery są połączone z tej samej domenie, a nadal otrzymujesz ten komunikat, sprawdź, czy DNS na komputerze docelowym jest poprawnie rozpoznawania nazwy komputera-hosta debugera. Zobacz poniższą procedurę.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Aby sprawdzić, czy DNS na komputerze docelowym poprawnie mapuje nazwę komputera hosta debugera  
  
1.  Na komputerze docelowym, otwórz **Start** menu wskaż **Akcesoria** a następnie kliknij przycisk **polecenia**.  
  
2.  W **polecenia** okna, typ:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  W pierwszym wierszu `ping` odpowiedzi zawiera pełną nazwę komputera i adres IP zwrócony przez serwer DNS dla określonego komputera.  
  
4.  Na komputerze-hoście debugera, otwarcie **polecenia** okna i uruchom `ipconfig`.  
  
5.  Porównaj wartości adresów IP.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



