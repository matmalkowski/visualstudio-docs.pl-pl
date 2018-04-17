---
title: 'Porady: zmiana maszyny odtwarzania diagnostyki grafiki | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 261714c530c2db36b64d7ef07aa19369b3f459bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Porady: zmiana maszyny odtwarzania diagnostyki grafiki
Można odtwarzać informacji graficznych za pomocą komputera lokalnego lub przy użyciu zdalnego komputera lub urządzenia.  
  
## <a name="choosing-a-playback-machine"></a>Wybieranie maszyny odtwarzania  
 Maszynie odtwarzającej jest komputera lub urządzenia, które służy do odtwarzania grafiki zdarzenia z dziennika grafiki. Zazwyczaj komputera lokalnego jest opcją najodpowiedniejszym, jednak problem podczas renderowania nie może odtworzyć na maszynie, która ma sprzętowe lub wersje sterowników niż komputer, w której został przechwycony; w takim przypadku można wybrać na komputerze zdalnym odtwarzania, który lepiej powoduje odtworzenie problemu i nadal używać do diagnozowania jego komputerze deweloperskim.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Aby użyć komputera lokalnego do odtwarzania informacji graficznych  
  
1.  W oknie Dokument dziennika grafiki, wybierz **maszyny odtwarzania** łącza. **Połączenia zdalnego debugera** zostanie wyświetlone okno dialogowe.  
  
2.  W obszarze **konfiguracji ręcznej**w **adres** właściwości, wprowadź `localhost`.  
  
3.  Ustaw **tryb uwierzytelniania** właściwości **Brak**.  
  
4.  Wybierz **wybierz** przycisku.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Do używania maszyny zdalnej, aby odtworzyć informacji graficznych  
  
1.  W oknie Dokument dziennika grafiki, wybierz **maszyny odtwarzania** łącza. **Połączenia zdalnego debugera** zostanie wyświetlone okno dialogowe.  
  
2.  W obszarze **konfiguracji ręcznej**w **adres** właściwości, wpisz nazwę domeny systemu Windows lub adres IP komputera lub urządzenia, które chcesz użyć do odtwarzania informacji graficznych.  
  
3.  Określ rodzaj autoryzacji, który ma być używany do bezpiecznego połączenia z maszyną odtwarzania.  
  
    -   Uwierzytelniania systemu Windows, należy ustawić **tryb uwierzytelniania** właściwości **Windows**.  
  
    -   Bez uwierzytelniania można ustawić **tryb uwierzytelniania** właściwości **Brak**.  
  
4.  Wybierz **wybierz** przycisku.  
  
> [!NOTE]
>  **Połączenia zdalnego debugera** okno dialogowe może być również wyświetlany zdalnego debugowania elementów docelowych, które są podłączone bezpośrednio do komputera rozwoju lub są w tej samej podsieci. Można użyć jednej z tych celów debugowania zdalnego jako maszyny odtwarzania diagnostyki grafiki bez ręcznego konfigurowania go. W **połączenia zdalnego debugera** oknie dialogowym Wybierz element docelowy ma, a następnie wybierz pozycję **wybierz** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokument dziennika grafiki](graphics-log-document.md)