---
title: Zabezpieczenia debugera | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95d637585a08089432c8ed054b535c3e56fc9c18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-security"></a>Zabezpieczenia debugera
Możliwość debugowania inny proces zapewnia bardzo szeroki uprawnień, które nie w przeciwnym razie będzie, szczególnie w przypadku debugowania zdalnego. Debuger złośliwego może spowodować rozległe zniszczenia na maszynie debugowany.  
  
 Jednak wielu deweloperów nie należy pamiętać, że zagrożenia zabezpieczeń również może przepływać w odwrotnym kierunku. Istnieje możliwość, że złośliwy kod obiektu debugowanego procesu w celu zagrozić bezpieczeństwu debugowania maszyny: liczba które musi być chroniony przed lukami w zabezpieczeniach.  
  
## <a name="security-best-practices"></a>Najlepsze praktyki w zakresie zabezpieczeń  
 Brak relacji nawiązywanie niejawnych relacji zaufania między kod, który jest debugowany i debuger. Jeśli chcesz debugować coś, należy także chce go uruchomić. Mierzenie jest, że użytkownik musi być zaufania jest debugowany. Jeśli nie ufasz, następnie należy nie debugowania go lub powinny debugowania go z komputera, który można pozwolić sobie na zagrozić i w izolowanym środowisku.  
  
 Aby ograniczyć potencjalny obszar ataków, debugowanie powinno zostać wyłączone na maszynach w środowisku produkcyjnym. Z tego samego powodu powinien nigdy nie być włączone debugowanie nieskończoność.  
  
### <a name="managed-debugging-security"></a>Zabezpieczenia debugowania zarządzanego  
 Poniżej przedstawiono ogólne zalecenia mające zastosowanie do wszystkich zarządzanych debugowania.  
  
-   Należy zachować ostrożność podczas dołączania do procesu niezaufany użytkownik: po wykonaniu tej założono jest zaufane. Przy próbie dołączyć do procesu niezaufany użytkownik zabezpieczeń ostrzeżenie potwierdzenia — okno dialogowe zostanie wyświetlony pytaniem, czy chcesz dołączyć do procesu. "Zaufanych użytkowników" należy dołączyć, i zbiór użytkowników standardowych często zdefiniowane na maszynach, które mają zainstalowany, takich jak w programie .NET Framework **aspnet**, **localsystem**, **usługisieciowej**, i **Usługa lokalna**. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: dołączanie do procesu należących do niezaufanych użytkownika może być niebezpieczne. Jeśli nie wiesz, poniższe informacje wyglądają podejrzanie, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
-   Należy zachować ostrożność podczas pobierania projektu od Internetu oraz załadowanie go do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jest to bardzo ryzykowne czy nawet bez debugowania. Po wykonaniu tej czynności są przy założeniu projekt i kod, który zawiera są zaufane.  
  
 Aby uzyskać więcej informacji, zobacz [debugowania kodu zarządzanego](../debugger/debugging-managed-code.md).  
  
### <a name="remote-debugging-security"></a>Zdalnego debugowania zabezpieczeń  
 Debugowanie lokalne jest zwykle bezpieczniejsze niż debugowanie zdalne. Debugowanie zdalne zwiększa obszaru powierzchni całkowity może sondowany.  
  
 Visual Studio zdalne debugowanie Monitor (msvsmon.exe) jest używany w zdalnego debugowania i istnieje kilka zaleceń dotyczących zabezpieczeń dla jego konfigurowania. Preferowany sposób, aby skonfigurować tryb uwierzytelniania jest uwierzytelnianie systemu Windows, ponieważ tryb bez uwierzytelniania jest niebezpieczne.  
  
 ![Okno dialogowe błędu](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")  
  
 Podczas korzystania z trybu uwierzytelniania systemu Windows, należy pamiętać, że przyznanie niezaufanych uprawnień do nawiązania połączenia polecenia msvsmon jest niebezpieczne, ponieważ użytkownik otrzymuje swoje uprawnienia na komputerze...  
  
 Nieznany procesu na komputerze zdalnym nie debugowania: istnieje potencjalne luki, który może mieć wpływ na komputerze, na którym działa debugera lub które mogą naruszyć msvsmon.exe, Visual Studio Monitor debugera zdalnego. Jeśli musisz debugować absolutnie nieznany proces, spróbuj lokalnie debugowania i korzystanie z zapory, aby zachować wszystkie potencjalne zagrożenia zlokalizowane.  
  
 Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).  
  
### <a name="web-services-debugging-security"></a>Zabezpieczenia debugowania usług sieci Web  
 Bezpieczniej debugowania lokalnie, ale ponieważ prawdopodobnie nie masz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane na serwerze sieci web, debugowania lokalnego może nie być praktyczne. Ogólnie rzecz biorąc debugowanie usług sieci Web jest wykonywane zdalnie, z wyjątkiem podczas opracowywania, więc zalecenia dotyczące zabezpieczeń debugowania zdalnego dotyczą także debugowanie usług sieci Web. Poniżej przedstawiono dodatkowe najlepsze rozwiązania. Aby uzyskać więcej informacji, zobacz [debugowania usług XML sieci Web](http://msdn.microsoft.com/en-us/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).  
  
-   Nie należy włączać debugowania na serwerze sieci Web, którego bezpieczeństwo zostało naruszone.  
  
-   Upewnij się, że wiesz, że serwer sieci Web są bezpieczne, przed jej debugowanie. Jeśli nie masz pewności, że jest bezpieczne, nie debugować go.  
  
-   Należy zachować szczególną ostrożność w przypadku debugowania usługi sieci Web, która jest widoczna w Internecie.  
  
### <a name="external-components"></a>Składniki zewnętrzne  
 Należy pamiętać o stanu zaufania zewnętrzne składniki, które wchodzi w interakcję z programem, zwłaszcza, jeśli nie pisanie kodu. Wziąć pod uwagę składników który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub może używać debugera.  
  
### <a name="symbols-and-source-code"></a>Symbole i kodu źródłowego  
 Dwa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi, które wymagają planowania zabezpieczeń są następujące:  
  
-   Serwer źródłowy zapewnia wersji kodu źródłowego z repozytorium kodu źródłowego. Jest przydatne, jeśli nie masz bieżącej wersji programu kodu źródłowego. [Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufaną komendę](../debugger/security-warning-debugger-must-execute-untrusted-command.md).  
  
-   Symbol serwera, który jest używany do dostarczania symbole potrzebne do debugowania awarii podczas wywołania systemu.  
  
 Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli nie wiesz, poniższe informacje wyglądają podejrzanie, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufaną komendę](../debugger/security-warning-debugger-must-execute-untrusted-command.md)