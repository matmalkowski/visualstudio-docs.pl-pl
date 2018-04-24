---
title: Karta Ogólne przetworzyć okno dialogowe właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3dcefc8be643c74349102261725c4879c0e161cd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="general-tab-process-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości procesu
Użyj **ogólne** kartę, aby dowiedzieć się więcej na temat określonego procesu. Aby wyświetlić [okno dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md), Przenieś fokus do [widok procesy](../debugger/processes-view.md) okna. Zaznacz dowolny węzeł procesu w drzewie, a następnie wybierz pozycję **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **ogólne** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Nazwa modułu**|Nazwa modułu.|  
|**Identyfikator procesu**|Unikatowy identyfikator tego procesu. Numery identyfikatorów procesów są używane ponownie, więc identyfikują one procesy jedynie dla okresu istnienia tego procesu. Typ obiektu procesu jest tworzony w momencie uruchomienia programu. Wszystkie wątki w procesie Udostępnij tę samą przestrzeń adresową i mają dostęp do tych samych danych.|  
|**Priorytet podstawowy**|Bieżący priorytet podstawowy tego procesu. Wątków w procesie można wywołać i zmniejszyć ich priorytet podstawowy względem priorytet podstawowy.|  
|**Wątki**|Liczba aktywnych wątków w tym procesie.|  
|**Czas procesora CPU**|Łączny czas procesora CPU podczas tego procesu i wątków. Taki sam jak czas użytkownika oraz czasu uprzywilejowanego.|  
|**Czas użytkownika**|Skumulowany czas, który upłynął czy wątki tego procesu ma poświęcony na wykonywanie kodu w trybie użytkownika w Aktywne wątki. Aplikacje wykonać w trybie użytkownika, jak podsystemów, takie jak Menedżera okien i aparat grafiki.|  
|**Czas uprzywilejowany**|Całkowity czas ten proces jest uruchomiony w trybie uprzywilejowanym w Aktywne wątki. Warstwy usługi, procedury wykonawczego i jądra należy wykonać w trybie uprzywilejowanym. Sterowniki urządzeń dla większości urządzeń innych niż kart graficznych i drukarki również wykonać w trybie uprzywilejowanym. Niektóre pracy, który wykonuje systemu Windows dla aplikacji mogą pojawić się w innych procesów podsystemu oprócz czasu uprzywilejowanego.|  
|**Czas, który upłynął**|Całkowity czas przez ten proces jest uruchomiony.|