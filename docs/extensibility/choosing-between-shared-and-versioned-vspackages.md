---
title: "Wybór między VSPackages udostępnionego i numerów wersji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9442d6685d27a9270c1e71e3a79e9f810b6f40f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Wybór między VSPackages udostępnionego i wersji
Różne wersje programu Visual Studio mogą współistnieć na tym samym komputerze. VSPackages może obsługiwać żadnych mieszane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wersji.  
  
 Można włączyć side-by-side instalacje VSPackages przy użyciu jednej z dwóch strategii, udostępnionych strategię lub strategii numerów wersji. Zarówno pomieścić obecności wielu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wraz ze skojarzonymi wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 W strategii udostępnionego, co pakiet VSPackage jest zarejestrowany do użycia w wielu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W strategii określonej wersji, są zainstalowane wielu pakiet VSPackage bibliotek DLL, po jednej dla każdej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] który obsługiwanych.  
  
## <a name="shared-vspackages"></a>VSPackages udostępnionego  
 Za pomocą udostępnionego pakiet VSPackage jest odpowiednia, korzystając z tego samego pakiet VSPackage w wielu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby zaimplementować pakiet VSPackage udostępnionego, należy wykonać następujące czynności:  
  
-   Zapewnić zgodność z wieloma wersjami VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dostępne są to zrobić na dwa sposoby:  
  
    -   Ogranicz VSPackage przy użyciu tylko funkcje wersji najwcześniejszą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] który obsługiwanych.  
  
    -   Program VSPackage w celu dostosowania do wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , w którym jest uruchomiona. Następnie, jeśli zapytania dla nowszej usług kończyć się niepowodzeniem, VSPackage zaoferować innych usług, które są obsługiwane przez starsze wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Zarejestruj odpowiednio VSPackage. Aby uzyskać więcej informacji, zobacz [rejestracji pakiet VSPackage](../extensibility/internals/vspackage-registration.md) i [zarządzane rejestracji pakiet VSPackage](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Zarejestruj odpowiednio rozszerzeń plików. Aby uzyskać więcej informacji, zobacz [rejestrowanie rozszerzeń nazw plików w przypadku wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Utworzyć Instalatora, która wdraża VSPackage odpowiednie wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [instalowanie VSPackages z Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) i [zarządzania składnika](../extensibility/internals/component-management.md).  
  
-   Rozwiąż problem kolizji rejestracji. Aby uzyskać więcej informacji, zobacz [rejestracji pakiet VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Upewnij się, że pliki zarówno udostępnionego i numerów wersji przestrzegać zliczanie umożliwia bezpieczne instalowaniu i usuwaniu wielu wersji. Aby uzyskać więcej informacji, zobacz [zarządzania składnika](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages numerów wersji  
 W obszarze określonej wersji strategii pakiet VSPackage, Utwórz jeden pakiet VSPackage dla każdej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] który obsługiwanych. W ten sposób jest odpowiednie, jeśli będziesz korzystać z usług świadczonych przez nowsze wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ponieważ każdy pakiet VSPackage można rozwijać bez wpływu na inne. Niemniej jednak numerów wersji strategii tworzenia wielu plików binarnych, ze ścieżki bazowej kodu jednego lub wielu baz kodu niezależne, spowodować początkowego projektowania więcej niż udostępnionego strategii. Ponadto pracy dodatkowe ustawienia mogą być wymagane, ponieważ należy utworzyć oddzielne ustawienia dla każdej wersji albo konfiguracji pojedynczego, wykrywające wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są instalowane i obsługuje VSPackage.  
  
## <a name="binary-compatibility"></a>Zgodność binarną  
 Ogólnie rzecz biorąc zgodność binarną umożliwia VSPackages kodu natywnego opracowany z wcześniejszymi wersjami programu Visual Studio, aby uruchomić w nowszej wersji programu Visual Studio. Istnieją trzy ważne wyjątki:  
  
-   Jeśli VSPackage zależy od konkretnej wersji środowiska CLR, a następnie należy określić, w której wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest uruchomiona.  
  
-   Pakiet VSPackage może mieć zależności na określoną funkcję inny pakiet VSPackage lub innego produktu. W rezultacie pakiet VSPackage można uruchomić tylko, gdy jest spełniony zależności.  
  
-   Pakiet VSPackage mogą wpłynąć na poprawkę zabezpieczeń w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dodatku service pack lub nowsza wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W takich przypadkach pakiet VSPackage opracowanych za pomocą wcześniejszej wersji [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] może nie działać w wersjach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po zastosowaniu poprawkę zabezpieczeń. Można jednak Skompiluj ponownie pakiet z nowszej wersji i została ona również uruchomić w starszych wersjach.  
  
 VSPackages zarządzanych muszą zostać skompilowane przy użyciu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] spełniających wersję docelową [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Oprócz Planowanie zgodności plików binarnych dla danych binarnych z pakiet VSPackage, należy również wziąć pod uwagę rozwiązanie i formaty plików projektu. Jeśli VSPackage tworzy nowy typ projektu, należy zdecydować, czy można wykonać w wersji tylko jeden lub wiele wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów niestandardowych](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie VSPackages za pomocą Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Składnik zarządzania](../extensibility/internals/component-management.md)