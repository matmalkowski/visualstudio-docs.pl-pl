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
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 21431cd16407d61db6f981aad68d52906c2de1f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
  