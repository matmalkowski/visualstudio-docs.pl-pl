---
title: Uruchamianie aplikacji platformy uniwersalnej systemu Windows na zdalnym komputerze | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36233571"
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym w programie Visual Studio
  
Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym, należy dołączyć do niej przy użyciu narzędzi Remote Tools for Visual Studio. Narzędzia remote tools umożliwiają uruchamianie, debugowanie profilu i testowanie aplikacji platformy uniwersalnej systemu Windows, który jest uruchomiony na jednym urządzeniu z drugiego komputera, na którym działa program Visual Studio. Uruchamianie na urządzeniu zdalnym mogą być szczególnie przydatny, gdy komputer programu Visual Studio nie obsługuje funkcje, które są określone do aplikacji platformy uniwersalnej systemu Windows, takich jak touch, lokalizacja geograficzna i orientację fizycznych. W tym temacie opisano procedury, aby skonfigurować i uruchomić sesję zdalną.

W niektórych scenariuszach narzędzia zdalnej są automatycznie instalowane podczas wdrażania na urządzeniu zdalnym.

- Systemem aktualizacji twórców i nowszych wersjach komputerów z systemem Windows 10 narzędzia do zdalnego zostaną zainstalowane automatycznie.
- W przypadku urządzeń z systemem Windows 10 w konsoli Xbox, IOT i HoloLens narzędzia zdalnego zostaną zainstalowane automatycznie.
- Dla urządzeń przenośnych z systemem Windows 10, muszą być fizycznie podłączeni do telefonu, należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development) i należy wybrać **urządzenia** jako cel debugowania. Zdalne narzędzia są wymagane lub nie obsługiwane.

Pre twórcy wersją aktualizacji systemu Windows komputerów z systemem Windows 10 należy zainstalować narzędzia zdalnej na komputerze zdalnym ręcznie przed debugowaniem. Postępuj zgodnie z instrukcjami w tym temacie. 
  
##  <a name="BKMK_Prerequisites"></a> Wymagania wstępne  
 Aby debugować na urządzeniu zdalnym:  
  
- Urządzenie zdalne i komputera programu Visual Studio musi być połączone za pośrednictwem sieci lub połączone bezpośrednio za pośrednictwem kabla USB lub sieci Ethernet. Debugowanie przez Internet nie jest obsługiwane.  

- Należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development). 
  
- Systemem Windows 10 w wersji starszej niż Windows 10 Creator aktualizacji komputerów z systemem Windows 10, należy najpierw [zainstalować i uruchomić składniki zdalnego debugowania](#BKMK_download).
  
##  <a name="BKMK_Security"></a> Zabezpieczeń  
Domyślnie **uniwersalnego (nieszyfrowanego protokołu)** jest używany w systemie Windows 10. Ten protokół należy używać tylko w sieciach zaufanych. Połączenie debugowania jest narażony na złośliwych użytkowników, którzy może przechwytywać i zmiany danych są przekazywane między opracowywania i komputer zdalny.
  
> [!WARNING]
>  Brak żadnych zabezpieczeń sieci po ustawieniu trybu uwierzytelniania **uniwersalnego (nieszyfrowanego protokołu)** lub **Brak**. Te tryby należy wybrać tylko wtedy, gdy masz pewność, że sieć nie jest narażone z złośliwego lub szkodliwy ruch.  
  
##  <a name="BKMK_DirectConnect"></a> Jak połączyć się bezpośrednio przy użyciu kabla USB 

W systemie Windows 10 można wdrożyć na urządzeniu połączenie USB, wybierając **urządzenia** zamiast **maszyny zdalnej** jako cel wdrożenia (można to zrobić w **standardowe** paska narzędzi lub na stronie właściwości debugowania).

##  <a name="BKMK_ConnectVS"></a> Konfigurowanie projektu programu Visual Studio zdalne debugowanie  
 Należy określić urządzenie zdalne, aby nawiązać połączenie we właściwościach projektu. Procedura zależy od języka programowania. Możesz wpisać nazwę sieciową urządzenie zdalne lub możesz wybrać je z **połączenia zdalnego** okno dialogowe.  
  
 ![Wybierz okno dialogowe połączenia zdalnego debugera](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Okno dialogowe wyświetla tylko te urządzenia, które są w podsieci lokalnej komputera programu Visual Studio i działają zdalnego debugera.  
  
> [!TIP]
>  Jeśli masz problemy z połączeniem urządzenie zdalne, spróbuj wprowadzić adres IP urządzenia. Aby określić adres IP urządzenia, Otwórz okno polecenia, a następnie wpisz **ipconfig**. Adres IP jest wymieniony jako **adres IPv4**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Wybierz urządzenie zdalne dla projektów C# i Visual Basic  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości** z menu skrótów.  
  
2.  Wybierz **debugowania**.  
  
3.  Wybierz **maszyny zdalnej** z **urządzenie docelowe** listy.  
  
4.  Wprowadź nazwę sieci urządzenie zdalne w **maszyny zdalnej** wpisz lub wybierz **znaleźć** aby wybrać urządzenie z **wybierz połączenia zdalnego debugera** okno dialogowe. 

    ![Właściwości projektu zdalne debugowanie zarządzane](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Wybierz urządzenie zdalne dla projektów języka JavaScript i C++  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości** z menu skrótów.  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
3.  Wybierz **zdalnego debugera** z **debugera, aby uruchomić** listy.  
  
4.  Wprowadź nazwę sieci urządzenie zdalne w **Nazwa maszyny** wpisz lub wybierz strzałkę w dół w polu, aby wybrać urządzenie z **wybierz połączenia zdalnego debugera** okno dialogowe.  

    ![C&#43; &#43; właściwości do zdalnego debugowania projektu](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a> Pobierz i zainstaluj narzędzia zdalnej (wstępne twórców aktualizacja)

Jeśli korzystasz z wersji pre twórcy wersje aktualizacji systemu Windows 10, wykonaj te instrukcje. W przeciwnym razie można pominąć tę sekcję.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Uruchom sesję debugowania zdalnego  
 Uruchom, Zatrzymaj, a nawigowanie po sesji debugowania zdalnego tak samo jak sesji lokalnej. W wersji pre twórcy wersje aktualizacji systemu Windows 10 upewnij się, że Monitor debugera zdalnego działa na urządzeniu zdalnym.  
  
 Następnie wybierz pozycję **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Projekt jest ponownie kompilowana, następnie wdrożyć i uruchomić na urządzeniu zdalnym. Debuger wstrzymuje wykonywanie w punktów przerwania i można przejść do, za pośrednictwem i z kodu. Wybierz **Zatrzymaj debugowanie** zakończyć sesję debugowania i zamknij aplikację zdalnego.
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane opcje zdalnego wdrażania](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
