---
title: "Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji (Projektant klas) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6cee0c289c67bb67213e963635334e96101ac690
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji (Projektant klas)
W Projektancie klas można zmienić sposób diagramu klas reprezentuje relację skojarzenia między dwoma typami z notacją członka skojarzenie notacji i na odwrót. Elementy członkowskie wyświetlane linie asocjacji często stanowi przydatne wizualizację, w jaki sposób są powiązane typy.  
  
> [!NOTE]
>  Relacje skojarzenie może być reprezentowana jako element członkowski właściwości lub pola. Aby zmienić skojarzenie notacji notacją członka, jeden typ musi mieć członkiem innego typu. Aby zmienić skojarzenie notacji notacją członka, dwa typy musi być dołączony do linia skojarzenia. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie skojarzenia między typami (Projektant klas)](../ide/how-to-create-associations-between-types-class-designer.md). Jeśli projekt zawiera wiele diagramów klas, zmiany wprowadzone w sposób diagram przedstawia relacje skojarzenia wpływa na tylko tego diagramu. Aby zmienić sposób innego diagramu zawiera relacje skojarzenia, Otwórz lub wyświetlić ten diagram i wykonaj następujące kroki.  
  
### <a name="to-change-member-notation-to-association-notation"></a>Aby zmienić notacją członka skojarzenie notacji  
  
1.  W węźle projekt w Eksploratorze rozwiązań Otwórz plik diagramu (.cd) klasy.  
  
2.  Typ kształtu na diagramie klas, kliknij prawym przyciskiem myszy element członkowski właściwości lub pola reprezentujący skojarzenie, a następnie wybierz pozycję **Pokaż jako skojarzenie**.  
  
    > [!TIP]
    >  Jeśli nie właściwości lub pola są widoczne w kształcie typu, może zostać zwinięty przedziałów w kształcie. Aby rozszerzyć kształtu typu, kliknij dwukrotnie nazwę przedziału lub kształtu typu prawym przyciskiem myszy i wybierz **rozwiń**.  
  
     Element członkowski zniknie z przedziału kształtu typu i linia asocjacji wydaje się połączyć z dwóch typów. Linia asocjacji jest oznaczony nazwę właściwości lub pola.  
  
### <a name="to-change-association-notation-to-member-notation"></a>Aby zmienić skojarzenie notacji Notacja członka  
  
-   Na diagramie klas, kliknij prawym przyciskiem myszy linię skojarzenia, a następnie wybierz pozycję **Pokaż jako właściwość** lub **Pokaż jako pole** odpowiednio.  
  
     Linia asocjacji znika, a właściwość wyświetla w odpowiedni przedział w jego typ kształtu na diagramie.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie dziedziczenia pomiędzy typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Porady: wyświetlanie dziedziczenia pomiędzy typami (Projektant klas)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md)   
 [Porady: wizualizacja skojarzeń kolekcji (Projektant klas)](../ide/how-to-visualize-a-collection-association-class-designer.md)