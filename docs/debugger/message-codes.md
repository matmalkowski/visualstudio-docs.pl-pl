---
title: "Kody komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 432012d897ecc4da508dd2925ac655b8dc9d1416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="message-codes"></a>Kody komunikatów
Każdy wiersz komunikat wyświetlany w [widoku komunikatów](../debugger/messages-view.md) zawiera "P", obiektu, "firmy," lub "R" kod. Te kody mają następujące znaczenie:  
  
|Kod|Znaczenie|  
|----------|-------------|  
|P|Komunikat była umieszczona w kolejce z **funkcji PostMessage** funkcji. Nie są dostępne informacje dotyczące ultimate dyspozycji wiadomości.|  
|S|Wiadomość została wysłana z **SendMessage** funkcji. Oznacza to, nadawca nie odzyskać kontrolę dopóki odbiornika przetwarza i zwraca komunikat. Odbiornik w związku z tym można przekazać wartości zwracanej do nadawcy.|  
|s|Komunikat został wysłany, ale zabezpieczeń uniemożliwia dostęp do wartości zwracanej.|  
|R|W każdym "w wierszu znajduje się odpowiedni wiersz"R"(zwrot) zawierającego wartości zwracanej wiadomości. Czasami wywołania wiadomości są zagnieżdżone, co oznacza, że ten program obsługi komunikatów jeden wysyła kolejną wiadomość.|