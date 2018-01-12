---
title: "Wdrażanie aplikacji platformy uniwersalnej systemu Windows z programu Visual Studio | Dokumentacja firmy Microsoft"
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
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 95f009ca761d4d978fb5e5a9323722e5dfc34cb8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Wdrażanie aplikacji platformy uniwersalnej systemu Windows z programu Visual Studio
![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Funkcja wdrożenia programu Visual Studio tworzy i rejestruje aplikacji platformy uniwersalnej systemu Windows, które są tworzone w programie Visual Studio na urządzeniu docelowym. Dokładnie, jak jest zarejestrowana aplikacja, zależy od tego, czy urządzenie docelowe jest lokalnym lub zdalnym:  
  
-   Gdy element docelowy jest na komputerze lokalnym programu Visual Studio, Visual Studio rejestruje aplikacji ze swojego folderu kompilacji.  
  
-   Gdy elementem docelowym jest urządzenie zdalne, Visual Studio kopiuje pliki wymagane do maszyny zdalnej i rejestruje aplikację na tym urządzeniu.  
  
 Wdrożenia jest automatycznie podczas debugowania aplikacji z programu Visual Studio za pomocą **Rozpocznij debugowanie** opcji (klawiatury: F5) lub **uruchomić bez debugowania** opcji (klawiatury: CTRL + F5). Można także wdrożyć aplikację ręcznie. Ręczne wdrażanie jest przydatne w następujących scenariuszach:  
  
-   Ad hoc testowania na komputerze lokalnym lub zdalnym.  
  
-   Wdrażanie aplikacji, która zostanie uruchomiony w innej aplikacji, który chcesz debugować.  
  
-   Wdrażanie aplikacji, która będzie debugowany po uruchomieniu przez inną aplikację lub metody.
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>Jak wdrożyć aplikację platformy uniwersalnej systemu Windows  
 Ręczne wdrażanie aplikacji jest prosty proces:  
  
1.  Jeśli wdrażasz do zdalnego urządzenia, określ nazwę lub adres IP urządzenia, na stronie właściwości projektu Projekt startowy aplikacji. (Kroki są wymienione w dół dalsze w tym temacie).  
  
2.  Na pasku narzędzi programu Visual Studio debugger wybierz cel wdrożenia z listy rozwijanej obok pola **Rozpocznij debugowanie** przycisku.  
  
     ![Uruchom na komputerze lokalnym](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  Na **kompilacji** menu, wybierz **wdrażania**  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a>Jak określać urządzenie zdalne  

**Wymagania wstępne**  
  
Na zdalnym urządzeniu z systemem Windows 10, należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development). Na urządzeniach z systemem Windows 10 systemem twórcy aktualizacji lub później, zdalne narzędzia są instalowane automatycznie podczas wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [debugowania pakietu aplikacji zainstalowanych](../debugger/debug-installed-app-package.md).

> [!NOTE]
> W wersji aktualizacji sprzed twórcy systemu Windows 10 i Windows 8.1 narzędzi Remote Tools for Visual Studio musi być zainstalowany na urządzeniu zdalnym i zdalnego debugera musi być uruchomiona. Na Windows 8.1 należy również zainstalować licencję dewelopera.
  
Wdrożenie używa zdalnego debugera kanał sieciowy do wysyłania plików aplikacji do urządzenia zdalnego.  
  
#### <a name="to-specify-a-remote-device"></a>Aby określić urządzenie zdalne  
  
1.  Na stronie właściwości debugowania projektu startowego Określ nazwę lub adres IP docelowego zdalnego wdrażania.  
  
2.  Aby otworzyć stronę właściwości debugowania, wybierz projekt w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.  
  
3.  Następnie wybierz pozycję **debugowania** węzła w oknie właściwości strony.

4. Dla **urządzenie docelowe**, wybierz pozycję **maszyny zdalnej**.

5. W obszarze **maszyny zdalnej**, kliknij przycisk **znaleźć**.
  
4.  Możesz wpisać nazwę lub adres IP urządzenia zdalnego, lub możesz wybrać urządzenia z **połączenia zdalnego** okno dialogowe.  
  
     ![Wybierz okno dialogowe połączenia zdalnego debugera](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     **Połączenia zdalnego** okno dialogowe wyświetla w podsieci sieci lokalnej i dowolne urządzenie, które są połączone bezpośrednio do maszyny programu Visual Studio przez kabla Ethernet urządzenia.  
  
 **Określanie zdalnego urządzenia na stronie projektu JavaScript lub Visual C++**  
  
 ![& C &43; 43; właściwości do zdalnego debugowania projektu](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Wybierz **zdalnego debugera** z **debugera, aby uruchomić** listy.  
  
2.  Wprowadź nazwę sieci urządzenie zdalne w **Nazwa maszyny** pole. Alternatywnie można wybrać strzałkę w dół w polu, aby wybrać urządzenie w oknie dialogowym Wybierz połączenia zdalnego debugera.  
  
 **Określanie zdalnego urządzenia na stronie projektu Visual C# i Visual Basic**  
  
 ![Właściwości projektu zdalne debugowanie zarządzane](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Wybierz **maszyny zdalnej** z **urządzenie docelowe** listy.  
  
2.  Wprowadź nazwę sieci urządzenie zdalne w **maszyny zdalnej** lub kliknij przycisk **znaleźć** aby wybrać urządzenie z **wybierz połączenia zdalnego debugera** okno dialogowe.  
  
##  <a name="BKMK_Deployment_options"></a>Opcje wdrażania  
 Można ustawić następujące opcje wdrażania na stronie właściwości debugowania projektu startowego.  
  
 **Zezwalaj na sprzężenie zwrotne sieci**  
 Ze względów bezpieczeństwa platformy uniwersalnej systemu Windows lub [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikację, która jest zainstalowana w standardowy sposób nie może wykonywać wywołania sieci jest zainstalowany na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed wysłaniem aplikacji [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], należy przetestować aplikację bez zwolnienia.  
  
 Aby usunąć wykluczenia sprzężenia zwrotnego sieci z poziomu aplikacji:  
  
-   Na stronie właściwości C# i VB debugowania wyczyść **Zezwalaj na sprzężenie zwrotne sieci** pole wyboru.  
  
-   Na stronie właściwości JavaScript i debugowania, ustaw **Zezwalaj na sprzężenie zwrotne sieci** do wartości **nr**.  
  
 **Nie uruchamiaj, ale Debuguj kod przy rozpoczęciu (C# i VB) / uruchom aplikację (JavaScript i C++)**  
 Aby skonfigurować wdrożenie, aby automatycznie uruchomić sesję debugowania, po uruchomieniu aplikacji:  
  
-   Na stronie właściwości C# i VB debugowania Sprawdź **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** pole wyboru.  
  
-   Na stronie właściwości JavaScript i debugowania, ustaw **uruchamianie aplikacji** do wartości **tak**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pakietu aplikacji zainstalowanych](../debugger/debug-installed-app-package.md).   
 [Uruchamianie aplikacji w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md)