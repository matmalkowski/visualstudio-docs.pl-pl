---
title: 'Porady: zmiana maszyny odtwarzania diagnostyki grafiki | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33d2acc46cbf92c9b2bbd699903ad3169661a54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684896"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Porady: zmiana maszyny odtwarzania diagnostyki grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: zmiana maszyny odtwarzania diagnostyki grafiki](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-change-the-graphics-diagnostics-playback-machine).  
  
Można odtwarzać informacji graficznych przy użyciu komputera lokalnego lub za pomocą zdalnym komputerze lub urządzeniu.  
  
## <a name="choosing-a-playback-machine"></a>Wybieranie komputera odtwarzania  
 Maszyna odtwarzania jest komputerem lub urządzeniem, który służy do odtwarzania zdarzenia grafiki z dziennika grafiki. Zwykle komputer lokalny to najwygodniejsza opcja, ale problem z renderowaniem może być nie do odtworzenia na komputerze, który ma innej sprzętowej lub wersjach sterowników niż komputer, w której został przechwycony; w takiej sytuacji można wybrać zdalny komputer do odtwarzania konfiguracji problemu i nadal używać komputera deweloperskiego do diagnozowania.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Aby użyć komputera lokalnego do odtwarzania informacji graficznych  
  
1.  W oknie dokumentu dziennika grafiki, wybierz **maszynę odtwarzającą** łącza. **Połączenia zdalnego debugera** pojawi się okno dialogowe.  
  
2.  W obszarze **Konfiguracja ręczna**w **adres** właściwości wprowadź `localhost`.  
  
3.  Ustaw **tryb uwierzytelniania** właściwości **Brak**.  
  
4.  Wybierz **wybierz** przycisku.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Aby użyć komputera zdalnego do odtwarzania informacji graficznych  
  
1.  W oknie dokumentu dziennika grafiki, wybierz **maszynę odtwarzającą** łącza. **Połączenia zdalnego debugera** pojawi się okno dialogowe.  
  
2.  W obszarze **Konfiguracja ręczna**w **adres** właściwość, wprowadź nazwę domeny Windows lub adres IP komputera lub urządzenia, które chcesz użyć do odtwarzania informacji graficznych.  
  
3.  Określ rodzaj autoryzacji, którego chcesz użyć do zabezpieczenia połączenia z komputerem odtwarzania.  
  
    -   W przypadku uwierzytelniania Windows ustaw **tryb uwierzytelniania** właściwości **Windows**.  
  
    -   Aby nie używać uwierzytelniania, należy ustawić **tryb uwierzytelniania** właściwości **Brak**.  
  
4.  Wybierz **wybierz** przycisku.  
  
> [!NOTE]
>  **Połączenia zdalnego debugera** okno dialogowe mogą być również wyświetlane obiekty docelowe debugowania zdalnego, które są podłączone bezpośrednio do komputera deweloperskiego lub znajdują się w tej samej podsieci. Można użyć jednej z tych celów zdalnego debugowania jako maszyny odtwarzania diagnostyki grafiki bez ręcznej konfiguracji. W **połączenia zdalnego debugera** okna dialogowego Wybierz element docelowy ma, a następnie wybierz **wybierz** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokument dziennika grafiki](../debugger/graphics-log-document.md)



