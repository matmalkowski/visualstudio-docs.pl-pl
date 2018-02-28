---
title: "Błąd: Brak uwierzytelnienia zapory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aed8e53436b43ba6d5cef6b50691df278f639f6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-firewall-no-authentication"></a>Błąd: Brak uwierzytelnienia zapory
Nie skonfigurowano Zapora połączenia internetowego na komputerze zdalnym w celu zezwolenia na debugowanie zdalne. Debugowanie zdalne z `No Authentication`, msvsmon.exe musi zostać dodany do listy wyjątków. Otwieranie portów niektórych IPSEC może być konieczne również.  
  
> [!NOTE]
>  Zdalny debuger będzie mógł automatycznie skonfigurować Zaporę systemu Windows. W przypadku używania innej zapory niż Zapora systemu Windows, takich jak Zapora oprogramowania innych firm lub Zapora sprzętu, zapory należy ręcznie skonfigurować w celu zezwolenia na debugowanie zdalne. W tym celu należy zezwolić na ruch na portach TCP/IP tego msvsmon.exe nasłuchuje. Domyślnie są to porty 4018 i 4019, gdzie 4018 jest używany we wszystkich systemach operacyjnych, a 4019 jest używana tylko w systemie Windows x64 w celu zezwolenia na debugowanie x86 procesów.  
  
 Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).