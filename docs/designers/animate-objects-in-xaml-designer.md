---
title: "Animowanie obiektów w Projektancie XAML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4fd45337ebd0f00362d352077cf8441e6f5afa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML
Można utworzyć krótkiej animacji, które przenoszenie obiektów lub stopniowe je i wylogowanie.  
  
 Aby rozpocząć, Utwórz *scenorysu*. Scenorysu zawiera jeden lub więcej *osi czasu*. Ustaw *klatki* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji Blend interpolacji zmiany właściwości w wyznaczonym okresie czasu. Wynik jest przejścia. Można animować dowolnej właściwości, która należy do obiektu, nawet właściwości niewidoczne.  
  
 Na poniższej ilustracji przedstawiono scenorysu o nazwie **MoveUp**. Oś czasu zawiera klatek, który oznacza pozycję X i Y prostokąta. Po uruchomieniu tego animacji prostokąt są przenoszone z jednego miejsca na inny sprawnie.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Dowiedz się, można utworzyć animacje obserwując te pliki wideo.  
  
|Obejrzyj krótki klip wideo:|Dowiedz się, jak:|  
|--------------------------|-------------------|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [tworzenia osi czasu](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Tworzenie osi czasu i pracy z obiektami na osi czasu.|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj kluczowych i animacji](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Dodaj kluczowych i ustaw właściwości w każdej klatki kluczowej. Następnie obiekt animacji i obejrzyj bezproblemowe działanie przejścia między nimi.|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [dodać wyzwalaczy zdarzeń interakcji](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Uruchom animacji, gdy wystąpi zdarzenie. Na przykład uruchomić jeden po załadowaniu okna.|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [animować kolorów](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Umożliwia zmianę koloru obiektu animacji.|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [tworzenie i modyfikowanie ścieżek ruchu](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animowanie obiektów wzdłuż ścieżki.|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [jej obsługi ułatwiają klatek](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Przyspieszenie działania lub spowolnić animacji na początku (*sterowania tempem zmian w*) lub w jego pobliżu zakończenia (*dynamiki poza*) animacji.|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [animować przycisk](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Utwórz interesujące efekty, które pojawiają się na przycisku, gdy użytkownik wskazuje on.|  
|![Konfigurowanie funkcji zainstalowane](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie animacji i Praca z napięcia](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animacja efekty, które są wyświetlane po naciśnięciu przycisku w obrazie Kalkulator.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)