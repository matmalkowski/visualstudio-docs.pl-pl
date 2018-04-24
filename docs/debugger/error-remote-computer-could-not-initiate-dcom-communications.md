---
title: 'Błąd: Zdalny komputer nie mógł zainicjować komunikacji DCOM | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
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
ms.openlocfilehash: 111c8b010f9d1415e8e9e4e86e1401346f78702d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Błąd: Zdalny komputer nie mógł zainicjować komunikacji DCOM
Wystąpił błąd modelu DCOM, gdy komputer zdalny próbował komunikować się z komputera lokalnego. Komputer, który jest to komputer lokalny  
  
 działanie programu Visual Studio. Ten błąd może wystąpić z kilku powodów:  
  
-   Komputer lokalny jest włączona Zapora.  
  
-   Uwierzytelnianie systemu Windows z komputera zdalnego na komputerze lokalnym nie działa.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli komputer lokalny jest włączona Zapora systemu Windows, zobacz [zdalnego debugowania](../debugger/remote-debugging.md) instrukcje dotyczące sposobu konfigurowania zapory dla debugowania lokalnego.  
  
2.  Test uwierzytelniania systemu Windows przez próby otwarcia z serwera zdalnego udziału plików na komputerze lokalnym.  
  
3.  Aby przywrócić uwierzytelniania systemu Windows, spróbuj wykonać ponowny rozruch obydwie maszyny. Sprawdź dzienniki zdarzeń na komputerach lokalnych i zdalnych dla błędów protokołu Kerberos i skontaktuj się z administratorami domeny o znanych problemach.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)