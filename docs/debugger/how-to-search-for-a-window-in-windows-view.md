---
title: 'Porady: wyszukiwanie okna w widoku systemu Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5762a9345f0246b8ee957c59da5d78ffb7a17749
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Porady: wyszukiwanie okna w widoku okien
Można wyszukiwać określone okno w widoku systemu Windows za pomocą jego uchwytu, podpis, klasy lub kombinację jego podpis i klasy jako kryterium wyszukiwania. Można również określić początkowego kierunku wyszukiwania. Pola w oknie dialogowym zostaną wyświetlone atrybutów okna wybranego w drzewie okna.  
  
 Rozpoczynanie drzewa rozwijany do drugiego poziomu (wszystkie okna, które są elementami podrzędnymi pulpitu), dzięki czemu można zidentyfikować windows desktop poziom według nazwy klasy i tytuł. Po wybraniu opcji okna poziomu pulpitu, można rozszerzyć tego poziomu można znaleźć oknem podrzędnym określonego.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Aby wyszukać okna w widoku okien  
  
1.  Rozmieścić okna, tak że Spy ++ [widoku systemu Windows](../debugger/windows-view.md) okna i docelowy są widoczne.  
  
2.  Z **wyszukiwania** menu, wybierz **Znajdź okno**.  
  
     [Wyszukiwania okna, okno dialogowe](../debugger/window-search-dialog-box.md) otwiera.  
  
    > [!TIP]
    >  Aby zwiększyć czytelność ekranu, wybierz **Ukryj Spy** opcji. Ta opcja zawiera Spy ++ okno główne i pozostawienie tylko **wyszukiwanie okien** okno dialogowe widoczne na innych aplikacji. Okno główne programu Spy ++ zostanie przywrócona po kliknięciu **OK** lub **anulować**, lub po usunięciu zaznaczenia **Ukryj Spy ++** opcji.  
  
3.  Przeciągnij **narzędzia wyszukiwania** za pośrednictwem docelowego okna. Przeciągnij narzędzie, **wyszukiwanie okien** okno dialogowe wyświetla szczegóły w oknie wybrane.  
  
     - lub -  
  
     Jeśli znasz uchwyt okna ma (na przykład z debugera), można wpisać w **obsługi** pole.  
  
     - lub -  
  
     Jeśli znasz podpisu i/lub klasy okno ma można wpisać je w **podpis** i **klasy** pola tekstowe i wyczyść zaznaczenie **obsługi** pola tekstowego.  
  
4.  Wybierz **się** lub **dół** dla początkowego kierunku wyszukiwania.  
  
5.  Kliknij przycisk **OK**.  
  
     Jeśli zostanie znaleziony zgodne okno, zostanie wyróżniona w [widoku systemu Windows](../debugger/windows-view.md) okna.