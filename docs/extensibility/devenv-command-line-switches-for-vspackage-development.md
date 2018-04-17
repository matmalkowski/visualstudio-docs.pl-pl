---
title: Przełączniki wiersza polecenia Devenv programowanie pakiet VSPackage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6ad615048255452fc5642f8680b586d69587db5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Przełączniki wiersza polecenia Devenv programowanie pakiet VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umożliwia deweloperom automatyzację zadań w wierszu polecenia, podczas wykonywania devenv.exe, pliku, który uruchamia proces programu Visual Studio zintegrowane środowisko programistyczne (IDE).  
  
 Zadania obejmują:  
  
-   Wdrażanie aplikacji w konfiguracjach wstępnie z poza IDE.  
  
-   Automatycznie kompilowania projektów przy użyciu ustawienia domyślne ustawienia kompilacji lub konfiguracje debugowania.  
  
-   Podczas ładowania środowisko IDE w określonej konfiguracji, wszystko poza IDE. Ponadto można dostosować IDE po uruchomieniu.  
  
## <a name="guidelines-for-switches"></a>Wytyczne dotyczące przełączników  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dokumentacji opisano przełączniki wiersza polecenia devenv na poziomie użytkownika. Aby uzyskać więcej informacji, zobacz [przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md). Devenv obsługuje również dodatkowe przełączniki wiersza polecenia, które są przydatne w przypadku pakiet VSPackage tworzenie, wdrażanie i debugowanie.  
  
|Przełącznik wiersza polecenia|Opis|  
|--------------------------|-----------------|  
|/safemode|Uruchamia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym, ładowanie tylko domyślny IDE i usług. Przełącznik /safemode zapobiega wszystkich innych firm VSPackages podczas ładowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zostanie uruchomiony, w związku z tym zapewnienia stabilnej wykonywania.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
|/ resetskippkgs|Następnie uruchamia czyści wszystkie Pomiń ładowanie opcje, które zostały dodane przez użytkowników, którzy chcą, aby uniknąć obciążania problematyczne VSPackages [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Obecność tagu SkipLoading wyłącza ładowanie pakiet VSPackage. Ponownie wyczyszczenie tagu umożliwia ładowanie pakiet VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
|/ rootsuffix|Uruchamia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy użyciu lokalizacji alternatywnej. Poniższe polecenie jest uruchamiane przez skrót utworzony przez [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Instalatora:<br /><br /> Devenv/rootsuffix exp<br /><br /> W takim przypadku exp identyfikuje lokalizacji przy użyciu danego sufiksu, na przykład 10.0Exp niż 10.0. Eksperymentalne wystąpienie umożliwia debugowanie pakiet VSPackage niezależnie od wystąpienie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] używanym do pisania kodu.<br /><br /> Ten przełącznik może zająć dowolny ciąg identyfikujący lokalizację utworzonego przy użyciu VSRegEx.exe. Aby uzyskać więcej informacji, zobacz [eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md).|  
|/Splash|Pokazuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ekran powitalny w zwykły sposób, a następnie wyświetla okno przed pokazaniem głównego IDE. W oknie komunikatu umożliwia badanie ekran powitalny, aby na przykład sprawdzić ikoną produktu pakiet VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie przełączniki wiersza polecenia](../extensibility/adding-command-line-switches.md)   
 [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)