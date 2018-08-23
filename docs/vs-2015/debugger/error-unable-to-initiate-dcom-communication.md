---
title: 'Błąd: Nie można zainicjować komunikacji DCOM | Dokumentacja firmy Microsoft'
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
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8ee1e5a9a9f799a4e9d5d8a4cc3b6f5e03b504
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677937"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Błąd: nie można zainicjować komunikacji DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: nie można zainicjować komunikacji DCOM](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-initiate-dcom-communication).  
  
Wystąpił błąd modelu DCOM podczas próby komunikacji z komputerem zdalnym komputerze lokalnym. Jest to spowodowane przez zaporę na serwerze zdalnym lub uszkodzone uwierzytelniania Windows na komputerze zdalnym.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli maszyna zdalna ma włączoną zaporę Windows, zobacz [Ustaw się narzędzi zdalnych na urządzeniu](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) instrukcje dotyczące sposobu konfigurowania zapory dla debugowania lokalnego.  
  
-   Aby przywrócić uwierzytelniania Windows, spróbuj wykonać ponowny rozruch obu komputerach. Sprawdź dzienniki zdarzeń na komputerach lokalnych i zdalnych dla błędów protokołu Kerberos i skontaktuj się z administratorami domeny o znanych problemach.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)



