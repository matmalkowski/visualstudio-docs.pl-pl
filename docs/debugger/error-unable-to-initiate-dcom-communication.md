---
title: 'Błąd: Nie można zainicjować komunikacji DCOM | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c34de251125b49c8b3d7aebf301468b9b1d0252a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471798"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Błąd: nie można zainicjować komunikacji DCOM
Wystąpił błąd modelu DCOM podczas próby komunikacji z komputerem zdalnym komputerze lokalnym. Jest to spowodowane przez zaporę na serwerze zdalnym lub przerwane uwierzytelniania systemu Windows na komputerze zdalnym.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli komputer zdalny jest włączona Zapora systemu Windows, zobacz [zdalnego debugowania](../debugger/remote-debugging.md) instrukcje dotyczące sposobu konfigurowania zapory dla debugowania lokalnego.  
  
-   Aby przywrócić uwierzytelniania systemu Windows, spróbuj wykonać ponowny rozruch obydwie maszyny. Sprawdź dzienniki zdarzeń na komputerach lokalnych i zdalnych dla błędów protokołu Kerberos i skontaktuj się z administratorami domeny o znanych problemach.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)