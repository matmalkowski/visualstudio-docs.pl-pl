---
title: Praca z diagramu definicji DSL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e2631a81cd907c6946993461f953a0bc1ddbf2ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-the-dsl-definition-diagram"></a>Praca z diagramem definicji DSL
Diagram [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definicji jest ważnym narzędziem do definiowania języka specyficznego dla domeny. Można dodać elementy do Twojej domeny modelu i definiowanie relacji na diagramie i możesz zmodyfikować układ diagramu, aby był bardziej czytelny.  
  
## <a name="the-layout-of-the-diagram"></a>Układ diagramu  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Diagram definicji ma dwie partycje **klasy i relacje** partycji i **elementów diagramu** partycji. **Klasy i relacje** partycji zawiera klasy domeny i relacje domeny oraz dziedziczenia. **Elementów diagramu** partycji Wyświetla kształtu klasy, klasy łącznik klasy tor i wygenerowanego diagramu projektanta.  
  
 Klasy domeny może występować w wielu lokalizacjach **klasy i relacje** partycji. Definicję klasy domeny wyświetla drzewa dziedziczenia, gdy jest klasą bazową dla innych klas domeny i drzewa relacji, gdy jest źródło relacji osadzanie lub odwołanie. Symbole zastępcze klasy domeny są wyświetlane jako elementy docelowe relacji osadzanie lub odwołanie. Domyślnie są wyświetlane elementy symbolu zastępczego **właściwości domeny** przedział zwinięty. Dziedziczenie lub relacji osadzanie lub odwołanie nie są widoczne.  
  
 Po dodaniu klasą domeny pojawia się w dolnej części **klasy i relacje** partycji. Podczas dodawania, osadzanie lub relacji odwołania, jest to rysowane w obszarze i w prawo klasy domeny źródłowej.  
  
 W miarę dodawania klasy i relacje, mogą stać się trudne do zlokalizowania klasy konkretnej domeny. Klasy domeny można znaleźć, klikając prawym przyciskiem myszy w **DSL Explorer** , a następnie klikając polecenie **odszukaj na diagramie**.  
  
 W poniższych sekcjach opisano, jak można zmienić wygląd na diagramie, aby ułatwić do odczytu.  
  
## <a name="copying-elements"></a>Kopiowanie elementów  
 Można użyć kopii, wyciąć i wkleić elementy na diagramie definicji DSL.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>Powiększanie lub pomniejszanie na diagramie  
 Można powiększyć lub pomniejszyć diagramu przy użyciu **DSL projektanta** narzędzi, aby ustawić poziom powiększenia.  
  
## <a name="hiding-map-lines"></a>Ukrywanie mapy wierszy  
 Mapa wiersze są wiersze, które są rysowane między klasą domeny lub relacji domeny i kształtu lub łącznika, na którą jest zamapowany. Można ukryć linii mapy, klikając **Pokaż linie mapy** znajdującego się na **DSL projektanta** paska narzędzi. Aby wyświetlić wiersze, kliknij ponownie przycisk.  
  
## <a name="changing-the-diagram-layout"></a>Zmiana układu diagramu  
 Można zmienić układ **klasy i relacje** partycji w następujący sposób.  
  
### <a name="expandcollapse"></a>Rozwiń/Zwiń  
 Można zmniejszyć rozmiar elementu kształtu przedział, który reprezentuje klasę domeny lub kształt go prawym przyciskiem myszy, a następnie klikając polecenie **Zwiń**. Spowoduje to ukrycie **właściwości domeny** przedział kształtu. Aby wyświetlić **właściwości domeny** przedziału ponownie, kliknij prawym przyciskiem myszy, a następnie kliknij przycisk **rozwiń**.  
  
### <a name="move-updown"></a>Przenieś w górę lub w dół  
 Można przenieść domeny klasy lub diagram element w górę lub w dół w partycji prawym przyciskiem myszy element, a następnie klikając polecenie **Przenieś w górę** lub **Przenieś w dół**. Po przeniesieniu elementu zastępczego, który jest wyświetlany jako element docelowy relacji osadzanie lub odwołanie z nim zostanie przesunięty w relacji.  
  
### <a name="expandcollapse-relationships-tree"></a>Rozwijanie/zwijanie drzewa relacji  
 Jeśli klasa domeny pełni rolę źródła w relacje osadzanie lub odwołania z innych klas domeny, można ukryć relacje prawym przyciskiem myszy definicję klasy domeny, a następnie klikając polecenie **drzewa relacji Zwiń**. Aby wyświetlić zależności, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij przycisk **rozwiń węzeł drzewa relacji**.  
  
### <a name="expandcollapse-inheritance-tree"></a>Rozwijanie/zwijanie drzewa dziedziczenia  
 Jeśli klasa domeny jest klasą podstawową innych klas domeny, można ukryć drzewa dziedziczenia prawym przyciskiem myszy definicję klasy domeny, a następnie klikając polecenie **drzewa dziedziczenia Zwiń**. Aby wyświetlić drzewa dziedziczenia, kliknij prawym przyciskiem myszy element definicji, a następnie kliknij przycisk **rozwiń węzeł drzewa dziedziczenia**.  
  
### <a name="bring-tree-here"></a>Wyświetl drzewo tutaj  
 Diagram umożliwiającej obsługę prawym przyciskiem myszy klasę domeny symbolu zastępczego, a następnie klikając polecenie **Przełącz drzewa tutaj**. Klasa domeny symbolu zastępczego staje się elementem definicji i wyświetla dziedziczenia i relacji drzewa. Element definicji wcześniejsze staje się elementu zastępczego, jeśli jest ona elementem docelowym relacji lub podrzędnej w relacji dziedziczenia; w przeciwnym razie zniknie.  
  
### <a name="split-tree"></a>Podziel drzewo  
 Prawym przyciskiem myszy definicji klasy domeny, który wyświetla je, a następnie klikając pozycję można złamać drzewa dziedziczenia lub relacje **podziału drzewa**. Element definicji staje się elementu zastępczego i definicji klasy domeny, wraz z jego dziedziczenia i drzewa relacji, zostanie wyświetlona w dolnej części partycji.  
  
### <a name="show-as-class"></a>Pokaż jako klasę  
 Jeśli relacja domeny ma relacje, lub ma relacje osadzanie lub odwołania z innych relacje domeny, można wyświetlić relacji jako klasa, prawym przyciskiem myszy relację, a następnie klikając polecenie **Pokaż jako klasy** . Relacja będzie wyświetlane z **właściwości domeny** przedziału i wyświetli drzewa dziedziczenia i relacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)