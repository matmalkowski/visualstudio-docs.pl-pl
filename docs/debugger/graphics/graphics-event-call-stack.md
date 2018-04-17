---
title: Stos wywołań zdarzeń grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73dcda2cf0a6d3f565f8d7a282788b5861ebc218
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="graphics-event-call-stack"></a>Stos wywołań zdarzeń grafiki
Stos wywołań zdarzeń grafiki w analizatora grafiki programu Visual Studio ułatwia mapowania relacji między zdarzeń grafiki powodować problemy i kodu źródłowego aplikacji.  
  
 Jest to oknie stosu wywołań zdarzeń:  
  
 ![Poprzedzających stosu wywołań zdarzeń DrawIndexed. ] (media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Opis stos wywołań zdarzeń grafiki  
 Stos wywołań zdarzeń umożliwia zrozumienie przepływu wykonanie, które doprowadziły do konkretnego zdarzenia Direct3D. Podobny go z okna stosu wywołań Visual Studio, z tą różnicą, że zamiast wyświetlanie bieżącego stosu wywołań bieżącego wątku w uruchomionej aplikacji, wyświetla stosu wywołań który istniał w momencie wystąpienia wybranego zdarzenia Direct3D. Z stosu wywołań zdarzeń można przejść do witryny wywołania wybranego zdarzenia Direct3D do zbadania otaczającego kodu.  
  
 Za pomocą stosu wywołań zdarzeń do identyfikowania ścieżkę kodu, z którego pochodzi to zdarzenie problemu, można wywnioskować potencjalne źródła problemu swoją wiedzę na temat bazy kodu lub dodać punkty przerwania w kodzie źródłowym aplikacji tak, aby można było używać tradycyjny debugowanie techniki, aby sprawdzić, jak stan aplikacji lub zdarzeń parametrów powodują zdarzenia błędne działanie. W ten sposób mogą pomóc problemów w kodzie źródłowym, który tylko dyskowe widoczne jako problemy z renderowaniem.  
  
### <a name="graphics-event-call-stack-information"></a>Informacje stosu wywołań zdarzeń grafiki  
 Stos wywołań zdarzeń nie obsługuje wstępne ramki lub zdarzenia zdefiniowane przez użytkownika. Stos wywołań zdarzeń grafiki jest wyświetlana w formacie tabeli.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Symbol, który unikatowo identyfikuje funkcji, które zawiera miejsce wywołania. Symbolu debugowania dla funkcji jest wyświetlane, gdy jest on dostępny; w przeciwnym razie zostanie wyświetlony przesunięcie funkcji.|  
|**Plik**|Nazwa pliku pliku kodu źródłowego lub plik biblioteki, które zawiera miejsce wywołania.|  
|**Lokalizacja**|Numer wiersza, w miejsce wywołania.|  
  
### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych  
 Aby zrozumieć grafiki wybranego zdarzenia, może być konieczne informacje o obiektach Direct3D, które są skojarzone z nim. **Stosu wywołań zdarzeń grafiki** okna zawiera łącza do tych informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)