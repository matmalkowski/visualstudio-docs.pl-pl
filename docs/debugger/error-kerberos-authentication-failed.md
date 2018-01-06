---
title: "Błąd: Uwierzytelnianie Kerberos nie powiodło się. | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5c34b15d1611eaad106f3843070620af4470bc04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-kerberos-authentication-failed"></a>Błąd: Uwierzytelnianie Kerberos nie powiodło się
Podczas próby wykonania zdalnego debugowania, może uzyskać następujący komunikat o błędzie:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.  
```  
  
 Ten błąd występuje, gdy program Visual Studio Monitor debugera zdalnego działa na koncie systemu lokalnego lub usługi sieciowej. W jednym z tych kont zdalny debuger nawiązać połączenie uwierzytelniania Kerberos do komunikacji komputer-host debugera programu Visual Studio.  
  
 Uwierzytelnianie Kerberos nie jest dostępny w tych warunkach:  
  
-   Na komputerze docelowym lub debugera komputer-host znajduje się w grupie roboczej, a nie do domeny  
  
     \-lub -  
  
-   Kerberos została wyłączona na kontrolerze domeny.  
  
 Jeśli uwierzytelnianie Kerberos nie jest dostępna, należy zmienić konto, które jest używane do uruchamiania programu Visual Studio Monitor debugera zdalnego. Opis odpowiedniej procedury znajduje się w temacie [błąd: usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
 Jeśli oba komputery są podłączone do tej samej domeny, a ten komunikat nadal jest wyświetlany, sprawdź, czy DNS na komputerze docelowym jest poprawnie rozpoznawania nazwy komputera-hosta debugera. Przejrzyj następującą procedurę.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Aby sprawdzić, czy DNS na komputerze docelowym poprawnie mapuje nazwę komputera hosta debugera  
  
1.  Na komputerze docelowym, otwórz **Start** menu wskaż **Akcesoria** , a następnie kliknij przycisk **wiersza polecenia**.  
  
2.  W **wiersza polecenia** okna, wpisz:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  W pierwszym wierszu `ping` odpowiedzi zawiera pełną nazwę komputera i adres IP zwrócony przez serwer DNS dla określonego komputera.  
  
4.  Na komputerze hosta debugera, otwórz **wiersza polecenia** okna i uruchom `ipconfig`.  
  
5.  Porównaj wartości adresów IP.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)