---
title: Wytyczne dotyczące importowania wielokrotnych przepływów danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 57ca59e7e31cabde62128d2e56df45c4819cfb65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Wytyczne dotyczące importowania wielokrotnych przepływów danych
  Aby zaimportować wielokrotnych przepływów pracy tworzonych w programie SharePoint Designer, należy użyć szablonu projektu zaimportować programu SharePoint 2010 przepływu pracy wielokrotnego użytku w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Ten szablon importuje *deklaratywne* *przepływu pracy* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-tylko) i konwertuje ją na *kodu przepływu pracy*, czyli przepływu pracy, które mogą poprawić przy użyciu jednej [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] kodu. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Wskazówki: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Jednak szablonu importowanie wielokrotnego użytku z wersji 2010 przepływu pracy programu SharePoint można importować tylko rozwiązania farmy. Jeśli chcesz wdrożyć przepływu pracy jako rozwiązanie w trybie piaskownicy, należy go zaimportować przy użyciu szablonu Importowanie pakietu rozwiązania programu SharePoint 2010. Jednak w ten sposób, nie można przekonwertować go do kodu przepływu pracy i nie będzie można modyfikować jej jako takie.  
  
## <a name="importing-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importowania wielokrotnych przepływów danych przy użyciu szablonu importowania przepływu pracy wielokrotnego użytku  
 Po zaimportowaniu przepływu pracy wielokrotnego użytku przy użyciu szablonu importowania programu SharePoint 2010 przepływu pracy wielokrotnego użytku, możesz uruchomić lub zmienić rozwiązania, podobnie jak każdy inny [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązania programu SharePoint, ale może być konieczne ręczne rozwiązać niektóre elementy.  
  
### <a name="importing-task-forms"></a>Importowanie formularze zadań  
 Szablon projektu przepływu pracy importowania wielokrotnego użytku z wersji programu SharePoint 2010 importuje wszystkie formularzy inicjowania i skojarzenia, ale importuje tylko jedno zadanie formularza, ponieważ schemat przepływu pracy kodu zezwala na tylko jeden formularz zadania. Formularze wszelkie dodatkowe zadania z oryginalnym rozwiązaniu przepływu pracy są umieszczane w **inne pliki zaimportowane** folderu w **Eksploratora rozwiązań**.  
  
## <a name="importing-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importowania wielokrotnych przepływów danych przy użyciu szablonu pakietu importu programu SharePoint 2010 rozwiązania  
 Po zaimportowaniu przepływu pracy wielokrotnego użytku przy użyciu szablonu Importowanie pakietu rozwiązania programu SharePoint 2010, należy wziąć pod uwagę następujące kwestie:  
  
-   Po zaimportowaniu przepływu pracy, można natychmiast wdrożyć i uruchomić go w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wybierając klawisz F5. Jednak w przypadku zmiany niczego w przepływie pracy w rozwiązaniu zaimportowane, może być konieczne ręcznie rozwiązać elementy w projekcie, aby można było wdrożyć i Uruchom przepływ pracy.  
  
-   Ponieważ deklaracyjnego przepływu pracy, kodu nie można dodać do niego. Aby przekonwertować kod przepływu pracy przepływu pracy, należy zaimportować go do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu szablonu importowanie wielokrotnego użytku z wersji 2010 przepływu pracy programu SharePoint.  
  
-   Podczas można edytować plik projektanta (xoml) przepływu pracy w widoku Projekt, zaleca się edytować w widoku źródła, ponieważ projektanta przepływów pracy przedstawia błędy wartość false.  
  
-   Debugowanie w przepływie pracy nie działa, deklaratywne zawartości. Ustawić punktów przerwania w [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] nie są osiągane.  
  
## <a name="importing-globally-reusable-workflow-solutions"></a>Importowanie rozwiązań do wielokrotnego użytku globalnego przepływu pracy  
 Nie można zaimportować globalny wielokrotnych przepływów danych przy użyciu szablonu przepływu pracy importowania wielokrotnego użytku programu SharePoint 2010. Aby zaimportować do wielokrotnego użytku globalnego przepływu pracy, należy konwertować — globally wielokrotnego przepływu lub należy użyć szablonu Importowanie pakietu rozwiązania programu SharePoint 2010.  
  
 Aby dokonać konwersji przepływu pracy, należy utworzyć kopię do wielokrotnego użytku globalnego przepływu pracy w programie SharePoint Designer (Otwieranie menu skrótów dla przepływu pracy, a następnie wybierając **Zapisz jako kopię**). Następnie zaimportuj nowego przepływu pracy wielokrotnego użytku z szablonem zaimportować programu SharePoint 2010 przepływu pracy wielokrotnego użytku w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Aby zaimportować do wielokrotnego użytku globalnego przepływu pracy bez modyfikowania jej, użyj szablonu Importowanie pakietu rozwiązania programu SharePoint 2010. Jeśli używasz tej metody, przepływ pracy nie jest konwertowany na kod przepływu pracy i pozostaje deklaracyjnego przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Przewodnik: Importowanie przepływu danych wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  