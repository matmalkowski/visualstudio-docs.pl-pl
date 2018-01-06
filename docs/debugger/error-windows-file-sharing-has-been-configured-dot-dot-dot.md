---
title: "Błąd: Udostępnianie plików systemu Windows została skonfigurowana... | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7bbd8d00a6939030068bbe6dd565fb57393d18be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Błąd: Udostępnianie plików systemu Windows zostało skonfigurowano...
Udostępnianie plików systemu Windows została skonfigurowana, dzięki czemu będą łączyć się z komputerem zdalnym przy użyciu innej nazwy użytkownika. Jest to niezgodne z funkcją debugowania zdalnego  
  
 Aby połączyć się z komputerem zdalnym przy użyciu innej nazwy użytkownika skonfigurowano bieżącego pliku konfiguracji do udostępniania. Debugowanie zdalne nie jest możliwe w tym scenariuszu.  
  
 Aby rozwiązać ten problem, zaloguj się na komputerze przy użyciu nazwy konta lub zmienić udostępnianie plików do używania nazwy konta, które debugowania w obszarze.  
  
 Jeśli chcesz się połączyć z komputerem zdalnym przy użyciu tej nazwy użytkownika, należy najpierw odłączyć z komputera zdalnego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zaloguj się na komputerze lokalnym komputerze, na którym debugowania, przy użyciu nazwy konta.  
  
     —lub—  
  
     . Zakończyć połączenie z komputerem zdalnym, a następnie ponownie skonfigurować udostępnianie plików nawiązać połączenia z innego komputera przy użyciu nazwy konta:  
  
    1.  Na **Start** menu wskaż **Akcesoria**, a następnie kliknij przycisk **wiersza polecenia**.  
  
    2.  W wierszu polecenia systemu Windows wpisz:  
  
         `net use /delete computer_name`  
  
    3.  Zmiany ustawień udostępniania plików przy użyciu dowolnej z metod opisanych w Pomocy systemu Windows.