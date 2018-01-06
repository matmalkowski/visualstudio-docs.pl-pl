---
title: "Instalowanie VSPackages za pomocą Instalatora systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a9f4d45c3fccebed9febc2ea722981f597896ace
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalowanie VSPackages za pomocą Instalatora Windows
Integrowanie VSPackage do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wymaga więcej niż tylko kopiowanie plików na komputerze użytkownika. Instalator programu pakiet VSPackage należy zainstalować pakiet VSPackage i jego plików zależnych i zarejestrować i ich do integracji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. VSPackage można wykorzystać funkcje integracji, takie jak wyświetlanie ikony na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powitalny ekranu i okno dialogowe informacje.  
  
 Pliki Instalatora systemu Microsoft Windows są zalecanym sposobem dystrybucji Twojej VSPackages. Łatwy w użyciu pakietów Instalatora Windows można uruchomić na dowolnym systemie operacyjnym Windows, obsługiwane przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [Instalatora Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje dotyczące Instalatora Windows](../../extensibility/internals/windows-installer-basics.md)  
 Zawiera omówienie programu Windows Installer.  
  
 [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 W tym artykule omówiono różne sposoby, może obsługiwać instalacje side-by-side zarówno z VSPackages i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Tworzenie pakietu Instalatora Windows](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Zawiera omówienie typowe etapy instalatorów należy wykonać, aby poprawnie zainstalować oraz integrowanie VSPackages do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Wykrywanie wymagań systemowych](../../extensibility/internals/detecting-system-requirements.md)  
 W tym artykule opisano, jak można sprawdzić, Instalator [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , a jego składniki i Anuluj instalację, jeśli nie są spełnione wymagania pakiet VSPackage.  
  
 [Zarządzanie składnikami](../../extensibility/internals/component-management.md)  
 Opisano sposób tworzenia Instalatora, które będzie odpowiadać za utrzymanie integralności poprzednich wersji produktu.  
  
 [Wybieranie katalogu instalacyjnego dla pakietu VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Zawiera podsumowanie opcji do lokalizowania VSPackages.  
  
 [Rejestracja pakietu VSPackage](../../extensibility/internals/vspackage-registration.md)  
 W tym artykule omówiono, jak VSPackages są rejestrowane w czasie instalacji i dlatego Autorejestracja jest dobrym pomysłem.  
  
 [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)  
 W tym artykule omówiono sposób użycia nowego agregatora typu projektu dla typów projektów kodu zarządzanego.  
  
 [Instrukcje: generowanie informacji rejestru dla instalatora](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Wyjaśniono, jak używać RegPkg.exe do generowania manifestu rejestracji dla zarządzanych pakiet VSPackage.  
  
 [Polecenia, które należy uruchomić po instalacji](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Wyjaśnia sposób uruchamiania polecenia po instalacji, aby zintegrować VSPackages do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Odinstalowywanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 W tym artykule opisano kroki, które instalatorem należy wykonać podczas VSPackage odinstalowanie.  