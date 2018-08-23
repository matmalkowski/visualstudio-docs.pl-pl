---
title: 'Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania | Dokumentacja firmy Microsoft'
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
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7de8aaba3abf4ef7c767ed549b5454b1599e808d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681902"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: wykonanie Transact-SQL zakończyło się bez debugowania](https://docs.microsoft.com/visualstudio/debugger/error-transact-sql-execution-ended-without-debugging).  
  
Ten błąd występuje podczas próby debugowania języka Transact-SQL lub procedury SQLCLR i debuger nie odbiera komunikaty debugowania z programu SQL Server.  
  
 Może to być ze względu na problemy z siecią lub problemy w programie SQL Server, ale najbardziej prawdopodobną przyczyną jest problem z uprawnieniami.  
  
 Zaangażowanych dwa konta:  
  
-   Konto aplikacji znajduje się konto użytkownika, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] działa jako.  
  
-   Konto połączenia jest to tożsamość używana do nawiązywania połączeń z programem SQL Server. To nie jest zawsze taki sam jak tożsamość, która Visual Studio działa tak, jakby połączenie za pomocą uwierzytelniania SQL.  
  
 Debugowanie SQL wymaga, aby konto aplikacji musi odpowiadać kontu połączenia lub być sysadmin.  
  
 Jeśli używasz identyfikatora logowania SQL, takich jak Ameryka Południowa konta aplikacji musi być Instalatora na serwerze SQL, administrator systemu. Domyślnie administratorzy na komputerze program SQL server jest uruchomiony są głównym programu SQL Server.  
  
 Aby naprawić ten błąd, konieczne może być:  
  
-   Sprawdź ustawienia uprawnień. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie uprawnień programu SQL Server dla debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Upewnij się, że debugowanie SQL, jeśli skonfigurowane prawidłowo.  
  
-   Zapoznaj się z administratorem sieci lub bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie debugowania SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Porady: Ustawianie uprawnień programu SQL Server do debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



