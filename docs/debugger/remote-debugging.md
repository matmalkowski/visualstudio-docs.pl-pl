---
title: Zdalne debugowanie w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "65"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f2c18e107efbc35c662504a6f784fe6f922cacd
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2017
---
# <a name="remote-debugging"></a>Debugowanie zdalne
Można debugować aplikacji Visual Studio, która została wdrożona na innym komputerze. Aby to zrobić, należy użyć zdalny debuger programu Visual Studio.

Aby uzyskać szczegółowe instrukcje na debugowanie zdalne zobacz następujące tematy.

|Scenariusz|Łącze|
|-|-|-|
|ASP.NET|[Zdalne debugowanie platformy ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) lub [zdalnego debugowania ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# lub Visual Basic|[Zdalne debugowanie C# lub Visual Basic projektu](remote-debugging-csharp.md)|
|C++|[Zdalne debugowanie projektu C++](remote-debugging-cpp.md)|
|Aplikacje uniwersalne systemu Windows (UWP)|[Debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md)|
|Azure|[Zdalne debugowanie ASP.NET na platformie Azure](remote-debugging-azure.md)|
|Sieć szkieletowa usług Azure|[Debugowanie aplikacji sieci szkieletowej usług zdalnej](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).|

Jeśli po prostu chcesz pobrać i zainstalować zdalny debuger i nie wymagają żadnych dodatkowych instrukcji dla danego scenariusza, wykonaj kroki opisane w tym artykule.
  
## <a name="download-and-install-the-remote-tools"></a>Pobierz i zainstaluj narzędzia zdalnej  

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="fileshare_msvsmon"></a>(Opcjonalnie) Uruchamianie zdalnego debugera z udziału plików

Zdalny debuger można znaleźć (**msvsmon.exe**) na komputerze przy użyciu programu Visual Studio Community, Professional lub Enterprise już zainstalowana. W niektórych scenariuszach Najprostszym sposobem konfigurowania zdalnego debugowania jest uruchomienie zdalnego debugera (msvsmon.exe) z udziału plików. Ograniczenia użycia, zobacz stronę pomocy zdalny debuger (**Pomoc > użycia** w zdalnym debugerze).

1. Znajdź **msvsmon.exe** w katalogu odpowiadającym używanej wersji programu Visual Studio. Dla programu Visual Studio Enterprise 2017:

      **Program pliki (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program pliki (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Udział **zdalnego debugera** folderu na komputerze programu Visual Studio.

3. Na komputerze zdalnym, uruchom **msvsmon.exe**. Postępuj zgodnie z [instrukcje instalacji](#bkmk_setup).

> [!TIP] 
> Dla wiersza polecenia instalacji i informacje w wierszu polecenia, zobacz stronę pomocy, aby **msvsmon.exe** , wpisując ``msvsmon.exe /?`` w wierszu polecenia na komputerze z programem Visual Studio zainstalowany (lub przejdź do **Pomoc > użycia**w zdalnym debugerze).
  
## <a name="requirements_msvsmon"></a>Wymagania

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]
  
## <a name="set-up-the-remote-debugger"></a>Konfigurowanie zdalnego debugera  

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a>Skonfigurować debugera zdalnego  
Po uruchomieniu go po raz pierwszy, można zmienić niektóre aspekty konfiguracji zdalnego debugera.
  
-   Jeśli konieczne jest dodanie uprawnień dla innych użytkowników połączyć się ze zdalnym debugerem, wybierz **Narzędzia > uprawnienia**. Musisz mieć uprawnienia administratora, aby udzielić lub odmówić uprawnień.

     > [!IMPORTANT] 
     > Można uruchomić zdalnego debugera na koncie użytkownika, która różni się z konta użytkownika, którego używasz na komputerze programu Visual Studio, ale konta innego użytkownika należy dodać uprawnienia zdalnego debugera. 

     Alternatywnie można uruchomić zdalnego debugera z wiersza polecenia z **/ Zezwalaj \<nazwa użytkownika >** parametru: **polecenie msvsmon / Zezwalaj \< username@computer>**.
  
-   Jeśli musisz zmienić tryb uwierzytelniania lub numer portu lub określ wartość limitu czasu dla narzędzia zdalnej: Wybierz **Narzędzia > Opcje**.  
  
     Listę numerów portów, domyślnie używany, zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md).  
  
     > [!WARNING]
     >  Istnieje możliwość uruchomienia narzędzi zdalnych w trybie Bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest narażone złośliwego lub szkodliwy ruch.

##  <a name="bkmk_configureService"></a>(Opcjonalnie) Konfigurowanie zdalnego debugera jako usługi
Do debugowania w programie ASP.NET oraz innych środowiskach serwera, należy Uruchom zdalny debuger jako Administrator lub, jeśli ma ona zawsze uruchomiona, uruchom zdalny debuger jako usługa.
  
 Jeśli chcesz skonfigurować debugera zdalnego jako usługi, wykonaj następujące kroki.  
  
1.  Znajdź **Kreator konfiguracji zdalnego debugera** (rdbgwiz.exe). (Jest to innej aplikacji z debugera zdalnego). Jest dostępna tylko w przypadku instalowania narzędzi remote tools. Nie jest zainstalowany program Visual Studio.  
  
2.  Uruchamianie Kreatora konfiguracji. Gdy pierwszej strony, kliknij przycisk **dalej**.  
  
3.  Sprawdź **Uruchom debuger programu Visual Studio 2015 zdalnego jako usługi** wyboru.  
  
4.  Dodaj nazwę konta użytkownika i hasła.  
  
     Może być konieczne dodanie **Zaloguj jako usługa** użytkownika bezpośrednio do tego konta (Znajdź **zasady zabezpieczeń lokalnych** (secpol.msc) w **Start** strony lub okna (lub typu  **secpol** w wierszu polecenia). Po wyświetleniu okna, kliknij dwukrotnie **Przypisywanie praw użytkownika**, następnie znajdź **Zaloguj jako usługa** w okienku po prawej stronie. Kliknij go dwukrotnie. Dodaj konto użytkownika do **właściwości** i kliknij **OK**). Kliknij przycisk **Dalej**.  
  
5.  Wybierz typ sieci, który ma narzędzia zdalnej do komunikowania się z. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pośrednictwem domeny, wybierz pierwszy element. Jeśli komputery są połączone za pośrednictwem grupy domowej i grupy roboczej, należy wybrać elementy drugiego i trzeciego. Kliknij przycisk **Dalej**.  
  
6.  Jeśli usługa może być uruchomiona, zostanie wyświetlony **została pomyślnie ukończona Visual Studio Kreatora konfiguracji zdalnego debugera**. Jeśli nie można uruchomić usługi, zobaczysz **nie można ukończyć Visual Studio Kreatora konfiguracji zdalnego debugera**. Strona daje również kilka wskazówek dotyczących należy wykonać, aby pobrać do uruchamiania.  
  
7.  Kliknij przycisk **Zakończ**.  
  
 W tym momencie zdalny debuger działa jako usługa. Można to sprawdzić, przechodząc do **Panel sterowania > usług** i wyszukując **programu Visual Studio 2015 Remote Debugger**.  
  
 Można zatrzymać i uruchomić usługę zdalnego debugera z **Panel sterowania > usługi**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)   
 [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)   
 [Zdalne debugowanie platformy ASP.NET Core na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
