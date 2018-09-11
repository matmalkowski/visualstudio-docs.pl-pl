---
title: 'Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
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
ms.openlocfilehash: 5e6ae81608ee476e3748fde6830dfaa11c119f7a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283135"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania
Ten błąd występuje podczas próby debugowania języka Transact-SQL lub procedury SQLCLR i debuger nie odbiera komunikaty debugowania z programu SQL Server.  
  
 Może to być ze względu na problemy z siecią lub problemy w programie SQL Server, ale najbardziej prawdopodobną przyczyną jest problem z uprawnieniami.  
  
 Zaangażowanych dwa konta:  
  
-   Konto aplikacji znajduje się konto użytkownika, który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] działa jako.  
  
-   Konto połączenia jest to tożsamość używana do nawiązywania połączeń z programem SQL Server. To nie jest zawsze taki sam jak tożsamość, która Visual Studio działa tak, jakby połączenie za pomocą uwierzytelniania SQL.  
  
 Debugowanie SQL wymaga, aby konto aplikacji musi odpowiadać kontu połączenia lub być sysadmin.  
  
 Jeśli używasz identyfikatora logowania SQL, takich jak Ameryka Południowa konta aplikacji musi być Instalatora na serwerze SQL, administrator systemu. Domyślnie administratorzy na komputerze program SQL server jest uruchomiony są głównym programu SQL Server.  
  
 Aby naprawić ten błąd, konieczne może być:  
  
-   Sprawdź ustawienia uprawnień. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie uprawnień programu SQL Server dla debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Upewnij się, że debugowanie SQL, jeśli skonfigurowane prawidłowo.  
  
-   Zapoznaj się z administratorem sieci lub bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie debugowania SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))   
 [Porady: Ustawianie uprawnień programu SQL Server do debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)