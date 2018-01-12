---
title: "Ochrona za pomocą hasła w dokumentach pakietu Office | Dokumentacja firmy Microsoft"
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
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 52cadcec85580a9214da844bf887323227490f22
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="password-protection-on-office-documents"></a>Ochrona za pomocą hasła w dokumentach pakietu Office
  Użytkownik może ustawić hasło dla dokumentów pakietu Microsoft Office Word i skoroszytów programu Microsoft Office Excel, aby nie można otworzyć przez osobę, która nie może określić hasło. Ta opcja jest nazywany **hasła podczas otwierania**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Można tworzyć projektów na poziomie dokumentu przy użyciu istniejących dokumentów i skoroszytów, które mają **hasła podczas otwierania** włączone. W programie Visual Studio jest różny dla dokumentów programu Word i Excel, których **hasła podczas otwierania** włączone.  
  
 Aby uzyskać informacje na temat włączania **hasła podczas otwierania**, zobacz Pomoc programu Word czy Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Zachowanie programu Excel i Word  
 Za każdym razem, gdy Otwórz skoroszyt programu Excel w programie Visual Studio, który ma **hasła podczas otwierania** włączona, program Excel wyświetla monit o hasło. Podczas kompilowania rozwiązania pojawi się monit o podanie hasła ponownie, ponieważ dokument jest otwarty podczas kompilacji.  
  
 Przy pierwszym otwarciu dokumentu programu Word w Visual Studio, który ma **hasła podczas otwierania** włączony, użytkownik jest monitowany o podanie hasła. Po wprowadzeniu hasła, **hasła podczas otwierania** zostanie usunięty z dokumentu i otworzyć dokument nie będzie już potrzebować hasła. Jeśli chcesz dokumentu w rozwiązaniu wymagane jest hasło, zanim będzie można otworzyć, musisz włączyć **hasła podczas otwierania** po ostatnim kompilację i przed wdrożeniem rozwiązania.  
  
## <a name="see-also"></a>Zobacz też  
 [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego ― omówienie](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Porady: zezwalanie na uruchamianie w tle dokumentów z ograniczonymi uprawnieniami kodu](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Projektowanie i tworzenie rozwiązań Office](../vsto/designing-and-creating-office-solutions.md)  
  
  