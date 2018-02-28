---
title: "Zarządzanie opcjami konfiguracji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a3a5ae644d910cdad584c7b285c75987f39c26e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="managing-configuration-options"></a>Opcje konfiguracji zarządzania
Podczas tworzenia nowego typu projektu muszą zarządzać projektu i rozwiązania ustawienia konfiguracji, które określają jak projekt zostanie skompilowany, spakowanych, wdrażania i uruchamiania. W poniższych tematach opisano konfigurację projektu i rozwiązania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie](../../extensibility/internals/configuration-options-overview.md)  
 Opisuje sposób projekty w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] może obsługiwać wiele konfiguracji.  
  
 [Strony właściwości](../../extensibility/internals/property-pages.md)  
 Wyjaśnia, czy użytkownicy mogą wyświetlać i zmieniać właściwości zależnej konfiguracji projektu i niezależnych właściwości za pomocą stron właściwości.  
  
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)  
 Zawiera informacje o co to jest przechowywane w konfiguracji rozwiązania oraz jak konfiguracje rozwiązania bezpośrednie zachowanie **Start** i **kompilacji** poleceń.  
  
 [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)  
 W tym artykule wyjaśniono, jak obiekt konfiguracji projektu zarządza wyświetlania informacji o konfiguracji do interfejsu użytkownika.  
  
 [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)  
 Wyjaśniono, jak lista konfiguracji rozwiązania dla danego rozwiązania jest zarządzana przez **konfiguracje rozwiązania** okno dialogowe.  
  
 [Konfigurowanie projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md)  
 Definiuje czynność wdrażania oraz dwa sposoby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje projektów, które obsługują wdrażania.  
  
 [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)  
 Opisano obsługiwane w każdej konfiguracji procesów kompilacji i interfejsów i metod, przez który dane wyjściowe elementy mogą być udostępniane.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera omówienie projektów jako podstawowe bloki konstrukcyjne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Zostały podane linki do dodatkowych tematów, które opisano metody kontrolowania projektów, kompilowania i kompilowanie kodu.