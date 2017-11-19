---
title: "Definiowanie kształty i łączniki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 745e91e7d5cbb63238fc384c2f5cc9677218fda6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="defining-shapes-and-connectors"></a>Definiowanie kształtów i łączników
Istnieje kilka typów podstawowych kształtów, które mogą być używane do wyświetlania informacji na diagramie języka specyficznego dla domeny (DSL).  
  
##  <a name="shapeTypes"></a>Podstawowe typy łączników i kształtów  
 DSL diagram zawiera zbiór *kształtów* powiązane liniami lub *łączniki*.  Zwykle, ale nie zawsze:  
  
-   Kształty są widoczne reprezentację elementy modelu.  
  
-   Łączniki reprezentowania relacji odwołania.  
  
-   Diagram reprezentuje wystąpienie katalogu głównego modelu.  
  
-   Osadzanie relacji między elementami modelu są wyświetlane przez relację zawierania. Na przykład elementy reprezentujące porty składnika są osadzone w składniku.  
  
 Te wzorce nie są wymuszane, ale więcej silnie są obsługiwane. Podczas projektowania DSL przy tym pamiętać, że projekt osadzania relacje powinny być wpływ jak mają być przedstawiane modelu na ekranie. Z kolei relacji odwołania powinien odzwierciedlać pojęcia domeny biznesowych.  
  
 Dostępne są następujące typy kształtów:  
  
|Typ kształtu|Opis|  
|----------------|-----------------|  
|Geometria kształtu|Kształt prostokątny lub eliptycznej ogólnego przeznaczenia. Tekst i ikona elementów decorator można wyświetlić w określonych pozycji względem granic kształtu.<br /><br /> Aby zagnieździć kształtów wewnątrz kształtów geometry, zobacz [zagnieżdżania kształtów](../modeling/nesting-shapes.md).|  
|Przedział kształtu|Prostokąt zawierająca nagłówek i działów, podobnie jak klasa UML. Każdego przedziału może zawierać listę wierszy tekstu.<br /><br /> Wiersze zwykle odpowiadają za elementy osadzone w elemencie reprezentowany przez kształtu. Na przykład utwórz DSL na podstawie diagramów klas szablon rozwiązania.|  
|Kształt obrazu|Kształt, który wyświetla obraz.|  
|Port kształtu|Mały prostokąt przeznaczone do dołączenia do konturu innego kształtu. Zwykle używanych w modelach składnika.<br /><br /> Element modelu reprezentowanego przez port zwykle jest osadzony w elemencie reprezentowany przez kształtu nadrzędnego. Na przykład utworzyć DSL przy użyciu składników szablon rozwiązania.<br /><br /> Domyślnie kształt portu można przesunąć wzdłuż krawędzi jego elementu nadrzędnego. Można zdefiniować zasadę granice, aby ograniczyć go do określonej pozycji.<br /><br /> Bardzo małe i przezroczysty, co kształt portu, można użyć go zapewnienie punktu połączenia stałej powierzchni jego kształtu nadrzędnego.|  
|Ścieżek|Ścieżek partycji diagramu na segmenty pozioma lub pionowa. Tor zawsze pozostaje poniżej innych kształtów na diagramie.<br /><br /> Zazwyczaj elementem nadrzędnym elementy modelu tor w modelu głównym, a inne elementy są elementem nadrzędnym na nich. Na przykład utworzyć DSL na podstawie szablonu rozwiązania przepływ zadań.|  
|Łączniki|Linii między kształtami zazwyczaj reprezentuje relacji odwołania. Można ustawić opcje Tworzenie łącznika prostej lub prostoliniowego i mają różne typy grot strzałki.|  
  
##  <a name="shapeInheritance"></a>Dziedziczenie kształtu  
 Kształt może dziedziczyć z innego kształtu. Jednak kształty muszą być tego samego rodzaju. Na przykład kształt geometrii może dziedziczyć geometrii kształtu. Kształty dziedziczone mają przedziałów i dekoratory ich kształtu podstawowego. Łączniki mogą dziedziczyć łączników.