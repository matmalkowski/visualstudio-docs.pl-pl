---
title: "Błąd: Użytkownik może nie wykonać procedury przechowywanej sp_enable_sql_debug | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ab29925b12bfb14ba8f37d371c30aa6f312ea15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Błąd: użytkownik nie mógł wykonać procedury przechowywanej sp_enable_sql_debug
Procedury przechowywanej sp_enable_sql_debug nie można wykonać na serwerze. Może to być spowodowane:  
  
-   Problem z połączeniem. Musisz mieć stabilna połączenia z serwerem.  
  
-   Brak wystarczających uprawnień na serwerze. Do debugowania w programie SQL Server 2005, zarówno w przypadku konta, na którym działa program Visual Studio, jak i konto używane do połączenia z serwerem SQL musi być członkowie roli sysadmin. Konto używane do połączenia z serwerem SQL jest konto użytkownika systemu Windows (Jeśli używasz uwierzytelniania systemu Windows) lub konto z identyfikator użytkownika i hasło (Jeśli używane jest uwierzytelnianie SQL).  
  
 Aby uzyskać więcej informacji, zobacz [porady: Ustawianie uprawnień serwera SQL dla debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Ustawianie uprawnień programu SQL Server do debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Konfigurowanie debugowania SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)