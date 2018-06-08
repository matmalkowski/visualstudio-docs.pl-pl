---
title: Uruchom jako administrator
ms.date: 06/05/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 89ba7338645ab6cc421716832a3d6f424bb57dfc
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844394"
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i programu Visual Studio

Ze względów bezpieczeństwa należy uruchomić program Visual Studio jako zwykłego użytkownika, jeśli to możliwe.

> [!WARNING]
> Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

Możesz to zrobić prawie wszystko w programie Visual Studio IDE jako zwykłego użytkownika. Musisz mieć uprawnienia administratora, aby wykonać następujące zadania:

|Obszar|Zadanie|Więcej informacji|
|----------|----------|--------------------------|
|Instalacja|Zainstaluj program Visual Studio.|[Instalowanie programu Visual Studio](../install/install-visual-studio.md)|
||Zainstalować, zaktualizować lub usunąć zawartość lokalnej pomocy.|[Zainstaluj i Zarządzaj lokalnej zawartości pomocy](../ide/install-and-manage-local-content.md)|
|Typy aplikacji|Tworzenie rozwiązań programu SharePoint.|[Wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)|
|Przybornik|Dodawanie formantów klasycznego modelu COM **przybornika**.|[Przybornik](../ide/reference/toolbox.md)|
|Kompilowanie|Korzystanie ze zdarzeń po kompilacji, które rejestrują składnika.|[Niestandardowe kroki procesu kompilacji zrozumieć i zdarzenia kompilacji](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Podczas tworzenia projektów C++, obejmują kroku rejestracji.||
|Debugowanie|Debugowanie aplikacji, które są uruchamiane z podwyższonym poziomem uprawnień.|[Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)|
||Debugowanie aplikacji, które konta Uruchom pod innego użytkownika, takie jak witryny sieci Web ASP.NET.|[Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[WPF hosta (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Debugowanie projektów usług w chmurze Microsoft Azure przy użyciu emulatora.|[Usługi w chmurze w programie Visual Studio debugowania](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Konfigurowanie zapory do zdalnego debugowania.|[Debugowanie zdalne](../debugger/remote-debugging.md)|
|Narzędzia wydajności|Profilowanie aplikacji.|[Profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md)|
|wdrażania|Wdrażanie aplikacji sieci web do programu Internet Information Services (IIS) na komputerze lokalnym.|[Wdrażanie aplikacji sieci web ASP.NET przy użyciu programu Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Uruchom program Visual Studio jako administrator

Jeśli musisz uruchomić program Visual Studio jako administrator, wykonaj następujące kroki, aby otworzyć IDE:

> [!NOTE]
> Te instrukcje dotyczą systemu Windows 10. Są one podobne w innych wersjach systemu Windows.

1. Otwórz **Start** menu, a następnie przewiń do programu Visual Studio 2017 r.

1. Z menu kliknij prawym przyciskiem myszy lub kontekstu **programu Visual Studio 2017**, wybierz pozycję **więcej** > **Uruchom jako administrator**.

   Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

Można również zmodyfikować skrótu do aplikacji, aby zawsze uruchamiane z uprawnieniami administracyjnymi.

## <a name="see-also"></a>Zobacz także

- [Port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalowanie programu Visual Studio](../install/install-visual-studio.md)