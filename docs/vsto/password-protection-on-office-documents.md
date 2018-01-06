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
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f24c0493a66651a5d95925fd6777ba3e1cdd1658
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
  