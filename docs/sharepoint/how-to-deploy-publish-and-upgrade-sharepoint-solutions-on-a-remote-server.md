---
title: 'Porady: wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fbd21016d00bdfecfcb606e9fe2b720ab97bf3d0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120310"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Porady: wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym
  Oprócz wdrażania rozwiązań programu SharePoint na system lokalny, lokacje zdalne lub lokalnych witryn programu SharePoint można opublikować rozwiązań w trybie piaskownicy programu SharePoint. Zdalne kopie proces publikowania *WSP* pliku na serwerze programu SharePoint instaluje rozwiązanie, a następnie umożliwia Aktywuj. Możesz również uaktualnić zdalnej instalacji rozwiązania programu SharePoint, po wprowadzeniu zmian do niego.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Aby opublikować rozwiązania w trybie piaskownicy programu SharePoint do zdalnego serwera programu SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów w trybie piaskownicy projektu programu SharePoint, który chcesz opublikować, a następnie wybierz pozycję **publikowania**.  
  
2.  W **publikowania** oknie dialogowym wybierz **publikowania do witryny SharePoint** przycisk opcji, a następnie wprowadź adres URL witryny do publikowania online, takich jak: `https://mytestsite.sharepoint.microsoftonline.com`.  
  
3.  Wybierz **Otwórz stronę galerii rozwiązań w przeglądarce po opublikowaniu** przycisk opcji, aby wyświetlić listę rozwiązań w **galerii rozwiązań** strony po opublikowaniu.  
  
4.  Wybierz **publikowania** przycisku.  
  
5.  Zaloguj się na serwerze zdalnym, jeśli wymagane jest uwierzytelnienie użytkownika.  
  
     W programie Visual Studio jest wyświetlany postęp publikowania **dane wyjściowe** okna. Po zakończeniu procesu, rozwiązania (*WSP*) plik jest zainstalowany na zdalnym serwerze programu SharePoint. Jednak on nadal należy aktywować zanim będzie można go używać w programie SharePoint.  
  
6.  Na **galerii rozwiązań** wybierz aplikacji programu SharePoint, a następnie na Wstążce wybierz **Aktywuj** przycisku.  
  
7.  W **aktywować rozwiązania** okno dialogowe, na Wstążce wybierz **Aktywuj** przycisk ponownie.  
  
     **Stan** kolumny na **galerii rozwiązań** strony wskazuje, że aplikacja jest aktywna.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Aby uaktualnić rozwiązania w trybie piaskownicy programu SharePoint na serwerze zdalnym programu SharePoint  
 Jeśli rozwiązania w trybie piaskownicy programu SharePoint został już opublikowany na serwerze zdalnym, następujący proces umożliwia ją uaktualnić po wprowadzeniu zmian do aplikacji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Zmień nazwę pakietu programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby to zrobić, w **Eksploratora rozwiązań** Otwórz pakiet. Wygląda na to w **Explorer pakietu**.  
  
2.  W **Explorer pakietu**w **nazwa** Zmień nazwę pakietu do unikatową nazwę.  
  
3.  Zapisz projekt.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **publikowania**.  
  
5.  W **publikowania** oknie dialogowym wybierz **publikowania do witryny SharePoint** przycisk opcji, a następnie, jeśli brakuje adresu URL dla serwera zdalnego, w której jest zapisywany rozwiązania, wprowadź go.  
  
6.  Wybierz **Otwórz stronę galerii rozwiązań w przeglądarce po opublikowaniu** przycisk opcji, aby wyświetlić listę rozwiązań w **galerii rozwiązań** strony po opublikowaniu.  
  
7.  Wybierz **publikowania** przycisku.  
  
8.  Zaloguj się na serwerze zdalnym, jeśli wymagane jest uwierzytelnienie użytkownika.  
  
     Jeśli użytkownik zalogował się ze zdalnym serwerem ostatnio, uwierzytelniania nie może być wymagane.  
  
     Jeśli starszej wersji aplikacji, która ma taką samą nazwę, która jest nadal istnieje na serwerze programu SharePoint, wystąpi błąd, który pakiet o takiej samej nazwie już istnieje na serwerze programu SharePoint. Należy zmienić nazwę pakietu na nazwę unikatową przed opublikowaniem.  
  
9. Wybierz nową aplikację w programie SharePoint, a następnie na Wstążce wybierz **uaktualnienia** przycisku.  
  
10. W **Uaktualnij rozwiązanie** okno dialogowe, na Wstążce wybierz **uaktualnienia** przycisk ponownie. **Stan** kolumny na **galerii rozwiązań** strony teraz powinny wskazywać, że aplikacja jest aktywna.  
  
     Stara wersja rozwiązania jest dezaktywowany, nowa wersja rozwiązania jest uaktualniony przy użyciu danych zachowywanych z rozwiązania do starego i nowego rozwiązania została aktywowana w programie SharePoint.  
  
## <a name="see-also"></a>Zobacz także
 [Porady: wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Porady: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
