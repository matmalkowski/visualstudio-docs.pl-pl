---
title: 'Błąd: Zapora na komputerze lokalnym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: 98badb458be79e17684c5ce134813d25b6605352
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Nie skonfigurowano Zapora połączenia internetowego na komputerze lokalnym komputerze, na którym uruchamiasz program Visual Studio, w celu zezwolenia na debugowanie zdalne. Zarządzanym lub macierzystym zdalne debugowanie z domyślny transport, należy otworzyć port TCP 135 dla ruchu modelu DCOM. Udostępnianie plików i drukarek muszą być otwarte i devenv.exe musi zostać dodany do listy wyjątków. Otwieranie portów niektórych IPSEC może być konieczne również.  
  
 Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).