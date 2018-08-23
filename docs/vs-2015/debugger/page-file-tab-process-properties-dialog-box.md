---
title: Karta plik stronicowania, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa1eba7af60638d82c791958af6bf66a3272242
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42692333"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Plik stronicowania, okno dialogowe właściwości procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [karta plik stronicowania, okno dialogowe właściwości procesu](https://docs.microsoft.com/visualstudio/debugger/page-file-tab-process-properties-dialog-box).  
  
Użyj **pliku stronicowania** kartę, aby przejrzeć plik stronicowania procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **pliku stronicowania** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Bajty pliku stronicowania**|Bieżąca liczba stron, które tego procesu są używane w pliku stronicowania. Plik stronicowania przechowuje stron danych używane w procesie, ale nie jest zawarta w innych plikach. Plik stronicowania jest używany przez wszystkie procesy i braku miejsca w pliku stronicowania może powodować błędy, gdy są uruchomione inne procesy.|  
|**Szczytowe Bajty pliku stronicowania**|Maksymalna liczba stron, które ten proces został użyty w pliku stronicowania.|  
|**Błędy stron**|Liczba błędów strony w wątkach wykonywanych w ramach tego procesu. Błąd strony występuje, gdy wątek odwołuje się do strony pamięci wirtualnej, która nie znajduje się w jego zestawie roboczym w pamięci głównej. W związku z tym, strona nie zostanie pobrany z dysku jeśli znajduje się na liście gotowości i dlatego już w pamięci głównej, lub jeśli jest on używany przez inny procesu zostały udostępnione strony.|



