---
title: "Błąd: Debugowanie nie powiodło się, ponieważ nie włączono zintegrowanego uwierzytelniania systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords: debugger, Web application errors
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d3d66a2892378f04061907e383965c6c02096bf1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Błąd: debugowanie nie powiodło się ponieważ zintegrowane uwierzytelnianie systemu Windows nie jest włączone
Uwierzytelnianie użytkownika, który debugowania żądanego uniemożliwiły błąd uwierzytelniania. Taka sytuacja może wystąpić przy próbie wkroczyć do aplikacji sieci Web lub usługi XML sieci Web. Jedną z przyczyn tego błędu jest tym zintegrowane uwierzytelnianie systemu Windows nie jest włączona. Aby go włączyć, postępuj zgodnie z instrukcjami "Aby włączyć zintegrowane uwierzytelnianie systemu Windows".  
  
 Jeśli ten błąd nadal występuje ma włączone zintegrowane uwierzytelnianie systemu Windows, jest to możliwe, że ten błąd jest spowodowany **szyfrowanego uwierzytelniania dla serwerów domeny systemu Windows** jest włączona. W takiej sytuacji należy skontaktować się z administratorem sieci.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Aby włączyć zintegrowane uwierzytelnianie systemu Windows  
  
1.  Zaloguj się na serwerze sieci Web przy użyciu konta administratora.  
  
2.  Kliknij przycisk **Start** , a następnie kliknij przycisk **Panelu sterowania**.  
  
3.  W **Panelu sterowania**, kliknij dwukrotnie **narzędzia administracyjne**.  
  
4.  Kliknij dwukrotnie **Internetowe usługi informacyjne**.  
  
5.  Kliknij węzeł serwera sieci Web.  
  
     A **witryn sieci Web** zostanie otwarty folder poniżej nazwę serwera.  
  
6.  Możesz skonfigurować uwierzytelnianie dla wszystkich witryn sieci Web lub dla poszczególnych witryn sieci Web. Aby skonfigurować uwierzytelnianie dla wszystkich witryn sieci Web, kliknij prawym przyciskiem myszy **witryn sieci Web** folder, a następnie kliknij przycisk **właściwości**. Aby skonfigurować uwierzytelnianie witryny sieci Web, otwórz **witryn sieci Web** folderu, kliknij prawym przyciskiem myszy witryny sieci Web, a następnie kliknij przycisk **właściwości**.  
  
     **Właściwości** zostanie wyświetlone okno dialogowe.  
  
7.  Kliknij przycisk **zabezpieczenia katalogu** kartę.  
  
8.  W **dostęp anonimowy i uwierzytelniania kontrola** kliknij **Edytuj**.  
  
     **Metod uwierzytelniania** zostanie wyświetlone okno dialogowe.  
  
9. W obszarze **dostęp uwierzytelniany**, wybierz pozycję **zintegrowanego uwierzytelniania systemu Windows**.  
  
10. Kliknij przycisk **OK** zamknąć **metod uwierzytelniania** okno dialogowe.  
  
11. Kliknij przycisk **OK** zamknąć **właściwości** okno dialogowe.  
  
12. Zamknij **Internetowe usługi informacyjne** okna.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Aby włączyć zintegrowane uwierzytelnianie systemu Windows w systemie Windows Vista/usług IIS 7  
  
1.  Zaloguj się na serwerze sieci Web przy użyciu konta administratora.  
  
2.  Włącz uwierzytelnianie systemu Windows oraz zgodność z narzędziami zarządzania II6, jeśli użytkownik nie wcześniej zostało to zrobione, wykonaj następujące czynności:  
  
    1.  Kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania** , a następnie kliknij przycisk **programy**.  
  
    2.  W obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.  
  
         Okno dialogowe kontroli dostępu użytkownika pojawia się i wyświetli monit o podanie uprawnień kontynuować.  
  
    3.  Kliknij przycisk **Kontynuuj**.  
  
         Zostanie wyświetlone okno dialogowe funkcje systemu Windows.  
  
    4.  Na liście funkcji Rozwiń **Internetowe usługi informacyjne** węzła.  
  
    5.  W obszarze **Internetowe usługi informacyjne**, rozwiń węzeł **usługi sieci World Wide Web** węzła.  
  
    6.  W obszarze **usługi sieci World Wide Web**, kliknij przycisk **zabezpieczeń**.  
  
    7.  Kliknij przycisk **uwierzytelniania systemu Windows**.  
  
    8.  W obszarze **Internetowe usługi informacyjne**, rozwiń węzeł **narzędzia zarządzania siecią Web** węzła.  
  
    9. W obszarze **narzędzia zarządzania siecią Web**, rozwiń węzeł **zgodność z narzędziami zarządzania usług IIS 6** , a następnie wybierz węzeł **metabazy usług IIS 6 i IIS 6 Configuration Compatibility** pole wyboru.  
  
    10. W obszarze **narzędzia zarządzania siecią Web**, wybierz pozycję **Konsola zarządzania usługami IIS** i kliknij przycisk **OK.**  
  
    11. Uruchom ponownie komputer, aby te zmiany zaczęły obowiązywać.  
  
3.  Kliknij przycisk **Start** , a następnie kliknij przycisk **Panelu sterowania**.  
  
4.  Kliknij przycisk **Klasyczny**, a następnie kliknij dwukrotnie **narzędzia administracyjne**.  
  
5.  W **nazwa** kolumny i kliknij dwukrotnie **Internet Information Services (IIS) Manager**.  
  
6.  W **połączeń** kolumny, rozwiń węzeł serwera.  
  
     A **witryn sieci Web** zostanie otwarty folder poniżej nazwę serwera.  
  
7.  Rozwiń węzeł **witryn sieci Web** węzeł i kliknij witrynę sieci Web, dla której chcesz włączyć zintegrowane uwierzytelnianie systemu Windows.  
  
8.  Tytuł w środkowym okienku zmienia nazwę wybranej witryny sieci Web. W tym okienku w obszarze **IIS** pozycji, kliknij dwukrotnie **uwierzytelniania**.  
  
     Zmiany tytułu okienka **uwierzytelniania**.  
  
9. W **uwierzytelniania** okienko w **nazwa** kolumny, kliknij prawym przyciskiem myszy **uwierzytelniania systemu Windows** , a następnie kliknij przycisk **włączyć**.  
  
10. Zamknij **Internet Information Services (IIS) Manager** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Uwierzytelnianie szyfrowane firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Uruchamianie aplikacji sieci Web w systemie Windows Vista z usługami IIS 7.0 i programu Visual Studio](http://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)