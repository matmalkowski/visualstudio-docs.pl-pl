---
title: Zabezpieczanie wdrożenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1efc8087476cbe879a647288c35a7e7f329100a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="secure-deployment"></a>Wdrażanie zabezpieczeń
  Po utworzeniu rozwiązania do pakietu Office, komputerze dewelopera jest aktualizowane automatycznie uruchamianie kodu w projekcie do uruchomienia. Jednak podczas wdrażania rozwiązania, należy podać dowody, na którym można oprzeć decyzji dotyczącej zaufania rozwiązania przy użyciu certyfikatu podpisywania, lub używając [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monitu o klucz zaufania. Aby uzyskać więcej informacji, zobacz [udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Na poziomie dokumentu wdrożenia dokument w lokalizacji sieciowej, należy również dodać lokalizację dokumentu do listy zaufanych lokalizacji w Centrum zaufania aplikacji pakietu Office. Aby uzyskać więcej informacji o ustawianiu uprawnień do dokumentu na użytkownika końcowego komputerów, zobacz [udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
## <a name="preventing-office-solutions-from-running-code"></a>Uniemożliwia uruchomiony kod rozwiązań pakietu Office  
 Administratorzy mogą używać rejestru, aby uniemożliwić wszystkie rozwiązań pakietu Office na komputerze. Jeśli rozwiązania do pakietu Office, który zarządza rozszerzenia kodu jest otwarty, Visual Studio Tools for Office runtime kontroli czy wpis o nazwie `Disabled` istnieje w jednej z następujących kluczy rejestru na komputerze:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Aby zapobiec uruchamianiu kodu rozwiązań pakietu Office, należy utworzyć `Disabled` wpis w jedną lub obie te klucze rejestru i określić jedną z następujących typów danych i wartości dla `Disabled`:  
  
-   REG_SZ lub REG_EXPAND_SZ skonfigurowanej do dowolnego ciągu znaków innych niż "0" (zero).  
  
-   Wartości REG_DWORD ustawionej wartości innej niż 0 (zero).  
  
 Aby włączyć rozwiązań pakietu Office do uruchomienia kodu, ustaw obie `Disabled` wpisy na 0 (zero), lub Usuń wpisy rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Przygotowywanie komputerów do uruchamiania lub Host rozwiązań pakietu Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  