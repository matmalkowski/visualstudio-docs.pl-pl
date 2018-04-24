---
title: 'ASP.NET debugowanie: Wymagania systemu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a0d591c9f68e5331b2047ee749fff148c8844937
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Debugowanie: wymagania systemu
W tym temacie opisano wymagania programowe i zabezpieczeń dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debugowania scenariusze:  
  
-   Debugowanie lokalne, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i aplikacji sieci Web, uruchom na tym samym komputerze. Istnieją dwie wersje tego scenariusza:  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Kod znajduje się w systemie plików.  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Kod znajduje się w witrynie sieci Web usług IIS.  
  
-   Debugowanie zdalne, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest uruchamiany na komputerze klienckim i debuguje aplikacji sieci Web, w której jest uruchomiona na komputerze serwera zdalnego.  
  
## <a name="security-requirements"></a>Wymagania dotyczące zabezpieczeń  
 Zdalne debugowanie komputerów lokalnych i zdalnych musi znajdować się na Instalatora domeny lub grupy roboczej.  
  
 Aby debugować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy (obsługiwanych przez pulę aplikacji), musi mieć uprawnienia do debugowania tego procesu. Domyślnie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji przed ich usług IIS 6.0, Uruchom jako **ASPNET** użytkownika. W usługach IIS 6.0 i IIS 7.0 **usługi SIECIOWEJ** konta jest ustawieniem domyślnym. Jeśli proces roboczy jest uruchomiona jako **ASPNET**, lub jako **usługi SIECIOWEJ**, musisz mieć uprawnienia administratora do jego debugowania.

 > [!IMPORTANT]
 > Począwszy od systemu Windows Server 2008 R2, firma Microsoft zaleca użycie [puli](/iis/manage/configuring-security/application-pool-identities) jako tożsamość, dla każdej puli aplikacji.
  
 Nazwa [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy zmienia się za pomocą debugowania scenariusza i wersji programu IIS. Aby uzyskać więcej informacji, zobacz [porady: znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Użytkownika można zmienić konto, które [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uruchamiania procesu roboczego w obszarze, edytując plik machine.config na serwerze, na którym działa program IIS. W tym celu najlepiej jest użycie **Internet Information Services (IIS) Manager**. Aby uzyskać więcej informacji, zobacz [porady: Uruchom konta procesu roboczego w obszarze użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Jeśli zmienisz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego służącego do uruchamiania własnego konta użytkownika, nie trzeba być administratorem na serwerze, na którym działa program IIS.  
  
> [!CAUTION]
>  Przed wprowadzeniem zmian w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego służącego do uruchamiania przy użyciu innego konta, należy wziąć pod uwagę powiadomienia o możliwych konsekwencjach Jeśli [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego powinien zaatakowane uruchomionej na tym koncie. Uruchom ASPNET i Usługa sieciowa kont użytkowników z minimalnymi uprawnieniami, zmniejsza ryzyko uszkodzenia, jeśli proces jest zaatakowane. Jeśli musisz zmienić [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego służącego do uruchamiania przy użyciu konta mającego większe uprawnienia, potencjalne szkody jest większa.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Porady: uruchamianie procesu roboczego na koncie użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md)