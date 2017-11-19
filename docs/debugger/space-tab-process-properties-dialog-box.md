---
title: "Karta przestrzeń, okno dialogowe właściwości procesu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70f9805f0868c7afec70fdda26ff97766281d9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="space-tab-process-properties-dialog-box"></a>Karta Przestrzeń, okno dialogowe właściwości procesu
Użyj **miejsca** kartę, aby zbadać przestrzeni adresowej procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz pozycję **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **miejsca** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Pokaż dla przestrzeni oznaczonej jako**|Użyj tego pola listy, aby wybrać kategorię miejsca (obraz, mapowane, zarezerwowane lub nieprzypisane).|  
|**Bajty pliku wykonywalnego**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej używanej przez ten proces. Pamięć pliku wykonywalnego jest pamięć, która może być wykonywane przez programy, ale może nie być zapisu lub odczytu.|  
|**Exec — tylko do odczytu w bajtach**|Dla wybranej kategorii suma wszystkich przestrzeni adresowej używanej w użyciu, właściwości tylko do odczytu, które są używane przez ten proces. Exec — tylko do odczytu pamięci jest pamięć, która może być wykonane, a także do odczytu.|  
|**Exec — odczytu i zapisu w bajtach**|Dla wybranej kategorii suma wszystkich przestrzeni adresowej używanej w użyciu, właściwości odczytu i zapisu, które są używane przez ten proces. Exec — odczytu i zapisu pamięci jest pamięć, która jest wykonywana przez programy, a także do odczytu i modyfikować.|  
|**Bajty kopię zapisu exec**|Dla wybranej kategorii sumę wszystkich przestrzeń adresów, które można wykonać przez programy, a także odczyt i zapis. Ten typ ochrony jest używany, gdy pamięć musi być udostępniana między procesami. Jeśli procesy udostępniania tylko do odczytu pamięci, następnie wszystkie używają tej samej pamięci. Jeśli proces współużytkujący żąda dostępu do zapisu, kopię tej pamięci będzie nawiązywane przez proces.|  
|**Brak dostępu bajtów**|Dla wybranej kategorii sumę wszystkich przestrzeni adresowej procesu uniemożliwia korzystania z niego. Naruszenia zasad dostępu jest generowany, gdy zapisu lub odczytu zostanie podjęta.|  
|**Tylko do odczytu w bajtach**|Dla wybranej kategorii sumę całą przestrzeń adresową, który może być wykonane, a także do odczytu.|  
|**Bajty odczytu / zapisu**|Dla wybranej kategorii sumę całą przestrzeń adresową, który umożliwia odczytywanie i zapisywanie.|  
|**Bajty kopię zapisu**|Dla wybranej kategorii sumę wszystkich przestrzeń adresów, która umożliwia udostępnianie pamięci do odczytu, ale nie do zapisu. Gdy procesy odczytują tę pamięć, mogą współużytkować tego samego pamięci. Jednak proces chce mieć dostęp do odczytu/zapisu do tej pamięci współużytkowanej, kopię tej pamięci się do zapisu.|