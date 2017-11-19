---
title: "Wdrażanie, publikowanie i aktualizowanie pakietów rozwiązania SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ae973b0a1fc30f0592f6cb2702df645708ab43f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>Wdrażanie, publikowanie i aktualizowanie pakietów rozwiązania SharePoint
  Po tworzenia rozwiązań programu SharePoint w Visual Studio, można wdrożyć pliku pakietu (wsp) na lokalny serwer SharePoint lub opublikować go do lokalnego lub zdalnego serwera programu SharePoint. W przypadku wdrożenia z plików, można dostosować, sposób wdrożenia pliki pakietu (wsp).  
  
> [!NOTE]  
>  Obecnie tylko rozwiązań w trybie piaskownicy mogą być publikowane na serwerach zdalnych programu SharePoint. Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploying-publishing-and-upgrading"></a>Wdrażanie, publikowanie i uaktualnianie  
 *Wdrażanie* odwołuje się do kopiowania pliku rozwiązania programu SharePoint skompilowane z projektu programu SharePoint w Visual Studio dla hosta lokalnego. W rozwiązaniu wdrożone można skonfigurować kroków wdrażania, takie jak odtwarzanie puli usług Internet Information Services (IIS), aktywacja po wdrożeniu rozwiązania i tak dalej. Aby wdrożyć, użyj **Wdróż** na **kompilacji** menu. Aby uzyskać więcej informacji, zobacz [porady: edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) i [porady: wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Publikowanie* odwołuje się do przekazywania pliku rozwiązania piaskownicy programu SharePoint do zdalnego programu SharePoint lokacji; oznacza to, że znajduje się w innym systemie lokacji. Można również opublikować plik rozwiązania w trybie piaskownicy programu SharePoint w lokalnej witrynie programu SharePoint, ale niezależnie od tego, czy witryny, opublikowane w lokalnym lub zdalnym, nie można skonfigurować jego kroki wdrażania.  
  
 *Uaktualnianie* odwołuje się do aktualizacji istniejącego zdalnie lub lokalnie opublikowanych rozwiązania programu SharePoint. Po wszelkich zmian do rozwiązania programu SharePoint w Visual Studio, możesz zmienić nazwę pliku pakietu rozwiązania, ponownie opublikować rozwiązania, a następnie Uaktualnij rozwiązanie po pomyślnym publikuje ponownie. Jeśli ponownie opublikować lokalnie opublikowanych rozwiązania można zastąpić istniejącego pliku rozwiązania.  
  
## <a name="deploying-packages"></a>Wdrażanie pakietów  
 Pliki pakietu do serwera programu SharePoint można wdrożyć na komputerze deweloperskim, testowanie i debugowanie. Można również utworzyć plik pakietu, który można zainstalować na innym komputerze, wybierając **publikowanie w systemie plików** przycisków opcji w **publikowania** okno dialogowe. Pakiet jest utworzony i skopiowany do folderu określonego pliku lokalnego. Aby wdrożyć rozwiązanie programu SharePoint na serwerze lokalnym, należy użyć **Wdróż** na **kompilacji** menu. Aby uzyskać więcej informacji, zobacz [porady: wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Aby dowiedzieć się, jak wdrażanie definicji listy, Dodaj odbiorcy zdarzeń i użyj funkcji projektanta i projektanta pakietów, zobacz [wskazówki: Wdrażanie definicji listy zadań projektu](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customizing-the-deployment-process"></a>Dostosowywanie procesu wdrażania  
 W poniższej tabeli przedstawiono z dwiema konfiguracjami wdrożenia używanych podczas debugowania i wdrażania rozwiązania programu SharePoint.  
  
|Konfiguracja wdrażania|Opis|  
|------------------------------|-----------------|  
|Domyślny|Domyślna konfiguracja wdrożenia. Wykonywane są następujące kroki wdrażania:<br /><br /> 1.  Uruchom polecenie przed wdrożeniem.<br />2.  Odtwórz pulę aplikacji usług IIS.<br />3.  Wycofywanie rozwiązania.<br />4.  Dodaj rozwiązanie.<br />5.  Aktywacja funkcji.<br />6.  Uruchom polecenie po wdrożeniu.<br /><br /> Po odinstalowaniu pakietu są wykonywane następujące kroki wycofywania.<br /><br /> 1.  Odtwórz pulę aplikacji usług IIS.<br />2.  Wycofywanie rozwiązania.|  
|Nie aktywacji|Konfiguracja wdrożenia uruchamia te same kroki jako konfiguracji domyślnej, ale pomija krok aktywacji.|  
  
 Możesz utworzyć własne konfiguracji wdrażania, aby ukończyć pojedynczy krok lub zmiana kolejności kroków w ramach procesu wdrażania. Aby uzyskać więcej informacji, zobacz [porady: edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 Można również dodać polecenia do uruchomienia przed i po wdrożeniu. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie poleceń wdrażania SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>Publikowanie pakietów do serwera lokalnego lub zdalnego  
 Publikowanie rozwiązania w trybie piaskownicy programu SharePoint na serwerze zdalnym, na pasku menu wybierz **kompilacji**, **publikowania**, a następnie w **publikowania** okno dialogowe Wybierz **Publikowania do witryny SharePoint** przycisk opcji, podając adres URL zdalnego serwera, takich jak **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 Publikowanie rozwiązania SharePoint na serwerze lokalnym, w **publikowania** oknie dialogowym wybierz **publikowanie w systemie plików** przycisk opcji, podając ścieżkę systemu lokalnego.  
  
 Po rozwiązaniu pomyślnie publikuje do programu SharePoint, rozwiązanie zdaje się w **galerii rozwiązań** gdzie możesz to zrobić. Aby uzyskać więcej informacji, zobacz [porady: wdrażanie, publikowanie i uaktualniania rozwiązań programu SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrading-published-packages"></a>Uaktualnianie opublikowane pakiety  
 Jeśli zostaną wprowadzone zmiany do projektu SharePoint w Visual Studio po opublikowaniu opublikowanego pakietu muszą zostać uaktualnione, aby uwzględnić zmiany. Aby pomyślnie uaktualnić, pakiet musi mieć unikatową nazwę. Jeśli pakiet o takiej samej nazwie znajduje się w witrynie programu SharePoint — które mogą wystąpić podczas aktualizowania istniejących aplikacji — alerty o błędach na nazwę pliku w konflikcie i pozwala zmienić nazwę pakietu. Po ponownie opublikować, nowy pakiet pojawia się w witrynie programu SharePoint i może zostać uaktualniony. Uaktualnionego pakietu aktualizacji rozwiązania przy użyciu danych z starszej pakiet, a następnie aktywuje rozwiązań w programie SharePoint. Aby uzyskać więcej informacji, zobacz [porady: wdrażanie, publikowanie i uaktualniania rozwiązań programu SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  