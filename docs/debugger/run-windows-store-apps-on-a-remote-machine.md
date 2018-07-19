---
title: Uruchamianie aplikacji platformy UWP na komputerze zdalnym z | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2845057fe970299d249d580d97b557a5ed311fc0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38795975"
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Uruchamianie aplikacji platformy UWP na komputerze zdalnym w programie Visual Studio
  
Aby uruchomić aplikację platformy uniwersalnej systemu Windows na komputerze zdalnym, należy dołączyć do niego przy użyciu narzędzi Remote Tools for Visual Studio. Remote tools umożliwiają uruchamianie, debugowanie, profilowanie i testowanie aplikacji platformy uniwersalnej systemu Windows, która jest uruchamiana na jednym urządzeniu z drugiego komputera z programem Visual Studio. Uruchamianie na urządzeniu zdalnym może być szczególnie efektywna, gdy komputer z programem Visual Studio nie obsługuje funkcji, które są specyficzne dla aplikacji platformy uniwersalnej systemu Windows, takich jak dotyk, lokalizacji geograficznej i fizycznej orientacji. W tym temacie opisano procedury, aby skonfigurować i uruchomić sesję zdalną.

W niektórych scenariuszach zdalne narzędzia są automatycznie instalowane podczas wdrażania na urządzeniu zdalnym.

- Windows 10 komputery z systemem aktualizacja dla twórców i nowsze wersje narzędzia zdalnego zostaną zainstalowane automatycznie.
- Dla urządzeń z systemem Windows 10 z konsoli Xbox, IOT i HoloLens narzędzia zdalnego zostaną zainstalowane automatycznie.
- Windows Mobile 10, musi być fizycznie podłączona do telefonu, należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development) i należy wybrać **urządzenia** jako cel debugowania. Zdalne narzędzia są wymagane lub nie obsługiwane.

Dla systemu Windows 10 komputery z systemem pre twórcy zaktualizowanej wersji systemu Windows należy zainstalować narzędzia zdalne na komputerze zdalnym ręcznie przed można debugować. Postępuj zgodnie z instrukcjami w tym temacie. 
  
##  <a name="BKMK_Prerequisites"></a> Wymagania wstępne  
 Aby debugować na urządzeniu zdalnym:  
  
- Urządzenie zdalne i komputer z programem Visual Studio musi być połączone przez sieć lub podłączone bezpośrednio za pomocą kabla USB lub sieci Ethernet. Debugowanie przez Internet nie jest obsługiwane.  

- Należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development). 
  
- Dla systemu Windows 10 komputery z systemem Windows 10 w wersji starszej niż aktualizacja dla twórców 10 należy najpierw [Zainstaluj i Uruchom składniki debugowania zdalnego](#BKMK_download).
  
##  <a name="BKMK_Security"></a> Zabezpieczenia  
Domyślnie **uniwersalny (protokół niezaszyfrowanym)** jest używany w systemie Windows 10. Ten protokół można używać tylko w sieciach zaufanych. Połączenie debugowania jest narażony na złośliwych użytkowników, którzy mogą przechwytywać i zmiany danych są przekazywane między środowiskami deweloperskim i komputera zdalnego.
  
> [!WARNING]
>  Istnieje nie zabezpieczeń sieci, gdy tryb uwierzytelniania należy ustawić na **uniwersalny (protokół niezaszyfrowanym)** lub **Brak**. Te tryby należy wybrać tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.  
  
##  <a name="BKMK_DirectConnect"></a> Jak połączyć się bezpośrednio za pomocą kabla USB 

W systemie Windows 10 można wdrożyć na urządzeniu z portu USB, wybierając **urządzenia** zamiast **maszyny zdalnej** jako cel wdrożenia (można to zrobić w **standardowa** paska narzędzi lub na stronie właściwości debugowania).

##  <a name="BKMK_ConnectVS"></a> Konfigurowanie projektu programu Visual Studio dla zdalnego debugowania  
 Należy określić urządzenie zdalne, aby połączyć się we właściwościach projektu. Procedura różni się w zależności od języka programowania. Można wpisać nazwę sieciową urządzenia zdalnego lub wybrać go z **połączenia zdalnego** okno dialogowe.  
  
 ![Okno dialogowe Wybierz połączenie ze zdalnym debugerem](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Okno dialogowe wyświetla listę tylko tych urządzeń, które są w lokalnej podsieci komputera Visual Studio i działają zdalnego debugera.  
  
> [!TIP]
>  Jeśli masz problemy z nawiązaniem połączenia z urządzeniem zdalnym, spróbuj wprowadzić adres IP urządzenia. Aby określić adres IP urządzenia, Otwórz okno polecenia, a następnie wpisz **ipconfig**. Adres IP jest wymieniony jako **adres IPv4**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Wybieranie urządzenia zdalnego dla projektów C# i Visual Basic  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.  
  
2.  Wybierz **debugowania**.  
  
3.  Wybierz **maszyny zdalnej** z **urządzenie docelowe** listy.  
  
4.  Wprowadź nazwę sieciową urządzenia zdalnego w **maszyny zdalnej** pole, lub wybierz **znaleźć** do wyboru urządzenia z **wybierz połączenie ze zdalnym debugerem** okno dialogowe. 

    ![Właściwości projektu dla zdalnego debugowania zarządzane](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Wybieranie urządzenia zdalnego dla projektów języka C++ i JavaScript  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.  
  
2.  Rozwiń **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
3.  Wybierz **zdalny debuger** z **debuger do uruchomienia** listy.  
  
4.  Wprowadź nazwę sieciową urządzenia zdalnego w **NazwaKomputera** pole, lub wybierz strzałkę w dół w polu, aby wybrać urządzenie w **wybierz połączenie ze zdalnym debugerem** okno dialogowe.  

    ![C&#43; &#43; właściwości dla zdalnego debugowania projektu](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a> Pobieranie i instalowanie narzędzi zdalnych (Aktualizacja dla twórców wstępnego)

Jeśli używasz wersji Update pre twórcą systemu Windows 10, następnie postępuj zgodnie z tymi instrukcjami. W przeciwnym razie można pominąć tę sekcję.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Konfigurowanie debugera zdalnego

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Rozpocznij sesję debugowania zdalnego  
 Uruchom, Zatrzymaj i nawigowanie po sesji debugowania zdalnego taki sam sposób czy lokalnej sesji. W wersji Update pre twórcą systemu Windows 10 upewnij się, że Monitor debugera zdalnego działa na urządzeniu zdalnym.  
  
 Następnie wybierz **Rozpocznij debugowanie** na **debugowania** menu (klawiatura: F5). Projekt jest ponownie skompilowana, a następnie wdrożona i uruchomiona na urządzeniu zdalnym. Debuger zawiesza wykonywanie w punktach przerwania, a użytkownik może przechodzić do nad lub poza swój kod. Wybierz **Zatrzymaj debugowanie** aby zakończyć sesję debugowania i zamknąć zdalną aplikację.
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane opcje zdalnego wdrażania](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
