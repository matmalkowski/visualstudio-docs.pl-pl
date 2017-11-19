---
title: "Aplikacji i wdrażania manifesty w rozwiązaniach pakietu Office | Dokumentacja firmy Microsoft"
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
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 822be7f0e6e79f600331197c60ed48ea84cde200
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office
  Manifest aplikacji jest plik XML, który zawiera informacje, które jest używane przez rozwiązania do pakietu Office do lokalizowania i zaktualizuj jego zestawów. Manifest aplikacji można łączyć z manifest wdrażania, który jest plikiem XML przechowywane na serwerze, który zawiera informacje potrzebne do zlokalizowania aktualna wersja umowy manifest aplikacji Kreatora raportów i zestawów.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Struktura manifestu dla rozwiązań pakietu Office  
 Dla rozwiązań Microsoft Office utworzone za pomocą narzędzi programowania pakietu Office w Visual Studio wszystkich manifestów są oparte na standardowych schematu ClickOnce. Podczas wdrażania rozwiązań pakietu Office, manifesty aplikacji dla poziomie dokumentu i projektów dodatku VSTO znajdują się w pamięci podręcznej ClickOnce. Manifesty wdrożenia nie są kopiowane do komputera klienckiego.  
  
 Aby uzyskać informacje dotyczące zawartości aplikacji i manifestów wdrożenia dla projektów pakietu Office, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md) i [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="creating-application-and-deployment-manifests"></a>Tworzenie aplikacji i wdrażania manifesty  
 Manifesty aplikacji są tworzone automatycznie w ramach procesu kompilacji. Zawsze w przypadku kompilowania projektu poziomie dokumentu, lokalizacja manifestu rozmieszczenia jest osadzony w dokumencie jako właściwości niestandardowego dokumentu. Dla dodatków VSTO lokalizacja manifestu rozmieszczenia jest przechowywane w rejestrze.  
  
 Aby uzyskać więcej informacji na temat **Kreator publikowania**, zobacz [wdrażania rozwiązania do pakietu Office za pomocą technologii ClickOnce za pomocą](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Aby uzyskać więcej informacji na temat manifesty współpracują z rozwiązań pakietu Office, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Manifest wdrażania ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  