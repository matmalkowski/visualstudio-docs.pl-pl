---
title: "Przegląd właściwości niestandardowego dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 672eaf3ed82a80983b919a37b2aeff4c99621f43
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2018
---
# <a name="custom-document-properties-overview"></a>Niestandardowe właściwości dokumentu ― Omówienie

Podczas kompilowania projektu poziomie dokumentu programu Visual Studio dodaje dwie właściwości niestandardowych do dokumentu w projekcie: \_AssemblyLocation i \_AssemblyName. Po otwarciu dokumentu aplikacji Microsoft Office sprawdza te niestandardowe właściwości dokumentu. Jeśli istnieją w dokumencie ładowania aplikacji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], który uruchamia dostosowań. Aby uzyskać więcej informacji, zobacz [architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Ta właściwość zawiera identyfikator CLSID interfejsu w składniku modułu ładującego rozwiązań pakietu Office z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Wartość identyfikatora CLSID jest 4E3C66D5 58D 4-491E-A7D4-64AF99AF6E8B. Nigdy nie należy zmieniać tej wartości.

## <a name="assemblylocation"></a>\_AssemblyLocation

Ta właściwość zawiera ciąg, który zawiera szczegółowe informacje o manifeście rozmieszczenia do dostosowania. Aby uzyskać więcej informacji na temat manifestów zobacz [manifesty wdrożenia w rozwiązaniach pakietu Office i aplikacji](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Wartość właściwości The_AssemblyLocation mogą mieć różnych formatach, w zależności od sposobu wdrażania rozwiązania:

- Jeśli rozwiązanie zostanie opublikowana do zainstalowania z witryny sieci Web, ścieżka UNC lub dysk CD lub dysk USB, _AssemblyLocation właściwość ma format *DeploymentManifestPath*|*SolutionID*. Przykładem jest następujący ciąg:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Jeśli są uruchomione lub debugowanie rozwiązań w programie Visual Studio, _AssemblyLocation właściwość ma format *DeploymentManifestName*|*SolutionID*| vstolocal. Przykładem jest następujący ciąg:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 *SolutionID* jest identyfikatorem GUID który [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] identyfikuje rozwiązania. *SolutionID* jest generowany automatycznie podczas kompilowania projektu. **Vstolocal** wskazuje termin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] czy zestawu powinna być załadowana z tym samym folderze co dokument.

## <a name="see-also"></a>Zobacz także

[Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
[architektura dostosowań na poziome dokumentu](../vsto/architecture-of-document-level-customizations.md)
[aplikacji i wdrażania manifesty w rozwiązaniach pakietu Office ](../vsto/application-and-deployment-manifests-in-office-solutions.md) 
 [Porady: publikowanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
[porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)
