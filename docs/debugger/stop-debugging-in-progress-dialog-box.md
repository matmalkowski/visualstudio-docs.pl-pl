---
title: "Zatrzymaj debugowanie w oknie dialogowym postępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords: Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c056882d1a5c7eca4a7e09d040753d139c89b5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Zatrzymanie trwającego debugowania — Okno dialogowe
To okno dialogowe jest wyświetlany, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywania sesji jest, aby zająć trochę czasu. Zatrzymanie sesji debugowania jest zazwyczaj bardzo szybko i nie ma tego okna dialogowego. Czasami jednak potrzebny dodatkowy czas można odłączyć od wszystkich procesów debugowany. Zatrzymanie sesji zajmuje więcej niż kilka sekund (lub jeśli wystąpi awaria detach), zostanie wyświetlone okno dialogowe. W takim przypadku często, może to być spowodowane wystąpił problem wewnętrzny i można się z pomocą techniczną.  
  
 Poczekaj, aż procesy, aby odłączyć i to okno dialogowe do zniknąć lub użyj **Zatrzymaj** przycisk, aby wymusić natychmiastowe przerwanie działania.  
  
 **Zatrzymaj teraz**  
 Kliknij ten przycisk, aby zakończyć sesję debugowania natychmiast. Przy użyciu **Zatrzymaj** spowoduje przerwanie zamiast Odłączanie procesów debugowany. Jeśli są debugowanie procesów systemowych, zakończenie tych procesów z **Zatrzymaj** może mieć nieoczekiwane i niepożądane skutki.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Odłączanie programów](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)