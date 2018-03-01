---
title: "Widok - dane Kontencji szczegółów zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5a3deacd563759c2c6185ed8d2a57a2c0b00ce63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="resource-details-view---contention-data"></a>Widok szczegółów zasobów - dane Kontencji
Widok szczegółów zasobów przedstawia wykres osi czasu zdarzeń blokujące, które zostały spowodowane rywalizacji za pośrednictwem wybranego zasobu. To blokującego zdarzenie występuje, gdy wątek jest wymuszone wstrzymania wykonywania, ponieważ inny wątek został zablokowany dostęp do zasobu.  
  
 Ten widok reprezentuje osi czasu wykonywania każdego wątku jako poziomy pasek i reprezentuje każdego zdarzenia blokowania jako pasek pionowy w wątku na osi czasu. W razie potrzeby można powiększyć sekcji osi czasu, aby wyświetlić poszczególne zdarzenia. Aby wyświetlić ścieżki wykonywania (stosu wywołań), funkcji, które doprowadziły do zdarzenia, kliknij na pasku zdarzeń. Funkcje są wyświetlane w **stos wywołań** okna. Po udostępnieniu kodu źródłowego dla funkcji, można kliknąć nazwę funkcji do edycji pliku źródłowego w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-magnify-a-timeline-segment"></a>Aby powiększyć segment osi czasu  
  
-   Przeciągnij wskaźnik myszy nad obszarem osi czasu.  
  
     Po zwolnieniu przycisku myszy widoku powiększa do segmentu wybrana wartość czasu. Możesz powtarzać proces dalsze powiększać segmentu. Pole przewijania na pasku przewijania czasu reprezentuje rozmiar względny segmentu czasu, która jest wyświetlana w widoku.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Aby pomniejszyć na osi czasu  
  
-   Wykonaj jedną z następujących czynności:  
  
    -   Kliknij przycisk **Pomniejsz** aby powrócić do poprzedniego poziomu powiększenia.  
  
    -   Kliknij przycisk **zresetować powiększenie** aby pokazać wszystkie osi czasu, w widoku.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Aby wyświetlić stos wywołań zdarzeń  
  
-   Na wykresie osi czasu kliknij na pasku zdarzeń.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Aby wyświetlić lub edytować kodu źródłowego funkcji w stosie wywołań  
  
-   W **stos wywołań** okna, kliknij nazwę funkcji.  
  
 Kod źródłowy funkcja musi być częścią bieżącego projektu.  
  
#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Aby wyświetlić drzewo wywołań rywalizacji zdarzeń dla zasobu  
  
-   Na wykresie osi czasu, kliknij przycisk **całkowita**.  
  
     Widok Kontencji pojawia się dla zasobu. Aby uzyskać więcej informacji, zobacz [widok Kontencji zasobów](../profiling/resource-contentions-view-contention-data.md)  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Aby wyświetlić wszystkie zdarzenia rywalizacji wątku  
  
-   Na wykresie osi czasu kliknij nazwę lub identyfikator wątku.  
  
     Dla wybranego wątku zostanie wyświetlony widok szczegółów wątku. Aby uzyskać więcej informacji, zobacz [widok szczegółów wątku](../profiling/thread-details-view-contention-data.md).