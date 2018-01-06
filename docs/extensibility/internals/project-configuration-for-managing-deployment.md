---
title: "Zarządzanie wdrożenia programu Project konfiguracji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4859e47f8a7ade34a920e4d8e2fac3be58508de3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-managing-deployment"></a>Konfiguracja projektu do zarządzania wdrożenia
Wdrożenie jest czynnością fizycznie przeniesienie elementów dane wyjściowe z procesu kompilacji do oczekiwanej lokalizacji do debugowania i instalacji. Na przykład aplikacji sieci Web może być oparty na komputerze lokalnym i następnie umieszczone na serwerze.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje dwa sposoby, które projekty może być włączony we wdrożeniu:  
  
-   Jako podmiot procesu wdrażania.  
  
-   Menedżer procesu wdrażania.  
  
 Przed wdrożeniem rozwiązania, należy najpierw dodać projekt wdrożenia, aby skonfigurować opcje wdrażania. Jeśli projekt Wdróż jeszcze nie istnieje, zostanie wyświetlona prośba, jeśli chcesz utworzyć po wybraniu **wdrożyć rozwiązanie** z **kompilacji** menu lub kliknij prawym przyciskiem myszy rozwiązanie. Kliknięcie przycisku **tak** otwiera **Dodawanie nowego projektu** okno dialogowe z **zdalnego Kreatora wdrażania** wybranego projektu.  
  
 Zdalne Kreatora wdrażania prośba dla typu aplikacji (Windows lub aplikacji internetowej), grupy dane wyjściowe projektu do dołączenia, wszelkie dodatkowe pliki, które chcesz uwzględnić i komputera zdalnego, który chcesz wdrożyć. Ostatniej strony kreatora Wyświetla podsumowanie wybrane opcje.  
  
 Projekty, które są objęte procesem wdrażania utworzyć elementy danych wyjściowych, które muszą zostać przeniesione do środowiska alternatywny. Te dane wyjściowe elementy są opisane jako parametry <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfejsu, którego podstawowy cel if zezwolić na dane wyjściowe grupy projektów. Aby uzyskać więcej informacji dotyczących stosowania `IVsProjectCfg2`, zobacz [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).  
  
 Projekty wdrażania, które zarządzają procesu wdrażania, włącz polecenie Wdróż i odpowiedzi w przypadku wybrania tego polecenia. Implementowanie projekty wdrażania <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejsu, aby wykonać wdrożenie i wykonywania wywołań do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> zdarzenia stanu wdrażania interfejsu do raportu.  
  
 Konfiguracje można określić zależności, które mają wpływ na operacje kompilacji lub wdrożenia. Kompilacji lub wdrożenia zależności są projektów, które muszą być skompilowane lub wdrożone przed lub po same konfiguracje są wbudowane lub wdrożyć. Opisano kompilacji współzależności między projektami o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfejsu i wdrożyć zależności z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsu. Aby uzyskać więcej informacji, zobacz [konfiguracji projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje konfiguracji zarządzania](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguracja projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)