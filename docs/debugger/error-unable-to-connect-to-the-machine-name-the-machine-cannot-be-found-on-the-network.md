---
title: 'Błąd: Nie można nawiązać połączenia z maszyną &lt;nazwa&gt;. Nie można znaleźć komputera w sieci. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e0654148823d40277bdd9c6b6d8ec5b881fdb80
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480062"
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