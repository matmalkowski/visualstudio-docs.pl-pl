---
title: "Porady: debugowanie hostowania samoobsługowego WCF | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e64f764153106c252ba1a9586bfd0a33f4e239f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Porady: debugowanie hostowania samoobsługowego WCF
A *usługi hosta samodzielnego* to usługa WCF, która nie jest uruchamiane w usługach IIS, Host usługi WCF, lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Najprostszym sposobem debugowanie hostowania samoobsługowego WCF jest skonfigurowanie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można uruchomić klienta i serwera, po wybraniu **Rozpocznij debugowanie** na **debugowania** menu.  
  
 Jeśli usługa WCF jest hostingu samodzielnego wewnątrz lub proces, który nie można uruchomić w ten sposób, na przykład usługi NT, nie można użyć tej metody. Zamiast tego możesz wybrać jedną z następujących czynności:  
  
-   Ręcznie dołączyć debuger do procesu hostingu. Aby uzyskać więcej informacji, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     — lub —  
  
-   Rozpocznij debugowanie klienta, a następnie wkroczyć do połączenia z usługą. Wymaga włączenia debugowania w pliku app.config. Aby uzyskać więcej informacji [ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Aby uruchomić klienta i hosta w programie Visual Studio  
  
1.  Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania zawierającego projekty zarówno klient, jak i serwer.  
  
2.  Konfigurowanie rozwiązania pod kątem uruchamiania procesów klienta i serwera, po wybraniu **Start** na **debugowania** menu.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę rozwiązania.  
  
    2.  Kliknij przycisk **Ustawianie projektów startowych**.  
  
    3.  W **rozwiązania \<name > właściwości** okno dialogowe, wybierz opcję **wiele projektów startowych**.  
  
    4.  W **wiele projektów startowych** siatki w wierszu, który odpowiada Projekt serwera, kliknij przycisk **akcji** i wybierz polecenie **Start**.  
  
    5.  W wierszu, który odpowiada projektu klienta, kliknij przycisk **akcji** i wybierz polecenie **Start**.  
  
    6.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Porady: Wkrocz do usługi WCF](../debugger/how-to-step-into-wcf-services.md)