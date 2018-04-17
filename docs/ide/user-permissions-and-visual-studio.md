---
title: Uprawnienia użytkownika i programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ba45cd360059d0ac6efbcdddbe3f1e550f3b3d8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio

Ze względów bezpieczeństwa należy uruchamiać Visual Studio jako zwykły użytkownik w każdym przypadku, gdy jest to możliwe.

> [!WARNING]
> Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

Jako zwykły użytkownik możesz zrobić w środowisku IDE programu Visual Studio prawie wszystko, ale musisz mieć uprawnienia administratora, aby wykonać następujące zadania:

|Obszar|Zadanie|Więcej informacji|  
|----------|----------|--------------------------|  
|Instalacja|Zainstaluj program Visual Studio.|[Instalowanie programu Visual Studio](../install/install-visual-studio.md)|  
||Instalowanie, aktualizowanie lub usuwanie lokalnej zawartości Pomocy.|[Instalowanie zawartości lokalnej i zarządzanie nią](../ide/install-and-manage-local-content.md)|  
|Typy aplikacji|Tworzenie rozwiązań programu SharePoint.|[Wymagania związane z opracowywaniem rozwiązań SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Uzyskanie licencji dewelopera dla [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Uzyskać licencji dewelopera](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Przybornik|Dodawanie klasycznego modelu COM formantów do **przybornika**.|[Przybornik](../ide/reference/toolbox.md)|  
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

### <a name="to-run-visual-studio-with-administrative-permissions"></a>Aby uruchomić program Visual Studio z uprawnieniami administracyjnymi

Te instrukcje dotyczą systemu Windows 10. Są one podobne w innych wersjach systemu Windows.

1. Otwórz **Start** menu, a następnie przewiń do programu Visual Studio 2017 r.

1. Z menu kliknij prawym przyciskiem myszy lub kontekstu **programu Visual Studio 2017**, wybierz pozycję **więcej** > **Uruchom jako administrator**.

     Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

## <a name="see-also"></a>Zobacz także

[Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
[Instalowanie programu Visual Studio](../install/install-visual-studio.md)
