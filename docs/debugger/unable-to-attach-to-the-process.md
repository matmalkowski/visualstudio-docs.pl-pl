---
title: "Nie można dołączyć do procesu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 691d0352b327dd2665b3a6daf22b3542929d3ca3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="unable-to-attach-to-the-process"></a>Nie można dołączyć do procesu
Nie można dołączyć do procesu. Składnik debugera na serwerze otrzymał odmowa dostępu podczas nawiązywania połączenia z tego komputera.  
  
 Istnieją dwa typowe scenariusze, które są przyczyną tego błędu:  
  
 **Scenariusz 1:** maszyny A systemem Windows XP. Komputer B działa system Windows Server 2003. Rejestr na komputerze B zawiera następujące wartości DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Użytkownik 1 uruchamia sesji serwera terminali (sesji 1) na komputerze B i zaczyna się aplikacją zarządzaną w tej sesji.  
  
 Użytkownik 2, który jest administratorem na obu komputerach, jest rejestrowane na komputerze A. Z tego miejsca użytkownik próbuje dołączanie do aplikacji działających w sesji 1 na komputerze B.  
  
 **Scenariusz 2:** jeden użytkownik jest zalogowany na dwóch komputerach, A i B, w tej samej grupie roboczej, przy użyciu tego samego hasła na obu komputerach. Debuger jest uruchomiony na komputerze A, a próby dołączenia zarządzanej aplikacji uruchomionych na maszynie B. maszyny, A ma **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** ustawioną **gościa**.  
  
### <a name="to-solve-scenario-1"></a>Aby rozwiązać scenariusz 1  
  
-   Uruchom debuger i zarządzanych aplikacji w ramach tej samej nazwy konta użytkownika i hasła.  
  
### <a name="to-solve-scenario-2"></a>Aby rozwiązać Scenariusz 2  
  
1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
2.  W Panelu sterowania, kliknij dwukrotnie **narzędzia administracyjne**.  
  
3.  W oknie Narzędzia administracyjne kliknij dwukrotnie **zasady zabezpieczeń lokalnych**.  
  
4.  W oknie Zasady zabezpieczeń lokalnych, wybierz **zasady lokalne**.  
  
5.  W **zasady** kolumny, kliknij dwukrotnie **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych**.  
  
6.  W **dostęp sieciowy: udostępnianie i model zabezpieczeń dla kont lokalnych** okno dialogowe Zmień ustawienia zabezpieczeń lokalnych, aby **klasycznego**i kliknij przycisk **OK**.  
  
    > [!CAUTION]
    >  Zmiana klasycznego modelu zabezpieczeń może spowodować nieoczekiwane dostęp do udostępnionych plików i składników DCOM components. Jeśli wprowadzisz tej zmiany, użytkownik zdalny można uwierzytelniać z Twojego konta użytkownika lokalnego, a nie gościa. Jeśli zdalnego użytkownika spełnia swoją nazwę użytkownika i hasło, ten użytkownik będzie można uzyskać dostępu do dowolnego folderu lub udostępnione limit obiektu modelu DCOM. Użycie tego modelu zabezpieczeń, upewnij się że wszystkie konta użytkowników na komputerze silnych haseł lub skonfigurować wyspę sieci izolowanej do debugowania i debugowania maszyny, aby uniemożliwić nieautoryzowany dostęp.  
  
7.  Zamknij wszystkie okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)