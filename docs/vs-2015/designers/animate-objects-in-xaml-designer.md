---
title: Animowanie obiektów w Projektancie XAML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 481ba0f156f6ea6cc43d9df19eedcb84ab864cbe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630834"
---
# <a name="animate-objects-in-xaml-designer"></a>Animowanie obiektów w projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Animowanie obiektów w Projektancie XAML](https://docs.microsoft.com/visualstudio/designers/animate-objects-in-xaml-designer).  
  
Tworzenie animacji w krótkim przenoszenie obiektów lub zanikanie je wewnątrz i na zewnątrz.  
  
 Aby rozpocząć, Utwórz *scenorysu*. Scenorysu zawiera jeden lub więcej *osi czasu*. Ustaw *klatki kluczowe* na osi czasu, aby oznaczyć zmiany właściwości. Następnie po uruchomieniu animacji, program Blend argumentu zmiany właściwości w wyznaczonym okresie. Wynikiem jest płynne przejście. Można animować dowolnej właściwości, która należy do obiektu, nawet właściwości niewizualnej.  
  
 Na poniższej ilustracji przedstawiono scenorysu o nazwie **MoveUp**. Oś czasu zawiera ramkami kluczowymi, który oznacza X i Y pozycja prostokąta. Po uruchomieniu ta animacja prostokąta bezproblemową z jednego miejsca do drugiego.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Dowiedz się, tworzenie animacji, obejrzyj te klipy wideo.  
  
|Obejrzyj krótki film wideo:|Dowiedz się, jak:|  
|--------------------------|-------------------|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [tworzenia osi czasu](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Tworzenie osi czasu i pracy z obiektami na osi czasu.|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj klatki kluczowe i powtórz animację](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Dodaj ramkami kluczowymi, a następnie ustaw właściwości w każdej klatce kluczowej. Następnie uruchom obiektów animacji i obejrzyj płynne przejście między nimi.|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [dodać wyzwalacze zdarzeń interakcji](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Rozpocznij animację, gdy wystąpi zdarzenie. Na przykład uruchomić jeden po załadowaniu okna.|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [animowanie kolorów](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Aby zmienić kolor obiektu, należy użyć animacji.|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [tworzenie i modyfikowanie ścieżki ruchu](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animowanie obiektów w ścieżce.|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [jej obsługi ułatwiają realizację klatek kluczowych](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Przyspieszyć lub zwolnić animację na początku (*sterowania tempem zmian w*) lub w pobliżu końca (*przyspieszania poza*) animacji.|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [animować przycisk](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Utwórz interesujące efekty, które są wyświetlane na przycisku, gdy użytkownik wskaże do niego.|  
|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie animacji i Praca z ułatwianie](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animowanie efektów, które pojawiają się po naciśnięciu przycisku na obrazie Kalkulator.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)



