---
title: Edytuj i Kontynuuj (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 825eac4ab53e95904e85a794b665ce6f6b11f873
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673362"
---
# <a name="edit-and-continue-visual-basic"></a>Edytuj i kontynuuj (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Edytuj i Kontynuuj (Visual Basic)](https://docs.microsoft.com/visualstudio/debugger/edit-and-continue-visual-basic).  
  
Edytuj i Kontynuuj jest funkcją, aby uzyskać [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] debugowania, która umożliwia zmianę kodu, podczas wykonywania w trybie przerwania. Po zastosowaniu edycji kodu można wznowić wykonywania kodu za pomocą nowego edycji w miejscu i zobaczyć efekt.  
  
 Możesz użyć edycji i kontynuowania funkcji zawsze wtedy, gdy tryb przerwania. W trybie przerwania, wskaźnika instrukcji, żółty grot strzałki w oknie źródła wskazuje na wierszu, który zostanie wykonany obok i będą znajdować się w instrukcji wykonywalnej w treści metody lub właściwości. Możesz wprowadzić niemal każdego rodzaju zmiany instrukcji wykonywalnych w trybie przerwania, a zmiany zostaną uwzględnione w podstawowej projektu. W trybie przerwania, jednak ogólnie nie możesz zmienić instrukcje deklaracji, takich jak metody publiczne, pola publiczne lub deklaracji klasy.  
  
 Po wprowadzeniu nieautoryzowane zmiany, zmiana jest oznaczona za pomocą purpurowy falistą i zadaniem jest wyświetlana na liście zadań. Jeśli chcesz nadal korzystać, Edytuj i Kontynuuj, musisz cofnąć nieautoryzowane zmiany. Może być dozwolony nieautoryzowanych zmian, jeśli będą wykonywane poza Edytuj i Kontynuuj. Jeśli chcesz zachować wyniki nieautoryzowanych edycji, należy zatrzymać debugowanie i ponownie uruchom aplikację.  
  
 Edytuj i Kontynuuj jest obsługiwana dla projektów 64-bitowych, przeznaczonych dla programu .NET Framework 4.5.1.  
  
 Edytuj i Kontynuuj nie jest obsługiwana podczas uruchamiania debugowania przy użyciu **dołączyć do procesu**. Edytuj i Kontynuuj nie jest obsługiwane dla zoptymalizowanego kodu, kod mieszany zarządzanego i natywnego lub projektów Compact Framework (urządzenia przenośne).  
  
 Tematy w tej sekcji zawierają dodatkowe szczegóły dotyczące sposobu używania tej funkcji i jakiego rodzaju zmiany są niedozwolone.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: stosowanie edycji w trybie przerwania za pomocą Edytuj i Kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Wyjaśnia sposób stosowania zmian kodu w trybie przerwania.  
  
 [Nieobsługiwane edycje w języku Visual Basic, Edytuj i Kontynuuj](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 W tym artykule opisano, jakie typy zmian nie mogą być wykonywane w [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] Edytuj i Kontynuuj.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Edytuj i Kontynuuj](../debugger/edit-and-continue.md)  
 Zawiera listę tematów na Edytuj i Kontynuuj.



