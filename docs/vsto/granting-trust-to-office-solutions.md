---
title: Udziel zaufania do rozwiązań pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfce58ca765e7e3710ecb55a1c84c09f0ee14f52
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447248"
---
# <a name="grant-trust-to-office-solutions"></a>Udziel zaufania do rozwiązań pakietu Office
  Zaufanie GRANT oznacza rozwiązań pakietu Office modyfikowanie zasad zabezpieczeń każdego komputera docelowego zaufania zestawu rozwiązania, manifest aplikacji i manifest wdrażania oraz dokumentu. Zaufania może zostać przydzielony do rozwiązania pakietu Office przez użytkownika lub użytkownika końcowego.  
  
 Po zarejestrowaniu manifestów aplikacji i wdrażania, można przyznać pełne zaufanie do rozwiązania pakietu Office.  
  
 Użytkownicy końcowi mogą udzielać dostępu zaufania do rozwiązań pakietu Office przy podejmowaniu decyzji zaufania w [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania wiersza.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Zaufania rozwiązania przez podpisywanie manifestów aplikacji i wdrażania  
 Wszystkich aplikacji i wdrażania manifesty dla pakietu Office rozwiązań muszą być podpisane przy użyciu certyfikatu, który identyfikuje wydawcy. Certyfikaty stanowią podstawę dla podejmowania decyzji dotyczących zaufania.  
  
 Tymczasowy certyfikat jest tworzony i przyznane zaufania w czasie kompilacji, więc rozwiązanie zostanie uruchomiona podczas debugowania jego. W przypadku publikowania rozwiązania, które jest podpisany przy użyciu certyfikatu tymczasowe, użytkownik końcowy wyświetli monit o podjęcie decyzji zaufania.  
  
 Jeśli zarejestrujesz rozwiązania przy użyciu znanego i zaufanego certyfikatu rozwiązania zostaną zainstalowane automatycznie bez monitowania użytkownika końcowego do podjęcia decyzji o zaufaniu. Aby uzyskać więcej informacji o tym, jak uzyskać certyfikat podpisywania, zobacz [ClickOnce i podpis Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Po uzyskaniu certyfikatu, certyfikat musi być jawnie zaufany przez dodanie go do listy zaufanych wydawców. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Jeśli projektant podpisuje rozwiązania przy użyciu tymczasowego certyfikatu, administrator może ponownie podpisać dostosowania przy użyciu znanego i zaufanego certyfikatu przy użyciu Generowanie manifestu i edytowania narzędzia (*mage.exe*), które jest jednym z Microsoft .NET Framework tools. Aby uzyskać więcej informacji na temat podpisywania rozwiązania, zobacz [porady: rozwiązań pakietu Office znak](../vsto/how-to-sign-office-solutions.md) i [porady: podpisania manifestów aplikacji i wdrażania](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Zaufania rozwiązania przy użyciu wiersza zaufania ClickOnce  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monituje użytkownika końcowego dokonanie wyboru zaufania, jeśli nie zasady całej organizacji, które ufają certyfikatu tego rozwiązania. Jeżeli użytkownik końcowy przyznaje zaufania do rozwiązania, tworzony jest wpisu listy dołączania, który zawiera adres URL i klucza publicznego do przechowywania tej decyzji dotyczącej zaufania. Podczas dostosowywania zaufanych jest uruchamiana później, użytkownik końcowy nie jest monitowany ponownie.  
  
 Administratorzy mogą wyłączyć [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufany monit ani nie wymaga się, że monit wystąpić tylko w przypadku rozwiązania, które są podpisane za pomocą certyfikatu Authenticode. Aby uzyskać więcej informacji na temat zmiany tych ustawień dla stref Mój komputer, LocalIntranet Internet, TrustedSites: i UntrustedSites, zobacz [porady: Konfigurowanie zachowania monitu o zaufanie ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Udziel zaufania do dokumentów](../vsto/granting-trust-to-documents.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  