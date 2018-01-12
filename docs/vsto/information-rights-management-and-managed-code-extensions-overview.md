---
title: "Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego ― omówienie | Dokumentacja firmy Microsoft"
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
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 561f17acd17cb34892d3f2d4f0eefa05dfced0e4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego ― Omówienie
  Microsoft Office Word i Microsoft Office Excel umożliwiają zarządzanie prawami informacji (IRM), funkcji, które mogą pomóc zapobiec osoby nieupoważnione wyświetlanie lub zmienianie poufne informacje. Aby uzyskać szczegółowe informacje dotyczące sposobu działania zarządzania prawami do informacji zobacz Pomoc w określonej aplikacji pakietu Office.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>Wykonywanie kodu w tle dokumentów z ograniczonymi uprawnieniami  
 Jeśli rozwiązanie zawiera dokument lub skoroszytu, który używa funkcji IRM, domyślnie, Word i Excel nie zezwalają na dowolny kod do uruchomienia. Jeśli autor dokumentu lub mają pełną kontrolę dostępu, można zmienić domyślne tak, aby Twoje rozwiązanie działa. Aby uzyskać więcej informacji, zobacz [porady: zezwolenie na kod, aby uruchomić za dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM uniemożliwia korzystanie z <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> można pobrać lub manipulować danymi zbuforowana w dokumencie.  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>Użytkownicy końcowi ograniczanie uprawnień do dokumentów, które używają rozszerzenia kodu zarządzanego  
 Aby ograniczyć uprawnienia, każdy, kto ma dostęp do pełnej kontroli do dokumentu lub skoroszyt w rozwiązaniu korzystać z tej funkcji. Na przykład jeśli użytkownik końcowy w dziale księgowości używa rozwiązania, które automatycznie wypełni arkusza z danymi z bazy danych, użytkownik może chcesz zezwolić Zmień dostęp tylko do osób w dziale własnego i dostęp do odczytu do innych użytkowników. Gdy użytkownik dodaje ograniczone uprawnienia, domyślnie nie może uruchomić kod związany z arkusza i arkusza nie zostaną wypełnione z danymi.  
  
 Aby rozwiązać ten problem, dostęp Pełna kontrola do dokumentu lub skoroszytu zmienić domyślne ustawienia uprawnień umożliwiających programistyczny dostęp do modelu obiektów. Aby uzyskać więcej informacji, zobacz [porady: zezwolenie na kod, aby uruchomić za dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Projektowanie i tworzenie rozwiązań Office](../vsto/designing-and-creating-office-solutions.md)  
  
  