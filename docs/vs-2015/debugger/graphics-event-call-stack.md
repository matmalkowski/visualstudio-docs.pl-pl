---
title: Stos wywołań zdarzeń grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d866e63ecffbed5cd5e9a9e477f99fbd8e8c3fc9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682894"
---
# <a name="graphics-event-call-stack"></a>Stos wywołań zdarzeń grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [stos wywołań zdarzenia grafiki](https://docs.microsoft.com/visualstudio/debugger/graphics/graphics-event-call-stack).  
  
Stos wywołań zdarzenia grafiki w analizatora grafiki programu Visual Studio ułatwia mapowanie relacji między zdarzenia grafiki problematyczne i kod źródłowy aplikacji.  
  
 Jest to okno stosu wywołań zdarzeń:  
  
 ![Poprzedzający stos wywołań zdarzeń DrawIndexed. ](../debugger/media/gfx-diag-demo-graphics-event-call-stack-orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Opis stos wywołań zdarzeń grafiki  
 Stos wywołań zdarzenia można użyć, aby zrozumieć przepływ wykonania, która doprowadziła do konkretnego zdarzenia Direct3D. Jest on podobny okna stosu wywołań programu Visual Studio, z tą różnicą, że zamiast bieżącego stosu wywołań z aktywnym wątkiem w uruchomionej aplikacji, wyświetla stos wywołań istniał wybrane zdarzenia Direct3D. Z stos wywołań zdarzenia można przejść do witryny wywołania wybranego zdarzenia Direct3D, aby sprawdzić otaczającym kodem.  
  
 Za pomocą stos wywołań zdarzenia, aby zidentyfikować ścieżki kodu, z której pochodzi zdarzenie problemu, swojej wiedzy na temat kodu można użyć, aby wywnioskował potencjalnych źródeł problemu, lub dodać punkty przerwania w kodzie źródłowym aplikacji tak, aby można było używać tradycyjny debugowanie techniki, aby sprawdzić, jak stan aplikacji lub zdarzeń parametrów powodują zdarzenia w celu błędne działanie. W ten sposób może pomóc w znalezieniu problemów w kodzie źródłowym, który tylko dyskowe widoczne jako problemów z renderowaniem.  
  
### <a name="graphics-event-call-stack-information"></a>Informacje stosu wywołań zdarzeń grafiki  
 Stos wywołań zdarzeń nie obsługuje wstępne ramki lub zdarzenia zdefiniowane przez użytkownika. Stos wywołań zdarzeń grafiki jest wyświetlana w formacie tabeli.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Symbol, który unikatowo identyfikuje funkcji, która zawiera wywołania. Symbol debugowania dla tej funkcji jest wyświetlane, gdy jest ona dostępna; w przeciwnym razie zostanie wyświetlony przesunięcie funkcji.|  
|**Plik**|Nazwa pliku, plik kodu źródłowego lub plik biblioteki, który zawiera wywołania.|  
|**Lokalizacja**|Numer wiersza wywołania.|  
  
### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych  
 Aby zrozumieć zdarzenia wybranego grafiki, może być konieczne informacje o obiektach Direct3D, które są skojarzone z nim. **Stos wywołań zdarzenia grafiki** okno zawiera łącza do tych informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)



