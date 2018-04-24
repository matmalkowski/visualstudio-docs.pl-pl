---
title: Widoku komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31baccc88b25979dfc92fed6217bec3b0ef16a55
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="messages-view"></a>Widok komunikatów
Każde okno ma strumienia skojarzonych komunikatów. Okno widoku komunikatów wyświetla ten strumień komunikatu. Uchwyt okna, kod wiadomości i wiadomości są wyświetlane. Można utworzyć widoku komunikatów dla wątku lub procesu również. Dzięki temu można wyświetlić komunikaty wysyłane do wszystkich okien należących do określonych proces lub wątek, który jest szczególnie przydatne w przypadku przechwytywania komunikaty inicjowania okna.  
  
 Typowe okno widoku komunikatów pojawia się poniżej. Należy pamiętać, że pierwsza kolumna zawiera uchwytu okna, a druga kolumna zawiera kod wiadomości (wyjaśniono w [kody komunikatów](../debugger/message-codes.md)). Komunikat dekodowane parametrów i zwracanych wartości są po prawej stronie.  
  
 ![Spy&#43; &#43; widoku komunikatów](../debugger/media/spy--_messagesview.png "Spy ++ _MessagesView")  
Widok komunikatów narzędzia Spy ++  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Aby otworzyć widok wiadomości dla okna, proces lub wątek  
  
1.  Przenieś fokus do [widoku systemu Windows](../debugger/windows-view.md), [widok procesy](../debugger/processes-view.md), lub [Widok wątków](../debugger/threads-view.md) okna.  
  
2.  Odnaleźć węzła dla elementu wiadomości, których chcesz zbadać i zaznacz go.  
  
3.  Z **Spy** menu, wybierz **komunikaty dziennika**.  
  
     [Okno dialogowe opcji komunikatów](../debugger/message-options-dialog-box.md) otwiera.  
  
4.  Wybierz opcje dla komunikatu, który chcesz wyświetlić.  
  
5.  Naciśnij klawisz **OK** aby rozpocząć rejestrowanie komunikatów.  
  
     Zostanie otwarte okno Widok wiadomości i a **wiadomości** menu zostanie dodany do Spy ++ — pasek narzędzi. W zależności od opcji wybranych wiadomości rozpoczęcia przesyłania strumieniowego do aktywnego okna wiadomości w widoku.  
  
6.  Jeśli masz za mało wiadomości, wybierz **Zatrzymaj rejestrowanie** z **wiadomości** menu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontrolowanie widoku komunikatów](../debugger/how-to-control-messages-view.md)  
 Wyjaśnia sposób zarządzania widoku komunikatów.  
  
 [Otwieranie widoku komunikatów w Znajdź okno](../debugger/how-to-open-messages-view-from-find-window.md)  
 Wyjaśniono, jak otwieranie widoku komunikatów w Znajdź okno dialogowe.  
  
 [Wyszukiwanie komunikatu w widoku komunikatów](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Wyjaśniono, jak można znaleźć określonego komunikatu w widoku komunikatów.  
  
 [Uruchamianie i zatrzymywanie wyświetlania dziennika komunikatów](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Wyjaśniono, jak uruchamianie i zatrzymywanie rejestrowania komunikatów.  
  
 [Kody komunikatów](../debugger/message-codes.md)  
 Definiuje kody komunikatów wymienionych w widoku komunikatów.  
  
 [Wyświetlanie właściwości komunikatów](../debugger/how-to-display-message-properties.md)  
 Jak wyświetlić więcej informacji na temat wiadomości.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Widoki w programie Spy++](../debugger/spy-increment-views.md)  
 W tym artykule wyjaśniono widoków Spy ++ drzewa systemu windows, wiadomości, procesów i wątków.  
  
 [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)  
 Wprowadzono narzędzie Spy ++ i opisano, jak mogą być używane.  
  
 [Okno dialogowe opcji komunikatów](../debugger/message-options-dialog-box.md)  
 Pozwala wybrać wiadomości, które są wyświetlane w widoku aktywnego wiadomości.  
  
 [Wyszukiwanie komunikatów — okno dialogowe](../debugger/message-search-dialog-box.md)  
 Umożliwia znalezienie węzła dla określonego komunikatu w widoku komunikatów.  
  
 [Okno dialogowe właściwości wiadomości](../debugger/message-properties-dialog-box.md)  
 Umożliwia wyświetlenie właściwości wybranego w widoku komunikatów wiadomości.  
  
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)  
 Zawiera sekcje zawierająca opis każdego Spy ++ menu i okno dialogowe.