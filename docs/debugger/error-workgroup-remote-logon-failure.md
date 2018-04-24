---
title: 'Błąd: Błąd logowania zdalnego grupy roboczej | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60cee4e6bdb4ebab925325695eb9ad6813929879
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="error-workgroup-remote-logon-failure"></a>Błąd: Błąd zdalnego logowania grupy roboczej
Odczytuje ten błąd:  
  
 Błąd logowania: Nieznana nazwa użytkownika lub nieprawidłowe hasło  
  
 **Przyczyna**  
  
 Ten błąd może wystąpić podczas debugowania na komputerze w grupie roboczej, a następnie spróbuj połączyć się z komputerem zdalnym. Możliwe przyczyny:  
  
-   Brak żadnego konta z zgodną nazwę i hasło na komputerze zdalnym.  
  
-   Jeśli zarówno na komputerze programu Visual Studio, jak i komputer zdalny znajdują się w grupach roboczych, ten błąd może wystąpić z powodu domyślnie **zasady zabezpieczeń lokalnych** ustawienie na komputerze zdalnym. Ustawieniem domyślnym dla **zasady zabezpieczeń lokalnych** jest ustawienie **tylko Gość — użytkownicy lokalni Uwierzytelnij jako gościa**. Do debugowania na tej instalacji, należy zmienić ustawienie na komputerze zdalnym, aby **Klasyczny - uwierzytelnianie użytkowników lokalnych siebie**.  
  
> [!NOTE]
>  Musi być administratorem, aby wykonać poniższe zadania.  
  
### <a name="to-open-the-local-security-policy-window"></a>Aby otworzyć okno Zasady zabezpieczeń lokalnych  
  
1.  Uruchom **secpol.msc** przystawki programu Microsoft Management Console. Wpisz secpol.msc wyszukiwania systemu Windows, pole Uruchom systemu Windows lub w wierszu polecenia.  
  
### <a name="to-add-user-rights-assignments"></a>Aby dodać przypisania praw użytkownika  
  
1.  Otwórz **zasady zabezpieczeń lokalnych** okna.  
  
2.  Rozwiń węzeł **zasady lokalne** folderu.  
  
3.  Kliknij przycisk **Przypisywanie praw użytkownika**.  
  
4.  W **zasad** kolumny, kliknij dwukrotnie **debugowanie programów** Aby wyświetlić bieżące przypisania zasad grupy lokalnej w **zasady zabezpieczeń lokalnych** okno dialogowe.  
  
     ![Prawa użytkownika zasady zabezpieczeń lokalnych](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
5.  Do dodawania nowych użytkowników, kliknij przycisk **Dodaj użytkownika lub grupę** przycisku.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Aby zmienić udostępnianie i Model zabezpieczeń  
  
1.  Otwórz **zasady zabezpieczeń lokalnych** okna.  
  
2.  Rozwiń węzeł **zasady lokalne** folderu.  
  
3.  Kliknij przycisk **opcje zabezpieczeń**.  
  
4.  W **zasad** kolumny, kliknij dwukrotnie **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych**.  
  
5.  W **dostępu do sieci: udostępnianie i model zabezpieczeń dla kont lokalnych** okna dialogowego Zmień wartość na **Klasyczny - uwierzytelnianie użytkowników lokalnych siebie** i kliknij przycisk **Zastosuj**przycisku.  
  
     ![Opcje zabezpieczeń zasady zabezpieczeń lokalnych](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)