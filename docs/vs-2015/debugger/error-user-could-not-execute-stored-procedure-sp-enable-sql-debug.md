---
title: 'Błąd: Użytkownik może nie wykonać procedury przechowywanej sp_enable_sql_debug | Dokumentacja firmy Microsoft'
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
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 172b7b7870e3bf35b2cda5fc04a894b6c52c70d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680617"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Błąd: użytkownik nie mógł wykonać procedury przechowywanej sp_enable_sql_debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: użytkownik może nie wykonać procedury przechowywanej sp_enable_sql_debug](https://docs.microsoft.com/visualstudio/debugger/error-user-could-not-execute-stored-procedure-sp-enable-sql-debug).  
  
Procedury przechowywanej sp_enable_sql_debug nie można wykonać na serwerze. Może to być spowodowane:  
  
-   Problem z połączeniem. Musisz mieć stabilne połączenie z serwerem.  
  
-   Brak wystarczających uprawnień na serwerze. Do debugowania w programie SQL Server 2005, zarówno w przypadku konta, programem Visual Studio, jak i konto używane do łączenia się z serwerem SQL muszą być członkami roli sysadmin. Konto używane do łączenia się z serwerem SQL jest kontem użytkownika Windows (Jeśli używasz uwierzytelniania Windows) lub konto z Identyfikatorem użytkownika i hasło (Jeśli używasz uwierzytelniania SQL).  
  
 Aby uzyskać więcej informacji, zobacz [porady: Ustawianie uprawnień programu SQL Server dla debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Ustawianie uprawnień programu SQL Server do debugowania](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Konfigurowanie debugowania SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)



