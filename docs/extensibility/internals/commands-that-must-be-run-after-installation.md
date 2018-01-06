---
title: "Polecenia uruchamiane po zakończeniu instalacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ff4b1e572fd1e0c5c500fbd756d01063665bd1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="commands-that-must-be-run-after-installation"></a>Polecenia uruchamiane po instalacji
Jeśli rozszerzenie zostanie wdrożony przy użyciu pliku msi, musisz uruchomić `devenv /setup` jako część instalacji w kolejności dla programu Visual Studio odnaleźć rozszerzeń.  
  
> [!NOTE]
>  Informacje przedstawione w tym temacie dotyczą znajdowanie DevEnv z programu Visual Studio 2008 i starszych wersji. Aby uzyskać informacje na temat odnajdywania DevEnv w nowszych wersjach programu Visual Studio, zobacz [wykrywanie wymagania systemowe](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Znajdowanie devenv.exe  
 Można znaleźć każdą wersję devenv.exe z rejestru wartości [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapisu pliki instalacyjne, za pomocą tabeli RegLocator i AppSearch powoduje niepoprawne obcięcie tabeli do przechowywania wartości rejestru jako właściwości. Aby uzyskać więcej informacji, zobacz [wykrywanie wymagania systemowe](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator wiersze tabeli, aby zlokalizować devenv.exe z różnych wersji programu Visual Studio  
  
|Signature_|główny|Key|Nazwa|Typ|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Wiersze tabeli AppSearch powoduje niepoprawne obcięcie dla odpowiednich wierszy tabeli RegLocator  
  
|Właściwość|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Na przykład, Instalator programu Visual Studio zapisuje wartość rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako **C:\VS2008\Common7\IDE\devenv.exe**, pełną ścieżkę do pliku wykonywalnego, należy uruchomić Instalatora.  
  
 **Uwaga** ponieważ kolumny typu RegLocator 2, nie jest konieczne Określ informacje o dodatkowych wersji w tabeli podpisu.  
  
## <a name="running-devenvexe"></a>Uruchomiona devenv.exe  
 Po AppSearch powoduje niepoprawne obcięcie uruchomieniu działania standardowe w Instalatorze każdej właściwości w AppSearch powoduje niepoprawne obcięcie tabeli ma wartość, wskazując plik devenv.exe dla odpowiedniej wersji programu Visual Studio. Jeśli dowolna z wartości rejestru określonych nie występują — ponieważ nie zainstalowano tej wersji programu Visual Studio — określona właściwość jest ustawiona na wartość null.  
  
 Obsługuje Instalatora Windows, uruchamianie pliku wykonywalnego, który wskazuje właściwość za pomocą akcji niestandardowej wpisz 50. Upewnij się, że pakiet VSPackage został pomyślnie zainstalowany przed zintegrowaniem jej do wykonania w skryptu opcje, msidbCustomActionTypeInScript (1024) i msidbCustomActionTypeCommit (512), należy uwzględnić akcji niestandardowej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji zobacz tabelę Akcja niestandardowa i opcje wykonywania w skryptu akcji niestandardowej.  
  
 Akcje niestandardowe typu 50 określać właściwości zawierającego plik wykonywalny jako wartość kolumny źródłowej i argumenty wiersza polecenia w kolumna docelowa.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Akcja niestandardowa wiersze tabeli, aby uruchomić devenv.exe  
  
|Akcja|Typ|Źródło|docelowy|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/ Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/ Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/ Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/ Setup|  
  
 Akcje niestandardowe musi być utworzone do tabeli InstallExecuteSequence można zaplanować je do wykonania podczas instalacji. Za pomocą odpowiadających im właściwości w każdym wierszu kolumny warunku blokować akcji niestandardowej ich uruchomienie w przypadku wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie jest zainstalowany w systemie.  
  
> [!NOTE]
>  `Null`wynikiem obliczania właściwości `False` w warunkach.  
  
 Wartość kolumny sekwencji dla każdej akcji niestandardowej jest zależny od innych wartości sekwencji pakietu Instalatora Windows. Wartości sekwencji powinny być devenv.exe akcje niestandardowe Uruchom jako najbliżej bezpośrednio przed działania standardowe funkcję InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabela InstallExecuteSequence można zaplanować devenv.exe niestandardowe akcje  
  
|Akcja|Warunek|Sekwencja|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)