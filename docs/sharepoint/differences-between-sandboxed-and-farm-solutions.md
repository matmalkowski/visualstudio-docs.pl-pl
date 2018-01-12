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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c9123f028bab5319f47e4bdc0ada0dbbee49bc2c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
 [Uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md)  
  
  