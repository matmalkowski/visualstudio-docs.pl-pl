---
title: Karta komunikaty, okno dialogowe opcji komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f19da533d2ab13e7493eae53af8dea3af4e520df
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="messages-tab-message-options-dialog-box"></a>Karta Komunikaty, okno dialogowe opcji komunikatów
Użyj **wiadomości** kartę, aby wybrać, które wiadomości typów do listy w [widoku komunikatów](../debugger/messages-view.md)i określić kryteria wyszukiwania komunikatu. Aby wyświetlić [okno dialogowe opcji komunikatów](../debugger/message-options-dialog-box.md), wybierz **komunikaty dziennika** z **Spy** menu.  
  
 Zwykle, najpierw wybierz **grup komunikat**, a następnie dostosowywać zaznaczenie wybierając poszczególne **wiadomości do widoku**. **Wszystkie** przycisk wybiera wszystkich typów komunikatów i **Brak** przycisku spowoduje wyczyszczenie wszystkich typów.  
  
 Następujące ustawienia są dostępne na **wiadomości** karty:  
  
 **Wiadomości do widoku**  
 Wybierz określone komunikaty do wyświetlenia. Podczas tworzenia nowego okna komunikatów go wyświetlić wszystkie komunikaty. Podczas filtrowania wiadomości z **wiadomości** kartę, że filtr dotyczy tylko wiadomości nie wiadomości, które już zostały wyświetlone w widoku systemu Windows.  
  
 **Komunikat grup**  
 Wybierz grupy komunikat do wyświetlenia. Dostępne grupy obejmują:  
  
-   WM_USER: z kodem większa niż lub równa WM_USER  
  
-   Zarejestrowany: zarejestrowany **RegisterWindowMessage** wywołania  
  
-   Nieznany: nieznany wiadomości w zakresie od 0 do (WM_USER - 1)  
  
 Należy pamiętać, że te **grup komunikat** nie są mapowane na określonej pozycji w obszarze **wiadomości, aby wyświetlić**. Po wybraniu grupy zaznaczenie jest stosowany bezpośrednio do strumienia komunikatów.  
  
 Wygaszone pole wyboru w **grup komunikat** oznacza to, że **wiadomości, aby wyświetlić** pole listy został zmodyfikowany wiadomości w tej grupie; nie wszystkie typy wiadomości w tej grupie nie zaznaczono.  
  
 **Zapisz ustawienia jako ustawienia domyślne**  
 Zapisz bieżące ustawienia do późniejszego użytku jako opcje wyszukiwania wiadomości. Te ustawienia zostały także zapisane podczas zamykania programu Spy ++.