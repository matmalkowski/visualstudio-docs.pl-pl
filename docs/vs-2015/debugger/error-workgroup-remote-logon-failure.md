---
title: 'Błąd: Błąd logowania grupy roboczej zdalnego | Dokumentacja firmy Microsoft'
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
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46d7043eba9d357f410d1a05655870ef5e1121d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676722"
---
# <a name="error-workgroup-remote-logon-failure"></a>Błąd: Błąd zdalnego logowania grupy roboczej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [błąd: zdalny błąd logowania grupy roboczej](https://docs.microsoft.com/visualstudio/debugger/error-workgroup-remote-logon-failure).  
  
Odczytuje ten błąd:  
  
 Błąd logowania: Nieznana nazwa użytkownika lub nieprawidłowe hasło  
  
 **Przyczyna**  
  
 Ten błąd może wystąpić podczas próby nawiązania połączenia z maszyną zdalną, gdy debugowany na komputerze w grupie roboczej. Możliwe przyczyny:  
  
-   Nie ma konta przy użyciu nazwy i hasła na komputerze zdalnym.  
  
-   Jeśli komputer z programem Visual Studio i komputer zdalny znajdują się w grupach roboczych, ten błąd może wystąpić z powodu domyślnie **zasady zabezpieczeń lokalnych** ustawienie na komputerze zdalnym. Ustawieniem domyślnym dla **zasady zabezpieczeń lokalnych** jest ustawienie **tylko Gość — Uwierzytelnij jako gościa, użytkownicy lokalni**. Do debugowania w tej konfiguracji, należy zmienić ustawienie na komputerze zdalnym, aby **klasycznego — uwierzytelnianie użytkowników lokalnych, jak samodzielnie**.  
  
> [!NOTE]
>  Musi być administratorem, aby wykonywać następujące zadania.  
  
### <a name="to-open-the-local-security-policy-window"></a>Aby otworzyć okno Zasady zabezpieczeń lokalnych  
  
1.  Rozpocznij **secpol.msc** przystawkę Microsoft Management Console. W polu wyszukiwania Windows, pole Uruchom Windows lub w wierszu polecenia, wpisz secpol.msc.  
  
### <a name="to-add-user-rights-assignments"></a>Aby dodać przypisania praw użytkownika  
  
1.  Otwórz lokalnej  
  
2.  Otwórz **zasady zabezpieczeń lokalnych** okna.  
  
3.  Rozwiń **zasady lokalne** folderu.  
  
4.  Kliknij przycisk **Przypisywanie praw użytkownika**.  
  
5.  W **zasad** kolumny, kliknij dwukrotnie **debugowanie programów** Aby przejrzeć bieżące przypisania zasad grupy lokalnej w **Ustawianie zasad zabezpieczeń lokalnych** okno dialogowe.  
  
     ![Prawa użytkownika zasady zabezpieczeń lokalnych](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Aby dodać nowych użytkowników, kliknij **Dodaj użytkownika lub grupę** przycisku.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Aby zmienić udostępnianie i Model zabezpieczeń  
  
1.  Otwórz **zasady zabezpieczeń lokalnych** okna.  
  
2.  Rozwiń **zasady lokalne** folderu.  
  
3.  Kliknij przycisk **opcje zabezpieczeń**.  
  
4.  W **zasad** kolumny, kliknij dwukrotnie **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych**.  
  
5.  W **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** okna dialogowego pola, zmień wartość na **klasycznego — uwierzytelnianie użytkowników lokalnych, jak samodzielnie** i kliknij przycisk **Zastosuj**przycisku.  
  
     ![Opcje zabezpieczeń zasady zabezpieczeń lokalnych](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



