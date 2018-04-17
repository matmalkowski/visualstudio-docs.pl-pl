---
title: Dostosowywanie funkcji interfejsu użytkownika korzystając z rozszerzalności interfejsów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 59a2eb15dcb21158df33b2f4a8ae138c424795cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-ui-features-by-using-extensibility-interfaces"></a>Dostosowywanie funkcji interfejsu użytkownika korzystając z rozszerzalności interfejsów
  Narzędzia Office development w Visual Studio Podaj klas i projektantów, które obsługują wiele szczegóły implementacji używanych do tworzenia niestandardowych okienek zadań, dostosowań Wstążki i regionów formularzy programu Outlook w dodatku VSTO. Jednak można też wdrożyć *rozszerzalności interfejsu* dla każdej funkcji samodzielnie, jeśli mają szczególne wymagania.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="overview-of-extensibility-interfaces"></a>Przegląd rozszerzalności interfejsów  
 Microsoft Office definiuje zestaw rozszerzalności interfejsów, które dodatków COM VSTO można zaimplementować w celu dostosowania niektórych funkcji, takich jak wstążki. Te interfejsy zapewniają pełną kontrolę nad funkcje, które zapewniają dostęp do. Jednak implementacja te interfejsy rutynowych współdziałanie COM w kodzie zarządzanym. W niektórych przypadkach model programowania z tych interfejsów również nie jest intuicyjne dla deweloperów, którzy są przystosowane do programu .NET Framework.  
  
 Podczas tworzenia dodatku VSTO przy użyciu szablonów projektu pakietu Office w Visual Studio, nie trzeba implementować interfejsów rozszerzalności, aby dostosować funkcje, takie jak wstążki. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Implementuje te interfejsy dla Ciebie. Zamiast tego można użyć bardziej intuicyjne klasy i projektantów dostarczane przez program Visual Studio. Jednak nadal zaimplementowaniem rozszerzalności interfejsów bezpośrednio w dodatku VSTO z aby.  
  
 Aby uzyskać więcej informacji na temat klas i projektantów, których program Visual Studio udostępnia tych funkcji, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md), [projektanta wstążki](../vsto/ribbon-designer.md), i [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Rozszerzalność interfejsów, które można zaimplementować w dodatku narzędzi VSTO  
 W poniższej tabeli wymieniono rozszerzalności interfejsów, które można zaimplementować i aplikacje, które je obsługują.  
  
|Interface|Opis|Aplikacje|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementuje ten interfejs do dostosowywania wstążki interfejsu użytkownika. **Uwaga:** można dodać **wstążki (XML)** elementu do projektu, aby wygenerować domyślną <xref:Microsoft.Office.Core.IRibbonExtensibility> implementacja użytkownika dodatku VSTO. Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementuje ten interfejs do tworzenia niestandardowego okienka zadań.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementuje ten interfejs do tworzenia regionów formularzy programu Outlook.|Outlook|  
  
 Istnieje kilka interfejsy rozszerzeń, w których są definiowane przez Microsoft Office, takich jak <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>, i <xref:Microsoft.Office.Core.SignatureProvider>. Program Visual Studio nie obsługuje wdrażanie tych interfejsów w Add VSTO utworzone przy użyciu szablonów projektu pakietu Office.  
  
## <a name="using-extensibility-interfaces"></a>Przy użyciu rozszerzalności interfejsów  
 Aby dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsu rozszerzalności, zaimplementuj odpowiedni interfejs w projekcie dodatku VSTO. Następnie zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> sposób zwrócenia wystąpienia klasy, która implementuje interfejs.  
  
 Przykładową aplikację prezentującą implementowania <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, i <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> interfejsy w dodatku VSTO dla programu Outlook, zobacz przykład interfejsu użytkownika menedżera w [Office Development ― przykłady](../vsto/office-development-samples.md).  
  
### <a name="example-of-implementing-an-extensibility-interface"></a>Przykład Implementowanie interfejsu rozszerzalności  
 W poniższym przykładzie kodu pokazano prosty implementacja <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> interfejs do tworzenia niestandardowego okienka zadań. W tym przykładzie definiuje dwie klasy:  
  
-   `TaskPaneHelper` Klasa implementuje <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> można tworzyć i wyświetlać niestandardowego okienka zadań.  
  
-   `TaskPaneUI` Klasa udostępnia interfejs użytkownika w okienku zadań. Wartości atrybutów `TaskPaneUI` klasy uwidaczniania klasy COM, który umożliwia aplikacjom Microsoft Office odnajdywanie klasy. W tym przykładzie interfejsu użytkownika jest pusta <xref:System.Windows.Forms.UserControl>, ale można dodawać formanty modyfikacji kodu.  
  
    > [!NOTE]  
    >  Do udostępnienia `TaskPaneUI` klasy dla modelu COM, należy także ustawić **Zarejestruj dla międzyoperacyjności z modelem COM** właściwości projektu.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]  
  
 Aby uzyskać więcej informacji o implementacji <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, zobacz [tworzenie okienka zadań niestandardowych pakietu 2007 Office System](http://msdn.microsoft.com/en-us/256313db-18cc-496c-a961-381ed9ca94be) w dokumentacji programu Microsoft Office.  
  
### <a name="example-of-overriding-the-requestservice-method"></a>Przykład przesłaniania metody RequestService  
 W poniższym przykładzie pokazano, jak zastąpić <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> sposób zwrócenia wystąpienia klasy `TaskPaneHelper` klasy z poprzednim przykładzie kodu. Sprawdza wartość *serviceGuid* parametr, aby ustalić, który interfejs, który jest wymagany, a następnie zwraca obiekt, który implementuje ten interfejs.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  