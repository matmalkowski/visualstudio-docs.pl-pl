---
title: Uruchamianie programu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5762b59a52cce2bf918c50630bbf82e176d9e82f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="launching-a-program"></a>Uruchamianie programu
Użytkownicy, którzy chcą debugowania programu można nacisnąć klawisz F5, aby uruchomić debugera z IDE. To rozpoczyna się szereg zdarzeń, które powoduje ostatecznie IDE nawiązywania aparat debugowania (DE), który z kolei jest połączony, lub dołączony do programu w następujący sposób:  
  
1.  Najpierw IDE wywołuje pakiet projektu można pobrać ustawień debugowania aktywnego projektu tego rozwiązania. Ustawienia obejmują katalog początkowy, zmienne środowiskowe, port, w którym program będzie uruchamiany i DE używać do tworzenia programu, jeśli określony. Te ustawienia są przekazywane do pakietu debugowania.  
  
2.  Jeśli określono DE, DE wymaga systemu operacyjnego, aby uruchomić program. Uruchamianie programu, w wyniku środowisko wykonawcze programu została załadowana. Na przykład jeśli program został napisany w MSIL, środowisko uruchomieniowe języka wspólnego wywoływane w celu uruchomienia programu.  
  
     —lub—  
  
     Jeśli nie określono DE, port wymaga systemu operacyjnego można uruchomić programu, co powoduje, że środowisko wykonawcze programu do załadowania.  
  
    > [!NOTE]
    >  Jeśli URZ służy do uruchamiania programu, istnieje prawdopodobieństwo, że tego samego DE zostanie dołączona do programu.  
  
3.  W zależności od tego, czy DE lub port uruchamiany program DE lub środowisku następnie tworzy opis programu lub węzeł i powiadamia portu, na którym działa program.  
  
    > [!NOTE]
    >  Zalecane jest, środowisko wykonawcze utworzyć węzła programu, ponieważ lekkie reprezentację program, który może być debugowany jest węzeł programu. Nie istnieje potrzeba ładowania całego DE podobnie można utworzyć ani zarejestrować węzła programu. Jeśli DE jest przeznaczony do uruchamiania w procesie IDE, ale IDE nie jest uruchomiona, musi istnieć składnik, który można dodać węzła programu do portu.  
  
 Nowo utworzony program, oraz wszystkie inne programy powiązane lub niezwiązanych ze sobą, uruchomienia lub powiązany z tym samym IDE, tworzenia sesji debugowania.  
  
 Programistycznie, gdy użytkownik najpierw naciśnie **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]przez pakiet debugowania wywołuje pakiet projektu (który jest skojarzony z typem program uruchamiany) za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metodę, która z kolei wypełnia <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> struktury z ustawieniami debugowania aktywnego projektu tego rozwiązania. Ta struktura jest przekazywane z powrotem do pakietu debugowania poprzez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> metody. Pakiet debugowania tworzy następnie Menedżer debugowania sesji (SDM), co powoduje uruchomienie programu aparatami debugowania debugowany i wszystkie skojarzone.  
  
 Jeden z argumentów przekazanych do SDM jest identyfikatorem GUID DE ma być używany do uruchomienia programu.  
  
 Jeśli nie jest identyfikatorem GUID DE `GUID_NULL`, SDM wspólnie tworzy DE, a następnie wywołuje jego [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodę, aby uruchomić program. Na przykład, jeśli program jest zapisywane w kodzie natywnym, następnie `IDebugEngineLaunch2::LaunchSuspended` prawdopodobnie wywoła `CreateProcess` i `ResumeThread` (funkcji Win32) do uruchomienia programu.  
  
 Uruchamianie programu, w wyniku środowisko wykonawcze programu została załadowana. Niemcy lub środowisku tworzy następnie [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu do opisywania program i przekazuje w tym interfejsie [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) powiadomiono port, który jest program uruchomiona.  
  
 Jeśli `GUID_NULL` są przekazywane, a następnie port uruchamia program. Po uruchomieniu programu tworzy środowisko wykonawcze `IDebugProgramNode2` interfejsu do opisywania program i przekazuje je do `IDebugPortNotify2::AddProgramNode`. Powiadamia to port, na którym działa program. Następnie SDM dołącza aparat debugowania do działającego programu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md)  
 W tym artykule wyjaśniono, co się stanie po uruchomieniu programu i portu jest powiadamiany.  
  
 [Dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md)  
 Dokumenty podczas sesji debugowania jest gotowy do dołączenia do programu DE.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i obliczaniu wyrażeń.