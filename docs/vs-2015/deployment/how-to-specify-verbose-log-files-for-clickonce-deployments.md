---
title: 'Porady: Określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce | Dokumentacja firmy Microsoft'
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
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b30260267fca5b7de16316e84082fc3b464f7deb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682842"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Porady: określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Określanie pełne pliki dziennika dla wdrożeń technologii ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-verbose-log-files-for-clickonce-deployments).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki dokumentu szczegóły dotyczące instalowanie, inicjowanie, aktualizowania i odinstalowywania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Aby zwiększyć szczegóły, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zapisu do tych plików dziennika, użyj Edytora rejestru (**regedit.exe**) można określić poziom szczegółowości.  
  
> [!CAUTION]
>  Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.  
  
 Poniższa procedura opisuje sposób określić poziom szczegółowości dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pliki dziennika dla bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.  
  
### <a name="to-specify-verbose-log-files"></a>Aby określanie plików pełnego dziennika  
  
1.  Otwórz **Regedit.exe**.  
  
2.  Przejdź do węzła `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Jeśli to konieczne, Utwórz nową wartość ciągu o nazwie `LogVerbosityLevel`.  
  
4.  Ustaw `LogVerbosityLevel` wartość `1`.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)



