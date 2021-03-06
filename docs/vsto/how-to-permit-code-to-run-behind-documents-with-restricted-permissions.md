---
title: 'Porady: zezwalanie kodu do uruchomienia w tle dokumentów z ograniczonymi uprawnieniami'
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
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3b02afb7008233c720feae179b4726f9958a44af
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255289"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Porady: zezwalanie kodu do uruchomienia w tle dokumentów z ograniczonymi uprawnieniami
  Aby ograniczyć uprawnienia do dokumentu lub skoroszytu, można użyć funkcji zarządzania prawami do informacji (IRM) pakietu Microsoft Office. Domyślnie kod związany z ograniczeniami dokumentu Microsoft Office Word lub skoroszyt programu Microsoft Office Excel nie jest dozwolone do uruchomienia. Rozszerzenia kodu zarządzanego mogą uzyskiwać dostęp do modelu obiektów, a Twoje rozwiązanie będzie działać, można zmienić domyślny.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Musi być Autor dokumentu lub skoroszytu lub mają dostęp Pełna kontrola, aby można było zmienić ustawienia uprawnień.  
  
## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Aby umożliwić kodu do uruchomienia w tle dokumentów z ograniczonymi uprawnieniami  
  
1.  Otwórz dokument lub skoroszyt w Word czy Excel.  
  
2.  Kliknij przycisk **pliku** karcie, wskaż pozycję **Prepare**, wskaż **Ogranicz uprawnienia**, a następnie kliknij przycisk **dostęp ograniczony**.  
  
    > [!NOTE]  
    >  Przy pierwszym użyciu monit o zainstalowanie klienta usługi Windows Rights Management. Po zainstalowaniu klienta może być konieczne Powtórz kroki.  
  
3.  W **uprawnienia** okno dialogowe, wybierz opcję **Ogranicz uprawnienia do tego dokumentu**, a następnie kliknij przycisk **więcej opcji**.  
  
4.  W obszarze **dodatkowe uprawnienia dla użytkowników**, wybierz pozycję **programowy dostęp do zawartości**.  
  
 Word czy Excel pozwoli na dostęp programistyczny do modelu obiektu.  
  
## <a name="see-also"></a>Zobacz także  
 [Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego ― omówienie](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  