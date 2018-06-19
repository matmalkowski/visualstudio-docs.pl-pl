---
title: Kody komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b2061d9f20da8e9c4d5b4f9794f400d638260c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474446"
---
# <a name="message-codes"></a>Kody komunikatów
Każdy wiersz komunikat wyświetlany w [widoku komunikatów](../debugger/messages-view.md) zawiera "P", obiektu, "firmy," lub "R" kod. Te kody mają następujące znaczenie:  
  
|Kod|Znaczenie|  
|----------|-------------|  
|P|Komunikat była umieszczona w kolejce z **funkcji PostMessage** funkcji. Nie są dostępne informacje dotyczące ultimate dyspozycji wiadomości.|  
|S|Wiadomość została wysłana z **SendMessage** funkcji. Oznacza to, nadawca nie odzyskać kontrolę dopóki odbiornika przetwarza i zwraca komunikat. Odbiornik w związku z tym można przekazać wartości zwracanej do nadawcy.|  
|s|Komunikat został wysłany, ale zabezpieczeń uniemożliwia dostęp do wartości zwracanej.|  
|R|W każdym "w wierszu znajduje się odpowiedni wiersz"R"(zwrot) zawierającego wartości zwracanej wiadomości. Czasami wywołania wiadomości są zagnieżdżone, co oznacza, że ten program obsługi komunikatów jeden wysyła kolejną wiadomość.|