---
title: "Błąd: Zdalny komputer nie mógł zainicjować komunikacji DCOM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 377211f0ca7e4095da58b169f113689db9c7b41e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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