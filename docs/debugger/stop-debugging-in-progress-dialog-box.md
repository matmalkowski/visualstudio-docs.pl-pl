---
title: Zatrzymaj debugowanie w oknie dialogowym postępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35e97e6a7f2b9eddb5694956633bc5bd79d8e426
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Zatrzymanie trwającego debugowania — Okno dialogowe
To okno dialogowe jest wyświetlany, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywania sesji jest, aby zająć trochę czasu. Zatrzymanie sesji debugowania jest zazwyczaj bardzo szybko i nie ma tego okna dialogowego. Czasami jednak potrzebny dodatkowy czas można odłączyć od wszystkich procesów debugowany. Zatrzymanie sesji zajmuje więcej niż kilka sekund (lub jeśli wystąpi awaria detach), zostanie wyświetlone okno dialogowe. W takim przypadku często, może to być spowodowane wystąpił problem wewnętrzny i można się z pomocą techniczną.  
  
 Poczekaj, aż procesy, aby odłączyć i to okno dialogowe do zniknąć lub użyj **Zatrzymaj** przycisk, aby wymusić natychmiastowe przerwanie działania.  
  
 **Zatrzymaj teraz**  
 Kliknij ten przycisk, aby zakończyć sesję debugowania natychmiast. Przy użyciu **Zatrzymaj** spowoduje przerwanie zamiast Odłączanie procesów debugowany. Jeśli są debugowanie procesów systemowych, zakończenie tych procesów z **Zatrzymaj** może mieć nieoczekiwane i niepożądane skutki.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Odłączanie programów](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)