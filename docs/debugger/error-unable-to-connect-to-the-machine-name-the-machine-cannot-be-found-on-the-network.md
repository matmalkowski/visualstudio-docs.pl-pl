---
title: "Błąd: Nie można nawiązać połączenia z maszyną &lt;nazwa&gt;. Nie można znaleźć komputera w sieci. | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: DCOM, unable to connect error
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8b7ef99717f0a68fbd17245958840c89cdf8544
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Błąd: Nie można nawiązać połączenia z maszyną &lt;nazwa&gt;. Nie można znaleźć komputera w sieci.
Dzieje się tak, jeśli jest spełniony jeden z następujących warunków:  
  
-   Połączenie z komputerem zdalnym zostało przerwane.  
  
-   Twoje konto użytkownika na komputerze zdalnym jest wyłączone.  
  
-   Na komputerze zdalnym hasło wygasło.  
  
### <a name="to-resolve-this-behavior"></a>Aby rozwiązać ten problem  
  
-   Upewnij się, że komputer lokalny i komputer zdalny znajdują się w tej samej sieci. Aby to zrobić, użyj Eksplorator systemu Microsoft Windows (lub Eksploratora plików), aby spróbować uzyskać dostęp do komputera zdalnego.  
  
     - i -  
  
-   Upewnij się, że konto użytkownika, którego używasz do nawiązania połączenia z komputerem zdalnym jest włączona.  
  
     - i -  
  
-   Upewnij się, że hasło, którego używasz do nawiązania połączenia z komputerem zdalnym jest prawidłowa i czy nie wygasł.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)   
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)