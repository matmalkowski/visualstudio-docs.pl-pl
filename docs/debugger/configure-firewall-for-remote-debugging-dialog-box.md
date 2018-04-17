---
title: Konfigurowanie zapory do zdalnego debugowania — okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8a3bef8a355b27fd5a566ccef7ac1a96223f119
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Konfigurowanie zapory do zdalnego debugowania — Okno dialogowe
To okno dialogowe jest wyświetlany, gdy Zapora systemu Windows zablokuje debugera z odbieranie informacji za pośrednictwem sieci. Aby kontynuować debugowanie zdalne, należy otworzyć dziury w zaporze, debuger może odbierać informacje.  
  
> [!CAUTION]
>  Otwieranie dziury w zaporze może narazić komputer na zagrożenia, które Zapora jest przeznaczone do blokowania zabezpieczeń. Otwieranie przerw do zdalnego debugowania odblokowuje porty 4020 i 4021 w programie Visual Studio 2015. W innych wersjach programu Visual Studio są używane inne numery portów. Aby uzyskać więcej informacji, zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Ponadto pozwala on debugera otworzyć porty dodatkowe. Aby uzyskać więcej informacji, zobacz [konfigurowania Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Anuluj debugowanie zdalne**  
 Anuluje próba debugowania zdalnego. Ustawienia zabezpieczeń komputera pozostaną nienaruszone.  
  
 **Odblokuj debugowanie zdalne z komputerami w sieci lokalnej (podsieci)**  
 Umożliwia zdalne debugowanie komputerów w podsieci lokalnej. Może to otwarcie luk w zabezpieczeniach dla komputerów w podsieci lokalnej, ale zapory w dalszym ciągu zablokować informacje pochodzące spoza tej podsieci.  
  
 **Odblokuj debugowanie zdalne z dowolnego komputera**  
 Umożliwia zdalne debugowanie maszyn w dowolnym miejscu w sieci. To ustawienie jest najmniej bezpieczna.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)  
 [Debugowanie odwołań do interfejsu użytkownika](../debugger/debugging-user-interface-reference.md)