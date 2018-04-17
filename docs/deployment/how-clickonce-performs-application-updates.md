---
title: Jak technologia ClickOnce wykonuje aktualizacje aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 942c37f693ada43eef1fc329d9c9b7092f150229
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-clickonce-performs-application-updates"></a>Jak technologia ClickOnce wykonuje aktualizacje aplikacji
ClickOnce używa informacji o wersji pliku określona w manifeście wdrażania aplikacji, aby zdecydować, czy należy zaktualizować pliki aplikacji. Po rozpoczęciu aktualizacji ClickOnce stosowana jest metoda o nazwie *plik poprawki* Aby uniknąć nadmiarowe pobierania plików aplikacji.  
  
## <a name="file-patching"></a>Plik poprawki  
 Podczas aktualizacji aplikacji, ClickOnce nie pobiera wszystkie pliki do nowej wersji aplikacji, chyba że zostały zmienione pliki. Zamiast tego porównuje sygnatury skrótu pliki określone w manifeście aplikacji dla bieżącej aplikacji przed podpisów w manifeście dla nowej wersji. W przypadku różnych podpisów plików ClickOnce pobiera nowej wersji. Jeśli podpisy są zgodne, plik nie został zmieniony z jedną wersję do następnego. W takim przypadku ClickOnce kopiuje istniejącego pliku i używa go w nowej wersji aplikacji. Takie podejście zapobiega konieczności pobierania całej aplikacji ponownie, nawet jeśli tylko jeden lub dwa pliki zostały zmienione ClickOnce.  
  
 Plik poprawki działa także dla zestawów, które są pobierane na żądanie przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> i <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metody.  
  
 Kompilowanie aplikacji za pomocą programu Visual Studio spowoduje wygenerowanie nowe sygnatury skrótu dla wszystkich plików zawsze, gdy odbudować całego projektu. W takim przypadku wszystkie zestawy zostanie pobrana na klienta, mimo że tylko kilka zestawów mógł ulec zmianie.  
  
 Plik poprawki nie działa w przypadku plików, które są oznaczone jako dane i przechowywane w katalogu danych. Te są zawsze pobierane niezależnie od sygnatury skrótu pliku. Aby uzyskać więcej informacji o katalogu danych, zobacz [dostęp do lokalnych i zdalnych danych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)