---
title: 'Porady: Określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbb3214df1cd51baf731f8a16f39b2c5a59933bb
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078745"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Porady: Określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki dokumentu szczegóły dotyczące instalowanie, inicjowanie, aktualizowania i odinstalowywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Aby zwiększyć szczegóły, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapisu do tych plików dziennika, użyj Edytora rejestru (*regedit.exe*) można określić poziom szczegółowości.  
  
> [!CAUTION]
>  Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.  
  
 Poniższa procedura opisuje sposób określić poziom szczegółowości dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki dziennika dla bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.  
  
### <a name="to-specify-verbose-log-files"></a>Aby określanie plików pełnego dziennika  
  
1.  Otwórz *Regedit.exe*.  
  
2.  Przejdź do węzła **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.  
  
3.  Jeśli to konieczne, Utwórz nową wartość ciągu o nazwie `LogVerbosityLevel`.  
  
4.  Ustaw `LogVerbosityLevel` wartość `1`.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)