---
title: Tworzenie rozwiązań pakietu Office | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b84334ac4454760c7457f131a9cd438f715a78ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="developing-office-solutions"></a>Tworzenie rozwiązań pakietu Office
  Po projektowania projektu za pomocą narzędzia Office developer tools w programie Visual Studio i konfigurowanie plików projektu, można rozpocząć skoncentrować się na realizacji kodu i niestandardowego interfejsu użytkownika (UI).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="office-solutions-programming-model"></a>Model programowania rozwiązań pakietu Office  
 Model obiektów pakietu Office udostępnia różnych obiektów, które można zaprogramować przed. Zawsze, gdy programowania rozwiązań pakietu Office za pomocą kodu zarządzanego pisania kodu, który używa typów w podstawowe zestawy międzyoperacyjne pakietu Office. W przypadku rozwiązań tworzonych przy użyciu szablonów projektu pakietu Office w Visual Studio również napisać kod bezpośrednio przed wygenerowane klasy w projekcie. Aby uzyskać więcej informacji, zobacz [pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="programming-different-types-of-office-solutions"></a>Programowanie różnego rodzaju rozwiązań pakietu Office  
 Typ rozwiązania, które tworzysz Określa funkcje, których można użyć w projekcie. Na przykład można Dodaj formanty formularzy systemu Windows i formanty rozszerzone pakietu Office (o nazwie *hostowania formantów*) na poziomie dokumentu przez przeciąganie elementów z **przybornika** w programie Visual Studio w czasie projektowania . Jednak jeśli tworzysz dodatku VSTO można tylko dodać tego rodzaju formantów do dokumentów w czasie wykonywania, pisanie kodu.  
  
 Aby uzyskać więcej informacji o funkcjach, które są specyficzne dla różnych typów rozwiązań zobacz następujące tematy:  
  
-   [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   [Programowanie dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
-   [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
 Aby uzyskać ogólne informacje ułatwiające zaplanować procedury ułatwiające tworzenie projektów i rozwiązań pakietu Office, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)|Zawiera opis różnych aspektów pisanie kodu w rozwiązaniach pakietu Office.|  
|[Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)|Omówienie modelu programowania dodatków narzędzi VSTO i powiązanych zadań programistycznych.|  
|[Programowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)|Omówienie modelu programowania dostosowań na poziomie dokumentu i powiązanych zadań programistycznych.|  
|[Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)|W tym artykule opisano różne sposoby, który można dostosować aplikacji interfejsu użytkownika pakietu Office za pomocą dodatków narzędzi VSTO i dostosowywanie na poziomie dokumentu.|  
|[Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)|W tym artykule opisano różne sposoby, w którym można pracować z danymi w rozwiązaniach pakietu Office, takich jak buforowanie danych w dostosowaniach na poziomie dokumentu i wiązanie danych do kontrolek.|  
|[Wpływ automatycznego zapisywania na rozwiązania pakietu Office](./how-autosave-impacts-office-solutions.md)|W tym artykule opisano zmiany należy wprowadzić rozwiązań pakietu Office, gdy jest włączone automatyczne zapisywanie.|
|[Rozwiązywanie problemów z rozwiązaniami Office](../vsto/troubleshooting-office-solutions.md)|Zawiera wskazówki dotyczące rozwiązywania problemów, które można napotkać podczas tworzenia rozwiązań pakietu Office.|  
|[Obsługa wątkowości w pakiecie Office](../vsto/threading-support-in-office.md)|Zawiera omówienie pracy z wielu wątków w rozwiązaniach pakietu Office.|  
|[Ułatwienia dostępu w projektach pakietu Office](../vsto/accessibility-in-office-projects.md)|Zawiera opis funkcji ułatwień dostępu, które są dostępne w rozwiązaniach pakietu Office.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Porady: Odczyt z oraz zapisywanie właściwości dokumentów](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Porady: docelowa Office wielojęzyczny interfejs użytkownika](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  