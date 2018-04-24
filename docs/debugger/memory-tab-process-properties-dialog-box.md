---
title: Karta pamięć, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b43dd047e4ebdb145092dc3b9f37098b8db6322e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="memory-tab-process-properties-dialog-box"></a>Karta Pamięć, okno dialogowe właściwości procesu
Użyj **pamięci** kartę, aby pokazać, jak proces korzysta z pamięci. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz pozycję **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **pamięci** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Licznik Bajty wirtualne**|Bieżący rozmiar (w bajtach) wirtualnej przestrzeni adresowej używanej przez proces. Użycie wirtualnej przestrzeni adresowej nie musi oznaczać odpowiedniego użycia dysku lub stron pamięci głównej. Jednak pamięć wirtualna jest jednak ograniczona i przy użyciu zbyt dużo może ograniczyć możliwość ładowania bibliotek przez proces.|  
|**Szczytowe Bajty wirtualne**|Maksymalna liczba bajtów w wirtualnej przestrzeni adresowej procesu został użyty w dowolnym momencie.|  
|**Zestaw roboczy**|Zestaw stron pamięci niedawno korzystały wątki w procesie. Jeśli ilość wolnej pamięci w komputerze jest większa niż wartość progowa, strony są pozostawiane w zestawie roboczym procesu, nawet jeśli nie są używane. Jeśli ilość wolnej pamięci spada poniżej wartości progowej, strony są usuwane z zestawu roboczego. Jeśli są one potrzebne, zostaną one ponownie umieszczone w zestawie roboczym przed opuszczeniem pamięci głównej.|  
|**Szczytowy zestaw roboczy**|Maksymalna liczba stron w zestawu roboczego tego procesu w dowolnym momencie.|  
|**Bajty w puli stronicowanej**|Bieżąca ilość przydzielonej przez proces puli stronicowanej. Puli stronicowanej jest obszar pamięci systemu, gdzie składników systemu operacyjnego uzyskać miejsca one wykonywać ich wyznaczonego zadania. Strony puli stronicowanej może być stronicowana się do pliku stronicowania w dostępie nie przez system dla trwałego okresów.|  
|**Bajty w puli niestronicowanej**|Bieżąca liczba bajtów w puli niestronicowanej alokowaną przez profilowany proces. Puli niestronicowanej jest obszar pamięci systemu, gdzie miejsca są uzyskiwane przez składniki systemu operacyjnego, zgodnie z ich realizacji ich wyznaczonego zadań. Strony puli niestronicowanej nie stronicowany pliku stronicowania; pozostają one w pamięci głównej tak długo, jak są przydzielone.|  
|**Bajty prywatne**|Bieżąca liczba bajtów, jaką przydzielonej ten proces, które nie może być współużytkowana z innymi procesami.|  
|**Wolnych bajtów**|Całkowita liczba nieużywanych wirtualnej przestrzeni adresowej tego procesu.|  
|**Bajty zarezerwowane**|Całkowita ilość pamięci wirtualnej zarezerwowana do użytku w przyszłości przez ten proces.|  
|**Obrazu wolnych bajtów**|Ilość wirtualnej przestrzeni adresowej nie jest w użyciu lub zarezerwowany przez obrazów w ramach tego procesu.|  
|**Bajty zarezerwowane obrazu**|Suma wszystkich pamięci wirtualnej zarezerwowanej przez obrazy uruchomione w ramach tego procesu.|