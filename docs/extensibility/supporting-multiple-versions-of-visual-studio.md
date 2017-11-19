---
title: "Obsługa wielu wersji programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc9c13ecf6a5cc6e62caa897adce16830026261a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Obsługa wielu wersji programu Visual Studio
Termin *side-by-side* oznacza, że można zainstalować i zarządzać wieloma wersjami produktu na tym samym komputerze. Do VSPackages oznacza to, że każdy użytkownik może mieć kilka wersji programu Visual Studio zainstalowany na tym samym komputerze. Jednak nie może mieć side-by-side wersje programu VSPackages ładowane do jednej wersji programu Visual Studio.  
  
 Przed wprowadzeniem VSPackage może być załadowane do side-by-side wersji programu Visual Studio, należy rozważyć następujące kwestie:  
  
-   Należy określić strategii wdrażania side-by-side, która ma następować.  
  
     Aby uzyskać więcej informacji, zobacz [wybór między udostępnionego i numerów wersji VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Formaty plików rozwiązań i projektów musi znajdować się w strategii wdrażania.  
  
     Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów niestandardowych](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) i [rejestrowanie rozszerzeń nazw plików w przypadku wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Instalatorem musi obsługiwać strategii wdrażania, dzięki czemu numerów wersji składników i składniki współużytkowana przez wszystkie wersje, są poprawnie zainstalowane i zarejestrowane.  
  
     Aby uzyskać więcej informacji, zobacz [instalowanie VSPackages z Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , a także [zarządzania składnika](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Instalowanie wersji programu Visual Studio instaluje odpowiednią wersję programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Na przykład instalowania programu Visual Studio 2010 i Visual Studio 2012 w tym samym komputerze instaluje wersji 4.0 i 4.5 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]odpowiednio.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybór między VSPackages udostępnionego i wersji](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Wyjaśniono, jak rozwiązać problemy side-by-side, w pakiecie VSPackage.  
  
 [Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 W tym artykule opisano, jak zarejestrować skojarzeń plików w scenariuszu side-by-side VSPackage.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instalowanie VSPackages za pomocą Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
