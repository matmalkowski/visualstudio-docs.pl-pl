---
title: Rozszerzanie systemu projektu SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 028e7aab10ae1ee1de452e69c8148dac099039d0
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326790"
---
# <a name="extend-the-sharepoint-project-system"></a>Rozszerzanie systemu projektu SharePoint
  Rozwiązania programu SharePoint można utworzyć przy użyciu zestawu szablonów projektu i elementu szablonów w programie Visual Studio. Te szablony spełniają wymagania wielu scenariusze programowania, ale można wykryć niektórych przypadkach, gdy nie zapewniają funkcji, która jest wymagana. W takich przypadkach można rozszerzyć system projektu programu SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Omówienie systemu projektu SharePoint
 System projektu programu SharePoint jest oparty na podstawowym składnikiem *SharePoint — elementy projektu*. Element projektu SharePoint reprezentuje pojedynczy dostosowanie programu SharePoint, takie jak listy definicji, składnik Web Part lub typu zawartości.  
  
 Projekt SharePoint jest projekt programu Visual Studio, który zawiera jeden lub więcej elementów projektu SharePoint. SharePoint — projekty zawiera również dodatkowe składniki, które definiują sposób grupowania elementów projektu do funkcji i pakietów dla wdrożenia.  
  
 Aby uzyskać więcej informacji o zawartości programu SharePoint — elementy projektu i SharePoint — projekty, zobacz [elementu Tworzenie szablonów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Jak rozszerzyć systemu projektu SharePoint
 System projektu programu SharePoint można rozszerzyć w następujący sposób:  
  
-   Definiowanie własnych typów elementów projektu SharePoint i skojarzyć je z nowych szablonów elementu lub szablony projektów programu Visual Studio. Na przykład można zdefiniować typu elementu projektu SharePoint do tworzenia niestandardowych akcji lub pola. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Rozszerzanie typów elementów projektu SharePoint, które są już zainstalowane w programie Visual Studio. Na przykład można dodać pozycji menu skrótów do elementu projektu w **Eksploratora rozwiązań** i dostosować elementu projektu, gdy projektant wybierze elementu menu. Aby uzyskać więcej informacji, zobacz [rozszerzyć SharePoint — elementy projektu](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Rozszerzanie projektów SharePoint. Na przykład można dodać obsługi zdarzeń do wykonywania określonych zadań, gdy elementy są dodawane lub usuwane z projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [rozszerzyć SharePoint — projekty](../sharepoint/extending-sharepoint-projects.md).  
  
-   Rozszerzanie pakowania i wdrażania zachowanie SharePoint — elementy projektu i SharePoint — projekty. Na przykład można utworzyć własne kroki wdrażania do wykonania podczas wdrażania lub wycofać projektu albo można wykonać dodatkowe zadania niestandardowych podczas niektóre kroki wdrażania programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pakowania i wdrażania SharePoint rozszerzyć](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Typowych zadań rozwoju
 Można wykonywać następujące typowe zadania w rozszerzeniach systemu projektu SharePoint:  
  
-   Zapisz niestandardowy ciąg danych z elementów projektu i kilka typów plików projektu. Aby uzyskać więcej informacji, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Konwersja obiektu systemu projektu SharePoint do odpowiedniego obiektu w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji, albo na odwrót. Aby uzyskać więcej informacji, zobacz [Skonwer pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Zobacz także
 [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Rozszerzanie elementów projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  
