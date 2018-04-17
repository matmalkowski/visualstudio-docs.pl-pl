---
title: 'Porady: podpisywanie rozwiązań pakietu Office | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 31b5e1fc3c78aecf518af0941a4a2dd0ab7e57c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-sign-office-solutions"></a>Porady: podpisywanie rozwiązań pakietu Office
  Jeśli zarejestrujesz rozwiązania można przyznać zaufania do rozwiązania jako dowód przy użyciu certyfikatu. Można użyć tego samego certyfikatu dla wielu rozwiązań, a wszystkie rozwiązania pozostaną zaufane, nie dodatkowe aktualizacje zasad.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Jeśli ręcznie edytować aplikację i manifesty wdrożenia przy użyciu Generowanie manifestu i edytowania narzędzia (mage.exe i mageui.exe), należy ponownie podpisać manifestów przed ich użyciem. Aby uzyskać więcej informacji, zobacz [porady: ponowne podpisywanie aplikacji i manifestów wdrożenia](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>Podpisywanie za pomocą certyfikatu  
 Certyfikat jest plik zawierający unikatowego klucza oraz tożsamości wydawcy rozwiązania. Można kupić certyfikatów od urzędu certyfikacji, lub utworzyć własny certyfikat i mieć urzędu certyfikacji, podpisz go.  
  
 Visual Studio podpisuje rozwiązań pakietu Office przy użyciu tymczasowego certyfikatu, aby włączyć debugowanie. Nie należy używać certyfikatu tymczasowe w rozwiązaniach wdrożonego jako dowód.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Aby zarejestrować rozwiązania do pakietu Office przy użyciu certyfikatu  
  
1.  Na **projektu** menu, kliknij przycisk * Nazwa rozwiązania ***właściwości**.  
  
2.  Kliknij przycisk **podpisywanie** kartę.  
  
3.  Wybierz **podpisania manifestów ClickOnce**.  
  
4.  Znajdź certyfikat, klikając **wybierz z magazynu** lub **wybierz z pliku** i przechodząc do certyfikatu.  
  
5.  Aby sprawdzić, czy jest używany prawidłowy certyfikat, kliknij przycisk **więcej szczegółów** do wyświetlania informacji o certyfikacie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)   
 [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)  
  
  