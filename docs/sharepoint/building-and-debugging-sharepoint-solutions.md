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
ms.openlocfilehash: e04f60ea5cfe72235bac6630b413c9c437255681
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691290"
---
# <a name="building-and-debugging-sharepoint-solutions"></a>Kompilowanie i debugowanie rozwiązań SharePoint
  Ogólnie rzecz biorąc, kompilowanie i debugowanie rozwiązań SharePoint jest taka sama jak kompilowanie i debugowanie innych typów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. W tematach w tej sekcji opisano różnice, które istnieją.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Dane wyjściowe projektu dla rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint tworzy zestawów i rozwiązania pakietu (wsp). W poniższej tabeli przedstawiono lokalizacje plików podczas kompilacji.  
  
|Tworzenie elementu|Folder wyjściowy|  
|----------------|-------------------|  
|Zestaw, bazy danych programu (PDB) i pliki WSP.|*ProjectName*\bin\debug lub *ProjectName*\bin\release|  
|Pliki elementu projektu SharePoint.|*ProjectName*\pkg\debug lub *ProjectName*\pkg\release|  
|Tworzenie plików pośrednich.|*ProjectName*\obj\debug lub *ProjectName*\obj\release|  
|Pakiet plików pośrednich.|*ProjectName*\pkgobj\debug lub *ProjectName*\pkgobj\release|  
  
## <a name="build-sharepoint-solutions"></a>Kompilowanie rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint, na komputerze deweloperskim musi mieć poprawną wersję programu SharePoint server. W przeciwnym razie tworzenie rozwiązań programu SharePoint jest taka sama jak tworzenie innych typów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: tworzenie rozwiązań programu SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Debugowania i testowania rozwiązań SharePoint
 Przed debugowania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopiuje pakiet WSP na serwer programu SharePoint, aktywuje lokacji i funkcji należących do zakresu sieci Web i w niektórych przypadkach uruchamia projektu. W innych przypadkach może być konieczne ręczne Otwórz projekt. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rozwiązań SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) i [debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>Debugowanie i sprawdź rozwiązań programu SharePoint przy użyciu funkcji ALM
 Visual Studio ALM funkcje takie jak testy jednostkowe i IntelliTrace włączyć więcej problemów znaleźć dokładnie w ramach rozwiązań programu SharePoint. Profilowanie umożliwia lokalizację i identyfikację problemów wydajności w ramach rozwiązań programu SharePoint. Aby uzyskać więcej informacji, zobacz [weryfikacji i debugowanie kodu aplikacji programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) i [profilowanie wydajności aplikacji SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Zabezpieczeń podczas procesu kompilacji
 Do pakietu lub wdrożenia rozwiązań SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] musi mieć uprawnienie do kopiowania plików do serwera programu SharePoint. Należy uruchomić [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako procesów z podwyższonym poziomem uprawnień i użytkownika konto musi być administratorem kolekcji witryn na serwerze programu SharePoint. Ponadto należy określić, czy projekt jest rozwiązania typu piaskownica lub rozwiązaniu farmy. Aby uzyskać więcej informacji, zobacz [różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Za pomocą polecenia Clean  
 Rozwiązania programu SharePoint jest zainstalowany na serwerze programu SharePoint do debugowania, **wyczyść** polecenie nie powoduje odinstalowania rozwiązania. Zamiast tego należy dezaktywować funkcji za pomocą konfiguracji programu SharePoint.  
  
## <a name="see-also"></a>Zobacz także
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 