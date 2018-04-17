---
title: Rozszerzanie pakowania i wdrażania SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c91c78e6ab78ac39eb5c53c32a70ead895129df0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="extending-sharepoint-packaging-and-deployment"></a>Rozszerzanie pakowania i wdrażania SharePoint
  Można rozszerzyć pakowania i proces wdrażania dla projektów programu SharePoint.
  
##  <a name="creating-deployment-steps"></a>Tworzenie kroki wdrażania  
 Podczas wdrażania projektu SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] wykonuje serię kroków wdrażania. Visual Studio zawiera kroki wdrażania wbudowanych dla wielu zadań, takich jak wycofania i Dodawanie rozwiązania. Można jednak również utworzyć etapów wdrożenia.  
  
 Aby uzyskać wskazówki, który demonstruje sposób tworzenia kroku wdrożenia, zobacz [wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating-deployment-configurations"></a>Tworzenie konfiguracji wdrażania  
 Konfiguracja wdrożenia jest zestaw kroków wdrażania, który jest wykonywane dla danego projektu, ale może mieć wpływ na wszystkie SharePoint — elementy projektu. Każdy konfiguracji wdrożenia zawiera jeden zestaw kroków, które jest wykonywane podczas wdrażania projektu, a innego zestawu, który zostanie wykonany po wycofany projektu. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] obejmuje dwie konfiguracje wdrożenia wbudowanych, ale mogą także tworzyć własne. Podczas tworzenia konfiguracji wdrożenia może zawierać kroki wdrażania wbudowanych i kroki wdrażania, które można utworzyć.  
  
 Aby uzyskać wskazówki, który demonstruje sposób tworzenia konfiguracji wdrażania, zobacz [wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Uruchom kod po rozwiązania programu SharePoint jest wdrożony lub wycofany  
 Można obsługiwać zdarzenia w celu wykonywania dodatkowych zadań, gdy rozwiązanie programu SharePoint jest wdrożony lub wycofany. Visual Studio informuje o zdarzeniach, które może obsłużyć w następujących scenariuszach:  
  
-   Przed i po każdym wdrożeniu krok jest wykonywany dla elementu projektu SharePoint. Aby uzyskać więcej informacji, zobacz [porady: uruchamianie kodu w trakcie kroków wdrożeniowych](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Przed i po projekt SharePoint jest wdrożony lub wycofany. Aby uzyskać więcej informacji, zobacz [porady: uruchamianie kodu, gdy projekt SharePoint jest wdrożony lub wycofany](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="handling-deployment-conflicts"></a>Obsługa konfliktów wdrożenia  
 Niektóre typy elementów projektu SharePoint, łącznie z modułami, części sieci Web, wystąpienia listy i typy zawartości, podaj Rozwiązywanie konfliktów wdrożenia wbudowanych. Podczas wdrażania rozwiązania, które zawiera jeden z tych elementów projektu programu Visual Studio najpierw sprawdza, czy plik istnieje już w witrynie programu SharePoint o tej samej nazwie, adres URL lub identyfikator jako plik w elemencie, który jest wdrażany. W przypadku konfliktu, Visual Studio automatycznie rozwiązać konflikt, lub jego monit o określenie, czy chcesz, aby Visual Studio Rozwiąż konflikt, lub przycisk Anuluj, wdrożenie. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Tej funkcji można rozszerzyć, podając własny kod, który sprawdza i rozwiązywania konfliktów wdrożenia. Aby uzyskać więcej informacji, zobacz [porady: Obsługa konfliktów wdrożenia](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Uruchom wiersz polecenia operacji przed lub po projektu jest wdrożona  
 Jeśli chcesz uruchomić operację wiersza polecenia, po wdrożeniu rozwiązania programu SharePoint, można ustawić <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu. Visual Studio wykonuje te polecenia przed i po wdrożeniu projektu.  
  
 W niektórych przypadkach może wystąpić konflikty wdrażania. Istnieje kilka różnych sposobów, aby rozwiązać konflikty. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing-validation-rules"></a>Dostosowywanie reguły walidacji  
 Przed wdrożeniem pakietu rozwiązania (wsp), można utworzyć funkcji niestandardowej oraz pakietu reguł sprawdzania poprawności, aby sprawdzić poprawność funkcji lub pakietu. Na przykład może raportować informacje, ostrzeżenia lub błędy dla deweloperów, aby ułatwić rozwiązywanie problemów z weryfikacji. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie funkcji niestandardowej oraz zasady walidacji pakietu dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: uruchamianie kodu w trakcie kroków wdrożeniowych](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Porady: Tworzenie funkcji niestandardowej oraz zasady walidacji pakietu dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
