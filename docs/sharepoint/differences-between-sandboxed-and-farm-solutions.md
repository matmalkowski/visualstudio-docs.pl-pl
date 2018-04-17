---
title: Różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy | Dokumentacja firmy Microsoft
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
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2340e7001d159b34bba62e9ba4ef90c34845b156
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Różnice między rozwiązaniami w trybie piaskownicy oraz rozwiązaniami farmy
  Podczas kompilowania rozwiązania programu SharePoint, wdraża programu SharePoint server i dołącza debuger do jego debugowania. Proces wykorzystywany do debugowania rozwiązania zależy od ustawienia właściwości rozwiązania w trybie piaskownicy: rozwiązania typu piaskownica lub rozwiązaniu farmy.  
  
 Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Rozwiązania farmy  
 Rozwiązania farmy, które są obsługiwane w procesie roboczym usług IIS (W3WP.exe), uruchom kod, który może mieć wpływ na całej farmy. Podczas debugowania projektu SharePoint, w których właściwość rozwiązania w trybie piaskownicy ma wartość "rozwiązanie farmy" puli aplikacji usług IIS systemu odtwarza przed SharePoint wycofuje lub wdraża funkcję tak, aby zwolnić wszystkie pliki zablokowany przez proces roboczy usług IIS. Jest tylko pula aplikacji usług IIS obsługujących adres URL witryny projektu programu SharePoint.  
  
## <a name="sandboxed-solutions"></a>Rozwiązania piaskownicy  
 Rozwiązania piaskownicy, które są hostowane w programie SharePoint użytkownika kodu rozwiązania proces roboczy (SPUCWorkerProcess.exe), uruchom kod, który można tylko na zbiorze witryn rozwiązania. Pula aplikacji usług IIS ani serwera IIS ponieważ rozwiązań w trybie piaskownicy nie są uruchamiane w procesie roboczym usług IIS, należy ponownie uruchomić. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza debuger do procesu SPUCWorkerProcess, który automatycznie wyzwala usługi SPUserCodeV4 w programie SharePoint i kontrolek. Nie jest niezbędna dla procesu SPUCWorkerProcess do odtworzenia załadować najnowsza wersja rozwiązania.  
  
## <a name="either-type-of-solution"></a>Wpisz rozwiązania  
 Z dowolnego typu rozwiązanie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] również dołącza debuger do przeglądarki, aby włączyć debugowanie skryptów po stronie klienta. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] używa debugowanie aparatu w tym celu skryptu. Aby włączyć debugowanie skryptów, należy zmienić domyślne ustawienia przeglądarki po wyświetleniu monitu.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza debuger tylko dla procesu W3WP lub SPUCWorkerProcess uruchamiającego bieżącej lokacji. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza również zarządzane COM Plus i aparaty debugowania przepływów pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md)  
  
  