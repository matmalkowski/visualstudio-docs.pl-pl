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
ms.openlocfilehash: 4d0bc3185b0684f96bf31cc127cd852448afe772
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765073"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Kompilowanie i debugowanie rozwiązań SharePoint
  Ogólnie rzecz biorąc, kompilowanie i debugowanie rozwiązań SharePoint jest taka sama jak kompilowanie i debugowanie innych typów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. W tematach w tej sekcji opisano różnice, które istnieją.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Dane wyjściowe projektu dla rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint tworzy zestawów i pakietu rozwiązania (*WSP*) pliku. W poniższej tabeli przedstawiono lokalizacje plików podczas kompilacji.  
  
|Tworzenie elementu|Folder wyjściowy|  
|----------------|-------------------|  
|Zestawu, bazy danych programu (*.pdb*), a *WSP* plików.|*{Nazwa_projektu} \bin\debug* lub *\bin\release {nazwa_projektu}*|  
|Pliki elementu projektu SharePoint.|*{Nazwa_projektu} \pkg\debug* lub *\pkg\release {nazwa_projektu}*|  
|Tworzenie plików pośrednich.|*{Nazwa_projektu} \obj\debug* lub *\obj\release {nazwa_projektu}*|  
|Pakiet plików pośrednich.|*{Nazwa_projektu} \pkgobj\debug* lub *\pkgobj\release {nazwa_projektu}*|  
  
## <a name="build-sharepoint-solutions"></a>Kompilowanie rozwiązań SharePoint
 Tworzenie rozwiązań programu SharePoint, na komputerze deweloperskim musi mieć poprawną wersję programu SharePoint server. W przeciwnym razie tworzenie rozwiązań programu SharePoint jest taka sama jak tworzenie innych typów projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: tworzenie rozwiązań programu SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Debugowania i testowania rozwiązań SharePoint
 Przed debugowania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopie *WSP* pakiet do serwera programu SharePoint aktywuje lokacji i funkcji należących do zakresu sieci Web, a w niektórych przypadkach rozpoczyna się projekt. W innych przypadkach może być konieczne ręczne Otwórz projekt. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rozwiązań SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) i [debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
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
  
 