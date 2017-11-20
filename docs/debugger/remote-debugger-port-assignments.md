---
title: "Przypisania portów debugera zdalnego | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb5f72669068855dfcff954faae5dbe6009a52f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debugger-port-assignments"></a>Przypisania portów debugera zdalnego
Zdalny debuger Visual Studio można uruchomić jako aplikacja lub usługa w tle. Po uruchomieniu jako aplikacja wykorzystuje port, który jest domyślnie przypisane w następujący sposób:  

-   Visual Studio 2017:4022

-   Visual Studio 2015:4020  
  
-   Visual Studio 2013:4018  
  
-   Program Visual Studio 2012:4016  
  
 Innymi słowy numer portu przypisany do zdalnego debugera jest zwiększany o 2 dla każdej wersji. Można ustawić inny numer portu z chcesz. Firma Microsoft objaśnia sposób ustawiania numerów portów w dalszej części artykułu.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port debugera zdalnego na 32-bitowe systemy operacyjne  
 4022 TCP (w programie Visual Studio 2017) jest port główny i jest wymagany w przypadku wszystkich scenariuszy. Można to skonfigurować z wiersza polecenia lub okna debugera zdalnego.  
  
 Kliknij w oknie zdalnego debugera **Narzędzia > Opcje**i Ustaw numer portu TCP/IP.  
  
 W wierszu polecenia Uruchom zdalny debuger programu **/port** przełącznika: **polecenie msvsmon/port \<numer portu >**.  
  
 Można znaleźć zdalnego debugera przełączniki wiersza polecenia w Pomocy programu zdalnego debugowania (naciśnij klawisz **F1** lub kliknij przycisk **Pomoc > użycia** w oknie zdalnego debugera).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port debugera zdalnego na 64-bitowe systemy operacyjne  
 Po uruchomieniu 64-bitowej wersji zdalnego debugera, domyślnie używa portu 4022.  Jeśli debugowania procesu 32-bitowego, 64-bitowej wersji zdalnego debugera uruchamia 32-bitowej wersji zdalnego debugera na porcie 4023. Uruchomienie zdalnego debugera 32-bitowy, używa 4022 i 4023 nie jest używany.  
  
 Port ten jest konfigurowane w wierszu polecenia: **/wow64port polecenia Msvsmon \<numer portu >**.  
  
## <a name="the-discovery-port"></a>Port odnajdywania  
 UDP 3702 służy do znajdowania uruchomionych wystąpień zdalnego debugera w sieci (na przykład **znaleźć** okno dialogowe w **dołączyć do procesu** okna dialogowego). Jest on używany tylko w przypadku odnajdywanie komputera z uruchomionym systemem zdalnego debugera, więc jest opcjonalne, jeśli istnieje inny sposób otrzymuje żadnej informacji o nazwę lub adres IP komputera docelowego. To standardowego portu dla odnajdywania, więc nie można skonfigurować numer portu.  
  
 Czy chcesz włączyć funkcję odnajdywania, można uruchomić polecenia msvsmon z wiersza polecenia, z odnajdywaniem wyłączone: **/nodiscovery polecenia Msvsmon**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Zdalny debuger porty na platformie Azure  
 Następujące porty są używane przez debuger zdalny na platformie Azure. Porty usługi w chmurze są mapowane na porty na poszczególnych maszyn wirtualnych. Wszystkie porty są TCP.  
  
||||  
|-|-|-|  
|**Połączenia**|**Port na usługi w chmurze**|**Port na maszynie Wirtualnej**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)