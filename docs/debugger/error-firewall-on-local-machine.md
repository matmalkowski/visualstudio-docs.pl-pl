---
title: "Błąd: Zapora na komputerze lokalnym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0eb7158fe2274fbe8707a147fe63a0937689d23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="error-firewall-on-local-machine"></a>Błąd: Zapora na zdalnym komputerze
Nie skonfigurowano Zapora połączenia internetowego na komputerze lokalnym komputerze, na którym uruchamiasz program Visual Studio, w celu zezwolenia na debugowanie zdalne. Zarządzanym lub macierzystym zdalne debugowanie z domyślny transport, należy otworzyć port TCP 135 dla ruchu modelu DCOM. Udostępnianie plików i drukarek muszą być otwarte i devenv.exe musi zostać dodany do listy wyjątków. Otwieranie portów niektórych IPSEC może być konieczne również.  
  
 Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).