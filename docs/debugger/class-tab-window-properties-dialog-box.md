---
title: Karta klasa, okno dialogowe właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 573eb3f9cbcaedddc67524e81b2508df2112de04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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