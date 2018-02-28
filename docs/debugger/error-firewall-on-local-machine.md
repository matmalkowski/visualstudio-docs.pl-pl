---
title: "Błąd: Zapora na komputerze lokalnym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: 160e71e357046b69019323ada5ff9cde006460bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Nie skonfigurowano Zapora połączenia internetowego na komputerze lokalnym komputerze, na którym uruchamiasz program Visual Studio, w celu zezwolenia na debugowanie zdalne. Zarządzanym lub macierzystym zdalne debugowanie z domyślny transport, należy otworzyć port TCP 135 dla ruchu modelu DCOM. Udostępnianie plików i drukarek muszą być otwarte i devenv.exe musi zostać dodany do listy wyjątków. Otwieranie portów niektórych IPSEC może być konieczne również.  
  
 Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).