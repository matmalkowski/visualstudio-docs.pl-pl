---
title: 'Błąd: SQL można&#39;t znaleźć SSDEBUGPS | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f263d76667eb197d85a99ba06a45fc08e2f4d0d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Błąd: SQL można&#39;t znaleźć SSDEBUGPS

Biblioteka SSDEBUGPS.dll jest składnikiem hosta debugowanie serwera SQL.

Ten błąd występuje, gdy chcesz rozpocząć debugowania i wskazuje, że określony plik nie jest obecny w [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny. Możliwe przyczyny to nigdy nie uruchomiono Instalatora albo zdalnego debugowania, lub że jakiś sposób ten plik został usunięty.

Istnieją dwa sposoby, aby rozwiązać ten problem: ponownie instalację zdalnego debugowania i przez kopiowanie plików na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny.

Aby ponownie uruchomić Instalatora zdalnego debugowania, postępuj zgodnie z instrukcjami w [zdalnego debugowania](../debugger/remote-debugging.md).

Jeśli kopia Biblioteka ssdebugps.dll może zlokalizować, możesz skopiować go na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny. Jeśli istnieje, plik zostanie w \Program Files\ katalogu wspólnej Files\Microsoft Shared\SQL debugowania. Można go znaleźć na innym [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] komputera, lub na komputerze, na którym został zainstalowany program Visual Studio 2005.

Aby skopiować Biblioteka SSDEBUGPS.dll na komputerze programu SQL Server 2005:

1. Skopiuj plik do katalogu z taką samą nazwę i ścieżkę na [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] maszyny.

2. Zarejestruj go przez otwarcie **wiersza polecenia**i uruchom następujące polecenie:

    ```
    regsrv32 ssdebugps.dll
    ```