---
title: 'Porady: wyszukiwanie komunikatu w widoku komunikatów | Dokumentacja firmy Microsoft'
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
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 984c3f0dc9b61059b53a7caf5a859d3413c99e62
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677230"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Porady: wyszukiwanie komunikatu w widoku komunikatów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: wyszukiwanie komunikatu w widoku komunikatów](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-message-in-messages-view).  
  
Możesz wyszukać szczegółowy komunikat o błędzie w widoku komunikatów za pomocą jego uchwytu, typ lub identyfikator komunikatu jako kryterium wyszukiwania. Jeden z nich — lub kombinacji — będą prawidłowe kryteria. Można również określić początkową kierunek wyszukiwania. Pola w oknie dialogowym są wstępnie ładowane z atrybutami komunikatów aktualnie wybrany.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Aby wyszukać komunikatu w widoku komunikatów  
  
1.  Rozmieść aplikacji dla systemu windows, więc tego programu Spy ++ i aktywne [widoku komunikatów](../debugger/messages-view.md) okna są widoczne.  
  
2.  Z **wyszukiwania** menu, wybierz **Znajdź komunikat**.  
  
     [Wyszukiwanie komunikatów — okno dialogowe](../debugger/message-search-dialog-box.md) zostanie otwarty.  
  
3.  Przeciągnij **Wyszukiwarka** przedziale żądaną. Przeciągnij narzędzie **Wyszukiwarka komunikatów** okno dialogowe wyświetla szczegóły wybranego okna.  
  
     — lub —  
  
     Jeśli uchwyt okna komunikatów, którego chcesz zbadać, wpisz go w **obsługi** pola tekstowego.  
  
     — lub —  
  
     Jeśli znasz typ komunikatu i/lub identyfikator wiadomości, które chcesz, aby wybrać je z **typu** i **komunikat** menu rozwijanych i wyczyść **obsługi** pola tekstowego.  
  
4.  Wyczyść wszystkie pola, dla których nie chcesz określać wartości.  
  
    > [!TIP]
    >  Aby zwiększyć czytelność ekranu, wybierz pozycję **Ukryj Spy** opcji. Ta opcja zawiera narzędzie Spy ++ oknie głównym, pozostawiając tylko **Znajdź okno** okno dialogowe widoczne na podstawie innych aplikacji. Okno główne programu Spy ++ jest przywracany po kliknięciu **OK** lub **anulować**, lub po usunięciu zaznaczenia **Ukryj Spy ++** opcji.  
  
5.  Wybierz **się** lub **dół** dla początkowej kierunek wyszukiwania.  
  
6.  Kliknij przycisk **OK**.  
  
 Jeśli zostanie znaleziona pasująca wiadomość, jest wyróżniona w oknie Widok komunikatów. Zobacz [widoku komunikatów](../debugger/messages-view.md).



