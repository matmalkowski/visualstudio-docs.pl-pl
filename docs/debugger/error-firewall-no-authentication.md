---
title: "Błąd: Brak uwierzytelnienia zapory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1750c0ab8bafe53136d01ba27ada9c242b318c3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="error-firewall-no-authentication"></a>Błąd: Brak uwierzytelnienia zapory
Nie skonfigurowano Zapora połączenia internetowego na komputerze zdalnym w celu zezwolenia na debugowanie zdalne. Debugowanie zdalne z `No Authentication`, msvsmon.exe musi zostać dodany do listy wyjątków. Otwieranie portów niektórych IPSEC może być konieczne również.  
  
> [!NOTE]
>  Zdalny debuger będzie mógł automatycznie skonfigurować Zaporę systemu Windows. W przypadku używania innej zapory niż Zapora systemu Windows, takich jak Zapora oprogramowania innych firm lub Zapora sprzętu, zapory należy ręcznie skonfigurować w celu zezwolenia na debugowanie zdalne. W tym celu należy zezwolić na ruch na portach TCP/IP tego msvsmon.exe nasłuchuje. Domyślnie są to porty 4018 i 4019, gdzie 4018 jest używany we wszystkich systemach operacyjnych, a 4019 jest używana tylko w systemie Windows x64 w celu zezwolenia na debugowanie x86 procesów.  
  
 Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).