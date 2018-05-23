---
title: 'Błąd: Serwer sieci Web nie mógł znaleźć żądanego zasobu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e6fec89a151525a84349b7019c7569eb752172e
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Błąd: serwer sieci Web nie mógł znaleźć żądanego zasobu
Z powodu zagadnienia dotyczące zabezpieczeń usługi IIS zwrócił błąd ogólny.  
  
 Jedną z możliwych przyczyn jest to konfiguracja zabezpieczeń serwera. Usług IIS 6.0 i starszych wersjach używane programu dodatkowego, znany jako URLScan, Filtrowanie żądań podejrzane i nieprawidłowo sformułowany. Usług IIS 7.0 ma taką samą funkcję filtrowania żądań wbudowanych. W obu przypadkach funkcja filtrowania żądań zbyt restrykcyjne uniemożliwia Visual Studio debugowanie serwera.  
  
 Istnieje wiele możliwych przyczyn tego błędu. Kilka najbardziej typowe przyczyny obejmują problem z instalacji usług IIS lub konfiguracji, konfiguracja witryny sieci web lub uprawnień w systemie plików. Możesz spróbować uzyskać dostęp do zasobu w przeglądarce. W zależności od sposobu skonfigurowania usług IIS może być konieczne na serwerze przy użyciu przeglądarki sieci lokalnej lub Sprawdź dziennik błędów programu IIS, aby uzyskać szczegółowy komunikat o błędzie.  
  
 Aby uzyskać więcej informacji na temat usuwania usług IIS, zobacz [zarządzania usługami IIS i administrowanie](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Zobacz też  
 [Błąd: Serwer sieci Web został zablokowany i blokuje zlecenie DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)