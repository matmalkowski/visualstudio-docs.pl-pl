---
title: 'Porady: wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint | Dokumentacja firmy Microsoft'
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
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c4f7e347f9cea3a73ab5326b42720a1b2c33529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Porady: wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie SharePoint
  Można wdrożyć lub publikowanie rozwiązań programu SharePoint do lokalnego serwera programu SharePoint na komputerze deweloperskim. Procesu wdrażania kopiuje plik wsp na serwer programu SharePoint, instaluje rozwiązanie, a następnie aktywuje funkcji. Proces publikowania tylko kopiuje plik wsp do serwera programu SharePoint i instaluje je. Należy ręcznie uaktywnić go w celu włączenia go w programie SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Aby wdrożyć rozwiązanie programu SharePoint do lokalnego serwera programu SharePoint  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt, który chcesz wdrożyć.  
  
2.  Na pasku menu wybierz **kompilacji**, **wdrożyć rozwiązanie**.  
  
     Plik wsp jest utworzony i zainstalowany na lokalnym serwerze programu SharePoint. Ponadto funkcje zostaną aktywowane.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Publikowanie rozwiązania SharePoint lokalny serwer SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu programu SharePoint, które chcesz opublikować, a następnie wybierz pozycję **publikowania**.  
  
2.  W **publikowania** oknie dialogowym wybierz **publikowanie w systemie plików** przycisk opcji.  
  
3.  W **lokalizacji docelowej** polu tekstowym wprowadź ścieżkę lokalną, a następnie wybierz **publikowania** przycisku.  
  
     W programie Visual Studio jest wyświetlany postęp publikowania **dane wyjściowe** okna. Po zakończeniu procesu plik rozwiązania (wsp) jest zainstalowany na lokalnym serwerze programu SharePoint. Jednak on nadal należy aktywować do użycia w programie SharePoint. Jeśli istnieje już plik rozwiązania, błąd jest zgłaszany oraz zapyta, czy chcesz zastąpić istniejący plik. Aby uzyskać informacje na temat uaktualniania pakietu, zobacz sekcję dotyczącą uaktualnianie pakietów zdalnych w [porady: wdrażanie, publikowanie i uaktualniania rozwiązań programu SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Porady: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  