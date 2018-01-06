---
title: "Udzielanie zaufania do rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
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
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8d4e1e92eab8def99a67b7da531770bb2dd58fc0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="granting-trust-to-office-solutions"></a>Udzielanie zaufania do rozwiązań pakietu Office
  Udzielanie zaufania do rozwiązań pakietu Office oznacza modyfikowanie zasad zabezpieczeń każdego komputera docelowego zaufania zestawu rozwiązania, manifest aplikacji i manifest wdrażania oraz dokumentu. Zaufania może zostać przydzielony do rozwiązania pakietu Office przez użytkownika lub użytkownika końcowego.  
  
 Po zarejestrowaniu manifestów aplikacji i wdrażania, można przyznać pełne zaufanie do rozwiązania pakietu Office.  
  
 Użytkownicy końcowi mogą udzielać dostępu zaufania do rozwiązań pakietu Office przy podejmowaniu decyzji zaufania w [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania wiersza.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a>Manifesty ufające rozwiązania przez podpisywanie aplikacji i wdrażania  
 Wszystkich aplikacji i wdrażania manifesty dla pakietu Office rozwiązań muszą być podpisane przy użyciu certyfikatu, który identyfikuje wydawcy. Certyfikaty stanowią podstawę dla podejmowania decyzji dotyczących zaufania.  
  
 Tymczasowy certyfikat jest tworzony i przyznane zaufania w czasie kompilacji, więc rozwiązanie zostanie uruchomiona podczas debugowania jego. W przypadku publikowania rozwiązania, które jest podpisany przy użyciu certyfikatu tymczasowe, użytkownik końcowy wyświetli monit o podjęcie decyzji zaufania.  
  
 Jeśli zarejestrujesz rozwiązania przy użyciu znanego i zaufanego certyfikatu rozwiązania zostaną zainstalowane automatycznie bez monitowania użytkownika końcowego do podjęcia decyzji o zaufaniu. Aby uzyskać więcej informacji o tym, jak uzyskać certyfikat podpisywania, zobacz [ClickOnce i podpis Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Po uzyskaniu certyfikatu, certyfikat musi być jawnie zaufany przez dodanie go do listy zaufanych wydawców. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Jeśli projektant podpisuje rozwiązania przy użyciu tymczasowego certyfikatu, administrator może ponownie podpisać dostosowania przy użyciu znanego i zaufanego certyfikatu przy użyciu Generowanie manifestu i narzędzia do edycji (mage.exe), które jest jednym z narzędzi programu Microsoft .NET Framework. Aby uzyskać więcej informacji na temat podpisywania rozwiązania, zobacz [porady: rozwiązań pakietu Office znak](../vsto/how-to-sign-office-solutions.md) i [jak: logowania aplikacji i manifestów wdrożenia](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Ufające rozwiązania przy użyciu wiersza zaufania ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]monituje użytkownika końcowego dokonanie wyboru zaufania, jeśli nie zasady całej organizacji, które ufają certyfikatu tego rozwiązania. Jeżeli użytkownik końcowy przyznaje zaufania do rozwiązania, tworzony jest wpisu listy dołączania, który zawiera adres URL i klucza publicznego do przechowywania tej decyzji dotyczącej zaufania. Podczas dostosowywania zaufanych jest uruchamiana później, użytkownik końcowy nie jest monitowany ponownie.  
  
 Administratorzy mogą wyłączyć [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufany monit ani nie wymaga się, że monit wystąpić tylko w przypadku rozwiązania, które są podpisane za pomocą certyfikatu Authenticode. Aby uzyskać więcej informacji na temat zmiany tych ustawień dla stref Mój komputer, LocalIntranet Internet, TrustedSites: i UntrustedSites, zobacz [porady: Konfigurowanie zachowania monitu o zaufanie ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Określone zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  