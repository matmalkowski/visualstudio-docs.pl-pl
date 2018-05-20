---
title: Przegląd właściwości niestandardowego dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85dfe077f73a26eadf173197de2ca514ff44679
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="custom-document-properties-overview"></a>Przegląd właściwości niestandardowego dokumentu

Podczas kompilowania projektu poziomie dokumentu programu Visual Studio dodaje dwie właściwości niestandardowych do dokumentu w projekcie: \_AssemblyLocation i \_AssemblyName. Po otwarciu dokumentu aplikacji Microsoft Office sprawdza te niestandardowe właściwości dokumentu. Jeśli istnieją w dokumencie ładowania aplikacji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], który uruchamia dostosowań. Aby uzyskać więcej informacji, zobacz [rozwiązania Architektura pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Ta właściwość zawiera identyfikator CLSID interfejsu w składniku modułu ładującego rozwiązań pakietu Office z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Wartość identyfikatora CLSID jest 4E3C66D5 58D 4-491E-A7D4-64AF99AF6E8B. Nigdy nie należy zmieniać tej wartości.

## <a name="assemblylocation"></a>\_AssemblyLocation

Ta właściwość zawiera ciąg, który zawiera szczegółowe informacje o manifeście rozmieszczenia do dostosowania. Aby uzyskać więcej informacji na temat manifestów zobacz [aplikacji i wdrażania manifesty w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Wartość właściwości The_AssemblyLocation mogą mieć różnych formatach, w zależności od sposobu wdrażania rozwiązania:

- Jeśli rozwiązanie zostanie opublikowana do zainstalowania z witryny sieci Web, ścieżka UNC lub dysk CD lub dysk USB, _AssemblyLocation właściwość ma format *DeploymentManifestPath*|*SolutionID*. Przykładem jest następujący ciąg:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Jeśli są uruchomione lub debugowanie rozwiązań w programie Visual Studio, _AssemblyLocation właściwość ma format *DeploymentManifestName*|*SolutionID*| vstolocal. Przykładem jest następujący ciąg:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

 *SolutionID* jest identyfikatorem GUID który [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] identyfikuje rozwiązania. *SolutionID* jest generowany automatycznie podczas kompilowania projektu. **Vstolocal** wskazuje termin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] czy zestawu powinna być załadowana z tym samym folderze co dokument.

## <a name="see-also"></a>Zobacz także

- [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Manifesty aplikacji i wdrażania rozwiązań pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Porady: publikowanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)
