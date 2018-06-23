---
title: Kompilowanie i debugowanie rozwiązań SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cf89354880059b8fe743e5558b2c406467a38014
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326117"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Kompilowanie i debugowanie rozwiązań SharePoint
  Ogólnie rzecz biorąc, kompilowanie i debugowanie rozwiązań SharePoint jest taka sama jak kompilowanie i debugowanie innych typów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. W tematach w tej sekcji opisano różnice, które istnieją.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Dane wyjściowe projektu dla rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint tworzy zestawów i pakietu rozwiązania (*WSP*) pliku. W poniższej tabeli przedstawiono lokalizacje plików podczas kompilacji.  
  
|Tworzenie elementu|Folder wyjściowy|  
|----------------|-------------------|  
|Zestawu, bazy danych programu (*.pdb*), a *WSP* plików.|*\<ProjectName > \bin\debug* lub  *\<ProjectName > \bin\release*|  
|Pliki elementu projektu SharePoint.|*\<ProjectName > \pkg\debug* lub  *\<ProjectName > \pkg\release*|  
|Tworzenie plików pośrednich.|*\<ProjectName > \obj\debug* lub  *\<ProjectName > \obj\release*|  
|Pakiet plików pośrednich.|*\<ProjectName > \pkgobj\debug* lub  *\<ProjectName > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Kompilowanie rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint, na komputerze deweloperskim musi mieć poprawną wersję programu SharePoint server. W przeciwnym razie tworzenie rozwiązań programu SharePoint jest taka sama jak tworzenie innych typów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: rozwiązań SharePoint kompilacji](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Debugowania i testowania rozwiązań SharePoint
 Przed debugowania, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopie *WSP* pakiet do serwera programu SharePoint aktywuje lokacji i funkcji należących do zakresu sieci Web, a w niektórych przypadkach rozpoczyna się projekt. W innych przypadkach może być konieczne ręczne Otwórz projekt. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md) i [rozwiązań SharePoint debugowania](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>Debugowanie i sprawdź rozwiązań programu SharePoint przy użyciu funkcji ALM
 Visual Studio ALM funkcje takie jak testy jednostkowe i IntelliTrace włączyć więcej problemów znaleźć dokładnie w ramach rozwiązań programu SharePoint. Profilowanie umożliwia lokalizację i identyfikację problemów wydajności w ramach rozwiązań programu SharePoint. Aby uzyskać więcej informacji, zobacz [weryfikacji i debugowanie kodu aplikacji programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) i [profilowanie wydajności aplikacji SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Zabezpieczeń podczas procesu kompilacji
 Do pakietu lub wdrożenia rozwiązań SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] musi mieć uprawnienie do kopiowania plików do serwera programu SharePoint. Należy uruchomić [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako procesów z podwyższonym poziomem uprawnień i użytkownika konto musi być administratorem kolekcji witryn na serwerze programu SharePoint. Ponadto należy określić, czy projekt jest rozwiązania typu piaskownica lub rozwiązaniu farmy. Aby uzyskać więcej informacji, zobacz [różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Za pomocą polecenia Clean  
 Rozwiązania programu SharePoint jest zainstalowany na serwerze programu SharePoint do debugowania, **wyczyść** polecenie nie powoduje odinstalowania rozwiązania. Zamiast tego należy dezaktywować funkcji za pomocą konfiguracji programu SharePoint.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Pakiet i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 
