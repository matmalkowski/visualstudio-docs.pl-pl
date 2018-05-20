---
title: Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego ― omówienie
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35a118774d50bcc697cd3ff5663fc26d8580ac88
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego ― omówienie
  Microsoft Office Word i Microsoft Office Excel umożliwiają zarządzanie prawami informacji (IRM), funkcji, które mogą pomóc zapobiec osoby nieupoważnione wyświetlanie lub zmienianie poufne informacje. Aby uzyskać szczegółowe informacje dotyczące sposobu działania zarządzania prawami do informacji zobacz Pomoc w określonej aplikacji pakietu Office.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami  
 Jeśli rozwiązanie zawiera dokument lub skoroszytu, który używa funkcji IRM, domyślnie, Word i Excel nie zezwalają na dowolny kod do uruchomienia. Jeśli autor dokumentu lub mają pełną kontrolę dostępu, można zmienić domyślne tak, aby Twoje rozwiązanie działa. Aby uzyskać więcej informacji, zobacz [porady: zezwalanie kodu do uruchomienia w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM uniemożliwia korzystanie z <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> można pobrać lub manipulować danymi zbuforowana w dokumencie.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Użytkownicy końcowi, aby ograniczyć uprawnienia do dokumentów, które używają rozszerzenia kodu zarządzanego  
 Aby ograniczyć uprawnienia, każdy, kto ma dostęp do pełnej kontroli do dokumentu lub skoroszyt w rozwiązaniu korzystać z tej funkcji. Na przykład jeśli użytkownik końcowy w dziale księgowości używa rozwiązania, które automatycznie wypełni arkusza z danymi z bazy danych, użytkownik może chcesz zezwolić Zmień dostęp tylko do osób w dziale własnego i dostęp do odczytu do innych użytkowników. Gdy użytkownik dodaje ograniczone uprawnienia, domyślnie nie może uruchomić kod związany z arkusza i arkusza nie zostaną wypełnione z danymi.  
  
 Aby rozwiązać ten problem, dostęp Pełna kontrola do dokumentu lub skoroszytu zmienić domyślne ustawienia uprawnień umożliwiających programistyczny dostęp do modelu obiektów. Aby uzyskać więcej informacji, zobacz [porady: zezwalanie kodu do uruchomienia w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
  
  