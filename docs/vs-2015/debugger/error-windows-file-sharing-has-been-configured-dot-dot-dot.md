---
title: 'Błąd: Udostępnianie plików Windows zostało skonfigurowane... | Dokumentacja firmy Microsoft'
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
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fc4d3fb02b1c7c9d5003f82fbe42be73c93d6eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677897"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Błąd: Udostępnianie plików systemu Windows zostało skonfigurowano...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: udostępnianie plików Windows zostało skonfigurowane... ](https://docs.microsoft.com/visualstudio/debugger/error-windows-file-sharing-has-been-configured-dot-dot-dot).  
  
Udostępnianie plików Windows został skonfigurowany, tak aby połączy się z komputerem zdalnym przy użyciu innej nazwy użytkownika. Jest to niezgodne z funkcją debugowania zdalnego  
  
 Bieżący plik Konfiguracja udostępniania jest skonfigurowany do łączenia się z komputerem zdalnym przy użyciu innej nazwy użytkownika. Zdalne debugowanie nie jest możliwe, w tym scenariuszu.  
  
 Aby rozwiązać ten problem, zaloguj się na komputerze przy użyciu nazwy konta lub zmienić udostępniania plików do używania nazwy konta, który debugujesz w obszarze.  
  
 Jeśli chcesz się połączyć z komputerem zdalnym przy użyciu tej nazwy użytkownika, musisz najpierw odłączyć z komputera zdalnego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zaloguj się na komputerze lokalnym komputera, który debugujesz, przy użyciu nazwy konta.  
  
     —lub—  
  
     . Rozłącz z komputera zdalnego, a następnie ponownie skonfiguruj Udostępnianie plików, połączyć się z innego komputera przy użyciu nazwy konta:  
  
    1.  Na **Start** menu wskaż **Akcesoria**, a następnie kliknij przycisk **polecenia**.  
  
    2.  W wierszu polecenia Windows wpisz:  
  
         `net use /delete computer_name`  
  
    3.  Zmień ustawienia udostępniania plików przy użyciu dowolnej z metod opisanych w Pomocy Windows.



