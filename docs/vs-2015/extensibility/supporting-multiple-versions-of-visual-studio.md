---
title: Obsługiwanie wielu wersji programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a15eb606e2415d3a6cd5cf115580c6a0d71e801
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685209"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Obsługiwanie wielu wersji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [obsługi wielu wersji programu Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/supporting-multiple-versions-of-visual-studio).  
  
Termin *side-by-side* oznacza, że można zainstalować i zarządzać wieloma wersjami produktu na tym samym komputerze. Dla pakietów VSPackage oznacza to, że użytkownik może mieć różne wersje programu Visual Studio zainstalowany na tym samym komputerze. Jednak nie może mieć side-by-side wersje usługi pakietów VSPackage załadowane do jednej wersji programu Visual Studio.  
  
 Przed wprowadzeniem Twojego pakietu VSPackage, mogą być ładowane do side-by-side wersji programu Visual Studio, należy rozważyć następujące kwestie:  
  
-   Należy ustalić strategię wdrażania side-by-side, w jakiej chcesz obserwować.  
  
     Aby uzyskać więcej informacji, zobacz [wybór między udostępnionych i kontrolą wersji pakietów VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Formaty plików rozwiązania i projektu należy dopasować strategii wdrażania.  
  
     Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów niestandardowych](../misc/upgrading-custom-projects.md) i [rejestrowanie rozszerzeń nazw plików dla wdrożeń Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Instalatora musi obsługiwać swoją strategię wdrażania, aby składniki numerów wersji, a także składniki współużytkowane przez wszystkie wersje, są poprawnie zainstalowane i zarejestrowane.  
  
     Aby uzyskać więcej informacji, zobacz [instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) , a także [Zarządzanie składnikami](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Instalowanie wersji programu Visual Studio instaluje odpowiednią wersję [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Na przykład instalowania programu Visual Studio 2010 i Visual Studio 2012 na tym samym komputerze instaluje wersjach 4.0 i 4.5 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]odpowiednio.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie między udostępnionymi i wersjonowanymi pakietami VSPackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Wyjaśnia, jak rozwiązywać problemy side-by-side w swojej pakietu VSPackage.  
  
 [Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 W tym artykule opisano, jak zarejestrować skojarzenia plików w scenariuszu side-by-side Twojego pakietu VSPackage.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instalowanie pakietów VSPackage](../misc/installing-vspackages.md)  
 W tym artykule omówiono sposób tworzenia i instalowania pakietów VSPackage i sposób obsługi użytkowników korzystających z wielu wersji programu Visual Studio, w tym samym czasie.

