---
title: "Karta klasa, okno dialogowe właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb10cf8a571d37f27244398e6c957c46cee87f8b
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="class-tab-window-properties-dialog-box"></a>Karta Klasa, okno dialogowe właściwości okna
Użyj **klasy** kartę, aby wyświetlić informacje dotyczące klasy wybranego okna. Aby wyświetlić [okno dialogowe właściwości](../debugger/window-properties-dialog-box.md), Przenieś fokus do [widoku systemu Windows](../debugger/windows-view.md) okna. Zaznacz dowolny węzeł okna w drzewie, a następnie wybierz pozycję **właściwości** z **widoku** menu.  
  
 Następujące ustawienia są dostępne na **klasy** karty:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Nazwa klasy**|Nazwa lub numer porządkowy tej klasy okna.|  
|**Style — klasa**|Kombinacja kodów stylu klasy.|  
|**Klasa b**|Dane aplikacji skojarzonych z tą klasą okna.|  
|**Klasa Atom**|Atom dla klasy zwrócony przez **RegisterClass** wywołania.|  
|**Dojście wystąpienia**|Dojście wystąpienia modułu, w którym zarejestrowano klasę. Uchwyty wystąpienia nie są unikatowe.|  
|**Okno bajtów**|Liczba bajtów dodatkowych skojarzonych z każdym okna tej klasy. Znaczenie tych bajtów jest określany przez aplikację. Rozwiń pole listy wartości bajtów w formacie DWORD.|  
|**Proces okna**|Bieżący adres **WndProc** funkcji dla systemu windows w tej klasy. To różni się od **proces okna** na **ogólne** Jeśli okno jest podklasą klasy.|  
|**Nazwy menu**|Nazwa menu głównego, który jest skojarzony z tej klasy ("Brak" w przypadku menu nie) z systemem windows.|  
|**Dojście ikony**|Dojście do ikonę, która jest skojarzona z tej klasy ("Brak" w przypadku bez ikony) z systemem windows.|  
|**Dojście do kursora**|Dojście do kursora, który jest skojarzony z tej klasy ("Brak" Jeśli żaden kursor) z systemem windows.|  
|**Tło / pędzla**|Dojście do pędzel tła jest skojarzony z tej klasy lub jeden z wstępnie zdefiniowanych kolorów COLOR_ * dla malowania tło okna ("Brak", jeśli nie istnieje żadne pędzla) z systemem windows.|