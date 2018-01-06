---
title: "Uprawnienia użytkownika i programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3cf223b0b4d2f8ca710a5d5fdb349c7a423b1b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio
Ze względów bezpieczeństwa należy uruchamiać Visual Studio jako zwykły użytkownik w każdym przypadku, gdy jest to możliwe.  

> [!WARNING]
>  Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.  

 Jako zwykły użytkownik możesz zrobić w środowisku IDE programu Visual Studio prawie wszystko, ale musisz mieć uprawnienia administratora, aby wykonać następujące zadania:  

|Obszar|Zadanie|Więcej informacji|  
|----------|----------|--------------------------|  
|Instalacja|Zainstaluj program Visual Studio.|[Instalowanie programu Visual Studio](../install/install-visual-studio.md)|  
||Instalowanie, aktualizowanie lub usuwanie lokalnej zawartości Pomocy.|[Instalowanie zawartości lokalnej i zarządzanie nią](../ide/install-and-manage-local-content.md)|  
|Typy aplikacji|Tworzenie rozwiązań programu SharePoint.|[Wymagania związane z opracowywaniem rozwiązań SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Uzyskanie licencji dewelopera dla [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Uzyskać licencji dewelopera](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Przybornik|Dodawanie klasycznego modelu COM formantów do **przybornika**.|[Korzystanie z przybornika](../ide/using-the-toolbox.md)|  
|Dodatki|Instalowanie i używanie dodatków, które zostały napisane przy użyciu klasycznego modelu COM w IDE.|[Tworzenie dodatków i kreatorów](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|  
|Kompilowanie|Używanie zdarzeń mających miejsce po kompilacji, które rejestrują składnik.|[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Włączanie etapu rejestracji podczas kompilowania projektów języka C++.|[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Debugowanie|Debugowanie aplikacji, które działają z podwyższonymi uprawnieniami.|[Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)|  
||Debugowanie aplikacji, które działają na innym koncie użytkownika, takich jak witryny sieci Web programu ASP.NET.|[Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[Host WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|  
||Debugowanie projektów usług w chmurze Microsoft Azure przy użyciu emulatora.|[Debugowanie usługi w chmurze w programie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Konfigurowanie zapory do zdalnego debugowania.|[Debugowanie zdalne](../debugger/remote-debugging.md)|  
|Narzędzia wydajności|Profilowanie aplikacji.|[Profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md)|  
|wdrażania|Wdrażanie aplikacji sieci Web do usług Internet Information Services (IIS) na komputerze lokalnym.|[Wdrażanie aplikacji sieci Web ASP.NET przy użyciu programu Visual Studio lub Visual Web Developer u dostawcy hostingu: Wdrażanie usług IIS jako środowisko testowe](http://go.microsoft.com/fwlink/?LinkId=266478)|

## <a name="running-visual-studio-as-an-administrator"></a>Uruchamianie programu Visual Studio jako administrator  
 Możesz uruchomić program Visual Studio z uprawnieniami administracyjnymi przy każdym uruchomieniu IDE lub zmodyfikować skrót aplikacji, aby program był zawsze uruchamiany z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz Pomoc systemu Windows.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8debuggerincludeswin8mdmd-includewin81debuggerincludeswin81mdmd-includewinserver8debuggerincludeswinserver8mdmd-or-includewinblueserver2ideincludeswinblueserver2mdmd"></a>Aby uruchomić program Visual Studio z uprawnieniami administracyjnymi [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)], lub[!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)]  

1.  Na **Start** ekranu, wpisz **programu Visual Studio**. Powinna się pojawić wersja lub wersje programu Visual Studio, które zostały zainstalowane.  

2.  Wybierz wersję programu Visual Studio, którą chcesz uruchomić, a następnie wywołaj menu podręczne (wyświetla się u dołu ekranu). Wybierz **Uruchom jako administrator**.  

     Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7debuggerincludeswin7mdmd-or-includewinsvr08r2debuggerincludeswinsvr08r2mdmd"></a>Aby uruchomić program Visual Studio z uprawnieniami administracyjnymi [!INCLUDE[win7](../debugger/includes/win7_md.md)] lub[!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]  

1.  Na **Start** menu, wybierz **wszystkie programy**.  

2.  W **programu Microsoft Visual Studio** *wersji* wybierz folder **programu Visual Studio** *wersji* Otwórz menu skrótów, a następnie wybierz pozycję  **Uruchom jako administrator**.  

     Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.  

## <a name="see-also"></a>Zobacz też  
 [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
