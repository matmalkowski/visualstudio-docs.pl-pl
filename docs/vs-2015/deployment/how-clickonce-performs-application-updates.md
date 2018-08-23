---
title: Jak technologia ClickOnce wykonuje aktualizacje aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 8011447de248c2dbcdbd513dc4e51106ceb3a568
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682746"
---
# <a name="how-clickonce-performs-application-updates"></a>Jak technologia ClickOnce wykonuje aktualizacje aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak ClickOnce wykonuje aktualizacje aplikacji](https://docs.microsoft.com/visualstudio/deployment/how-clickonce-performs-application-updates).  
  
Technologia ClickOnce używa informacji o wersjach plików, które zostały określone w manifeście wdrożenia aplikacji, aby zdecydować, czy można zaktualizować pliki aplikacji. Po rozpoczęciu aktualizacji, technologia ClickOnce używa technikę o nazwie *plików poprawek* w celu uniknięcia nadmiarowe pobieranie plików aplikacji.  
  
## <a name="file-patching"></a>Poprawianie plików  
 Podczas aktualizowania aplikacji ClickOnce nie pobiera wszystkie pliki do nowej wersji aplikacji, chyba, że pliki zostały zmienione. Zamiast tego porównuje sygnatury skrótu pliki określone w manifeście aplikacji dla bieżącej aplikacji przed podpisów w manifeście dla nowej wersji. W przypadku różnych podpisów plików ClickOnce pliki do pobrania nowej wersji. Jeśli podpisy są zgodne, plik nie zmienił się z jednej wersji do następnego. W tym przypadku ClickOnce kopiuje istniejący plik i używa go w nowej wersji aplikacji. To podejście zapobiega konieczności pobierania ponownie całej aplikacji, nawet jeśli tylko jeden lub dwa pliki zostały zmienione ClickOnce.  
  
 Poprawianie plików działa także dla zestawów, które zostały pobrane na żądanie przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> i <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metody.  
  
 Jeśli używasz programu Visual Studio do kompilowania aplikacji generuje on nowe sygnatury skrótu dla wszystkich plików w każdym przypadku, gdy należy ponownie skompilować cały projekt. W tym przypadku wszystkie zestawy zostaną pobrane do klienta, mimo że tylko kilka zestawów, które mogły ulec zmianie.  
  
 Plik poprawki nie działa dla plików, które są oznaczone jako dane i przechowywane w katalogu danych. Są one zawsze pobierane niezależnie od tego, sygnatury skrótu pliku. Aby uzyskać więcej informacji o katalogu danych, zobacz [Accessing Local and Remote Data in ClickOnce Applications](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



