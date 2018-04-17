---
title: Rozszerzanie narzędzi SharePoint w Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d5ad6f27574fcb7bd8a859bcd21ac65e159596e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>Rozszerzanie Narzędzi SharePoint w Visual Studio
  Narzędzia programu SharePoint w Visual Studio wymagań wiele scenariuszy programowania aplikacji. Może jednak odnajdywania przypadków, w którym nie zapewniają funkcje, które wymagają możesz lub innymi deweloperami. W takich przypadkach można rozszerzyć narzędzia programu SharePoint do tworzenia potrzebne funkcje.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Jak rozszerzyć narzędzi SharePoint  
 Można rozszerzyć systemu projektu SharePoint i **połączeń SharePoint** w węźle **Eksploratora serwera** okna.  
  
### <a name="extending-the-sharepoint-project-system"></a>Rozszerzanie systemu projektu SharePoint  
 Visual Studio zawiera zestaw szablonów projektu i szablony elementów, które umożliwia tworzenie rozwiązań programu SharePoint. Na przykład brak szablonów dla odbiorcy zdarzeń, definicje list, przepływy pracy i części sieci Web. Jednak również możliwość definiowania własnych typów SharePoint — elementy projektu do tworzenia składników programu SharePoint, takich jak pola lub akcje niestandardowe. Można również utworzyć rozszerzenia dla typów elementów projektu SharePoint, które są już zainstalowane w programie Visual Studio i tworzenia rozszerzeń dla projektów programu SharePoint.  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera  
 W programie Visual Studio, można użyć **połączeń SharePoint** w węźle**Eksploratora serwera** okna, aby wyświetlić wiele składników jednego lub więcej lokalnych witryn programu SharePoint w hierarchicznym widoku drzewa. Można również rozszerzyć zasięg **połączeń SharePoint** węzła w następujący sposób:  
  
-   Przez dodanie własnych węzłów. Jest to przydatne, jeśli chcesz wyświetlić składniki witryny programu SharePoint, które nie są wyświetlane domyślnie.  
  
-   Rozszerzając istniejących węzłów. Na przykład można dodać nowego węzła podrzędnego do istniejący węzeł, lub można dodać pozycji menu skrótów do węzła i wykonywać zadania, kliknięcie dewelopera elementu menu.  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Wymagania dotyczące komputera programowanie  
 Do tworzenia rozszerzeń dla narzędzi SharePoint, na komputerze deweloperskim musi spełniać te same wymagania dotyczące tworzenia rozwiązań programu SharePoint w Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Zalecamy również zainstalowanie [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Zestaw SDK zawiera szablony projektów i narzędzi, które służą do rozszerzania programu Visual Studio. W szczególności zestaw SDK zawiera szablon projektu, w którym można łatwo utworzyć pakiet rozszerzenia serwera Visual Studio (VSIX). Pakiety VSIX to preferowany sposób wdrażania rozszerzeń programu Visual Studio w programie Visual Studio. Należy wdrożyć wszystkie rozszerzeń narzędzi SharePoint za pomocą pakietów VSIX. Wszystkie przykłady w tej dokumentacji założono, że istnieje [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] zainstalowane.  
  
 Aby zainstalować program Visual Studio SDK, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Aby uzyskać więcej informacji na temat rozszerzeń programu Visual Studio, zobacz [rozpoczyna tworzenie rozszerzenia dla programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie programu SharePoint modelu programowania rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Odwołanie &#40;rozszerzalność narzędzi SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugowanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  