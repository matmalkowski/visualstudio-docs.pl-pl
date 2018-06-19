---
title: Karta plik stronicowania, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 624be76badf8d57b060198c2ee910ead17b5efcb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472971"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Plik stronicowania, okno dialogowe właściwości procesu
Użyj **pliku stronicowania** kartę, aby przejrzeć plik stronicowania procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz pozycję **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **pliku stronicowania** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Bajty pliku stronicowania**|Bieżąca liczba stron, które tego procesu są używane w pliku stronicowania. Plik stronicowania przechowuje stron danych używanych przez proces, ale nie są zawarte w innych plikach. Plik stronicowania jest używany przez wszystkie procesy i brak miejsca w pliku stronicowania może powodować błędy, gdy są uruchomione inne procesy.|  
|**Szczytowe Bajty pliku stronicowania**|Maksymalna liczba stron, używane przez ten proces w pliku stronicowania.|  
|**Błędy strony**|Liczba błędów stron w wątkach wykonywanych w tym procesie. Błąd strony występuje, gdy wątek odwołuje się do strony pamięci wirtualnej, która nie znajduje się w jego zestawie roboczym w pamięci głównej. W związku z tym strony nie zostanie pobrany z dysku, jeśli znajduje się na liście gotowości i dlatego już w pamięci głównej, lub jeśli jest on używany przez inny proces z jest udostępniany strony.|