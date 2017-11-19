---
title: "Różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d82bc012b2be9736b83fc07f7d0a83d354dda002
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy
  Podczas kompilowania rozwiązania programu SharePoint, wdraża programu SharePoint server i dołącza debuger do jego debugowania. Proces wykorzystywany do debugowania rozwiązania zależy od ustawienia właściwości rozwiązania w trybie piaskownicy: rozwiązania typu piaskownica lub rozwiązaniu farmy.  
  
 Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Rozwiązania farmy  
 Rozwiązania farmy, które są obsługiwane w procesie roboczym usług IIS (W3WP.exe), uruchom kod, który może mieć wpływ na całej farmy. Podczas debugowania projektu SharePoint, w których właściwość rozwiązania w trybie piaskownicy ma wartość "rozwiązanie farmy" puli aplikacji usług IIS systemu odtwarza przed SharePoint wycofuje lub wdraża funkcję tak, aby zwolnić wszystkie pliki zablokowany przez proces roboczy usług IIS. Jest tylko pula aplikacji usług IIS obsługujących adres URL witryny projektu programu SharePoint.  
  
## <a name="sandboxed-solutions"></a>Rozwiązania piaskownicy  
 Rozwiązania piaskownicy, które są hostowane w programie SharePoint użytkownika kodu rozwiązania proces roboczy (SPUCWorkerProcess.exe), uruchom kod, który można tylko na zbiorze witryn rozwiązania. Pula aplikacji usług IIS ani serwera IIS ponieważ rozwiązań w trybie piaskownicy nie są uruchamiane w procesie roboczym usług IIS, należy ponownie uruchomić. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dołącza debuger do procesu SPUCWorkerProcess, który automatycznie wyzwala usługi SPUserCodeV4 w programie SharePoint i kontrolek. Nie jest niezbędna dla procesu SPUCWorkerProcess do odtworzenia załadować najnowsza wersja rozwiązania.  
  
## <a name="either-type-of-solution"></a>Wpisz rozwiązania  
 Z dowolnego typu rozwiązanie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] również dołącza debuger do przeglądarki, aby włączyć debugowanie skryptów po stronie klienta. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]używa debugowanie aparatu w tym celu skryptu. Aby włączyć debugowanie skryptów, należy zmienić domyślne ustawienia przeglądarki po wyświetleniu monitu.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dołącza debuger tylko dla procesu W3WP lub SPUCWorkerProcess uruchamiającego bieżącej lokacji. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dołącza również zarządzane COM Plus i aparaty debugowania przepływów pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Zagadnienia dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md)  
  
  