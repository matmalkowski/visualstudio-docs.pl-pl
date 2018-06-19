---
title: 'Błąd: Zapora na komputerze lokalnym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: e85c97d5950f71d9552bba944450603e47a5ab49
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472870"
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Nie skonfigurowano Zapora połączenia internetowego na komputerze lokalnym komputerze, na którym uruchamiasz program Visual Studio, w celu zezwolenia na debugowanie zdalne. Zarządzanym lub macierzystym zdalne debugowanie z domyślny transport, należy otworzyć port TCP 135 dla ruchu modelu DCOM. Udostępnianie plików i drukarek muszą być otwarte i devenv.exe musi zostać dodany do listy wyjątków. Otwieranie portów niektórych IPSEC może być konieczne również.  
  
 Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).