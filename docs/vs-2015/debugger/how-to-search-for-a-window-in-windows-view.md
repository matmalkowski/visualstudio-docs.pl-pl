---
title: 'Porady: wyszukiwanie okna w widoku Windows | Dokumentacja firmy Microsoft'
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
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 043e3e92004eb5b0995bc285e90a138f4dc902f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680692"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Porady: wyszukiwanie okna w widoku okien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: wyszukiwanie okna w widoku Windows](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-window-in-windows-view).  
  
Możesz wyszukać określonego okna w widoku Windows za pomocą jego uchwytu, podpis, klasy lub kombinację jego podpisu i klasy jako kryterium wyszukiwania. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym pokaże atrybutów okna wybranego w drzewie okna.  
  
 Rozpoczyna się od drzewa, rozwinięty do drugiego poziomu (wszystkie okna, które są elementami podrzędnymi pulpit), dzięki czemu można zidentyfikować windows desktop poziomu według ich nazwy klasy i tytuł. Po wybraniu okna pulpitu poziomu można rozwinąć tego poziomu można znaleźć okna podrzędnego określonego.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Wyszukiwanie okna w widoku Windows  
  
1.  Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ [widoku Windows](../debugger/windows-view.md) okna i docelowy są widoczne.  
  
2.  Z **wyszukiwania** menu, wybierz **Znajdź okno**.  
  
     [Okno dialogowe Wyszukiwanie](../debugger/window-search-dialog-box.md) zostanie otwarty.  
  
    > [!TIP]
    >  Aby zwiększyć czytelność ekranu, wybierz pozycję **Ukryj Spy** opcji. Ta opcja zawiera głównego okna programu Spy ++ i pozostawia tylko **wyszukiwanie okien** okno dialogowe widoczne na podstawie innych aplikacji. Okno główne programu Spy ++ jest przywracany po kliknięciu **OK** lub **anulować**, lub po usunięciu zaznaczenia **Ukryj Spy ++** opcji.  
  
3.  Przeciągnij **Wyszukiwarka** przedziale docelowego. Przeciągnij narzędzie **wyszukiwanie okien** okno dialogowe wyświetla szczegóły wybranego okna.  
  
     — lub —  
  
     Jeśli znasz uchwyt okna ma (na przykład z debugerem), można wpisać go **obsługi** pole.  
  
     — lub —  
  
     Znając podpisu i/lub klasy okna, które chcesz, możesz wpisać je w **podpis** i **klasy** pola tekstowe i wyczyść **obsługi** pola tekstowego.  
  
4.  Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.  
  
5.  Kliknij przycisk **OK**.  
  
     Jeśli zgodne okno zostanie znaleziony, jest wyróżniona na [widoku Windows](../debugger/windows-view.md) okna.



