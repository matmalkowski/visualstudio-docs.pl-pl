---
title: Zatrzymywanie debugowania w okno dialogowe postępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 3a6e13967cc18fae8d837cc71ea8a91c60f2b1bb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281198"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Zatrzymanie trwającego debugowania — Okno dialogowe
To okno dialogowe pojawia się, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywania sesji jest zamierza zająć trochę czasu. Zatrzymywanie sesji debugowania jest zazwyczaj bardzo szybkie i nie ma tego okna dialogowego. Czasami jednak zajmuje dodatkowy czas, aby odłączyć od wszystkich procesów, które są debugowane. Jeśli zatrzymywania sesji przyjmuje więcej niż kilku sekund (lub jeśli wystąpi błąd odłączania), pojawi się okno dialogowe. W takim przypadku często, może to być spowodowane problem wewnętrzny i chcesz się z pomocą techniczną.  
  
 Poczekaj, aż procesy, które można odłączyć i to okno dialogowe zniknięcie lub użyj **Zatrzymaj** przycisk, aby wymusić natychmiastowe przerwanie działania.  
  
 **Zatrzymaj teraz**  
 Kliknij ten przycisk, aby zakończyć sesję debugowania natychmiast. Za pomocą **Zatrzymaj** spowoduje przerwanie działania, a nie Odłączanie procesów debugowania. Jeśli debugujesz procesy systemowe zakończenie tych procesów za pomocą **Zatrzymaj** może mieć niepożądane i nieoczekiwane skutki.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Trwa odłączanie programy](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))