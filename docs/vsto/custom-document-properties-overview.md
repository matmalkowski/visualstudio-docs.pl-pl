---
title: "Przegląd właściwości niestandardowego dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0a670510a7898b38ec7f61a22f8258015b112151
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-document-properties-overview"></a>Niestandardowe właściwości dokumentu ― Omówienie
  Podczas kompilowania projektu poziomie dokumentu programu Visual Studio dodaje dwie właściwości niestandardowych do dokumentu w projekcie: _AssemblyLocation i _AssemblyName. Po otwarciu dokumentu aplikacji Microsoft Office sprawdza te niestandardowe właściwości dokumentu. Jeśli istnieją w dokumencie ładowania aplikacji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], który uruchamia dostosowań. Aby uzyskać więcej informacji, zobacz [architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="assemblyname"></a>_AssemblyName  
 Ta właściwość zawiera identyfikator CLSID interfejsu w składniku modułu ładującego rozwiązań pakietu Office z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Wartość identyfikatora CLSID jest 4E3C66D5 58D 4-491E-A7D4-64AF99AF6E8B. Nigdy nie należy zmieniać tej wartości.  
  
## <a name="assemblylocation"></a>_AssemblyLocation  
 Ta właściwość zawiera ciąg, który zawiera szczegółowe informacje o manifeście rozmieszczenia do dostosowania. Aby uzyskać więcej informacji na temat manifestów zobacz [manifesty wdrożenia w rozwiązaniach pakietu Office i aplikacji](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Wartość właściwości The_AssemblyLocation mogą mieć różnych formatach, w zależności od sposobu wdrażania rozwiązania:  
  
-   Jeśli rozwiązanie zostanie opublikowana do zainstalowania z witryny sieci Web, ścieżka UNC lub dysk CD lub dysk USB, _AssemblyLocation właściwość ma format *DeploymentManifestPath*|*SolutionID*. Przykładem jest następujący ciąg:  
  
     File://deployserver/MyShare/ExcelWorkbook1.VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9  
  
-   Jeśli są uruchomione lub debugowanie rozwiązań w programie Visual Studio, _AssemblyLocation właściwość ma format *DeploymentManifestName*|*SolutionID*| vstolocal. Przykładem jest następujący ciąg:  
  
     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal  
  
 *SolutionID* jest identyfikatorem GUID który [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] identyfikuje rozwiązania. *SolutionID* jest generowany automatycznie podczas kompilowania projektu. **Vstolocal** wskazuje termin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] czy zestawu powinna być załadowana z tym samym folderze co dokument.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Aplikacji i manifestów wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Porady: publikowanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Instrukcje: Tworzenie i modyfikowanie właściwości niestandardowego dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  