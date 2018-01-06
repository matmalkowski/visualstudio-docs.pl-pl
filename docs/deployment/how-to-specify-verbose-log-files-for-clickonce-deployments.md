---
title: "Porady: Określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 6cac7764a941e88dd3901a3280e78717955e86b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Porady: określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki dokumentu szczegóły dotyczące instalowanie, inicjowanie, aktualizowanie i odinstalowywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Aby zwiększyć szczegółów który [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapisuje dane w tych plikach dziennika, użyj Edytora rejestru (**regedit.exe**) umożliwia określenie poziomu szczegółowości.  
  
> [!CAUTION]
>  Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.  
  
 W poniższej procedurze opisano sposób określić poziom szczegółowości dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki dziennika dla bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.  
  
### <a name="to-specify-verbose-log-files"></a>Aby określić plików pełnego dziennika  
  
1.  Otwórz **Regedit.exe**.  
  
2.  Przejdź do węzła `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Jeśli to konieczne, Utwórz nową wartość ciągu o nazwie `LogVerbosityLevel`.  
  
4.  Ustaw `LogVerbosityLevel` do wartości `1`.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)