---
title: Zarządzane odniesienia (Office development w Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3c991b6507ded441dd37ec92cb5efd0e2167285
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572195"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Zarządzane odniesienia (Office development w Visual Studio)
  Ta sekcja zawiera dokumentacji interfejsu API dla obszarów nazw i typy, które są używane w pakiecie Office projektów przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Dla dokumentacji interfejsu API o obszary nazw i typy, które są używane w projektach pakietu Office, które odnoszą się do programu .NET Framework 3.5, zobacz następującą sekcję informacyjną w dokumentacji programu Visual Studio: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="in-this-section"></a>W tej sekcji  
 <xref:Microsoft.Office.Tools>  
 Zawiera klasy, które są wspólne dla programowania rozwiązań pakietu Office. Należą do klasy podstawowej dodatków VSTO, klas do tworzenia niestandardowych okienek zadań w dodatkach VSTO, klasy służące do tworzenia tagów inteligentnych w rozwiązaniach programu Excel i Word i klasy tworzenia okienka akcji w dostosowaniach na poziomie dokumentu.  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Zawiera formanty hosta i hosta elementów, których można użyć w rozwiązaniach dla programu Excel.  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Zawiera formanty programu Excel i formanty formularzy systemu Windows, których można użyć w rozwiązaniach dla programu Excel.  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Zawiera klasy używane przez dodatków narzędzi VSTO dla programu Outlook, łącznie z klasy, które są używane do tworzenia regionów formularzy niestandardowych.  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 Zawiera klasy, które są używane do modyfikowania programowo dostosowań Wstążki utworzone za pomocą projektanta wstążki.  
  
 <xref:Microsoft.Office.Tools.Word>  
 Zawiera formanty hosta i hosta elementów, których można użyć w rozwiązaniach dla programu Word.  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Zawiera formanty programu Word i formanty formularzy systemu Windows, których można użyć w rozwiązaniach dla programu Word.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 Zawiera <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy i zestawu powiązanych klas danych w pamięci podręcznej. Te klasy mogą służyć do modyfikowania niektórych aspektów dostosowań na poziome dokumentu na komputerach, które nie mają zainstalowany w Microsoft Office.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 Zawiera <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfejsu (które można zaimplementować w celu utworzenia *post akcji wdrażania* dla rozwiązań pakietu Office), wyjątków, które mogą być generowane podczas instalowania rozwiązania do pakietu Office i innych interfejsów API, które są częścią elementu wizualnego Infrastruktura Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 Zawiera większość wyjątków, które mogą być generowane przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], kilka klas, które mogą służyć do danych w pamięci podręcznej w dostosowaniach na poziomie dokumentu i innych interfejsów API, które są częścią infrastruktury programu Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Zawiera klasy zadań programu MSBuild, które są używane do tworzenia projektów pakietu Office.  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia Visual Studio tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
  
  