---
title: "Praca z programów do cieniowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c92f7975e3fe45e4f87e67f2c3c54a26a7d8b87a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-shaders"></a>Praca z cieniowaniem
Można użyć projektanta programu do cieniowania na podstawie wykresu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektowania niestandardowego programu do cieniowania skutki. Możesz użyć tych programów do cieniowania w aplikacji lub gry opartych na technologii DirectX.  
  
## <a name="shaders"></a>Programów do cieniowania  
 A *programu do cieniowania* to program komputera, który wykonuje obliczenia grafiki — na przykład przekształcenia wierzchołka lub kolorowanie pikseli — i zwykle odbywa się na procesor graficzny (GPU) zamiast Procesora. Ponieważ większość etapy potoku grafiki tradycyjnych, stałej funkcji są teraz wykonywane przez programy do cieniowania, można użyć ich do tworzenia potok, który jest przeznaczony dla potrzeb aplikacji.  
  
 Najbardziej typowych rodzajów programów do cieniowania są *programów do cieniowania wierzchołków*, który wierzchołków obliczeń i Zastąp stałej funkcja transformacji i obwody oświetlenia sprzętu nieprzewidywalnych grafiki i *pikseli programów do cieniowania*, który przeprowadzanie obliczeń na piksel określić kolor piksel i Zastąp obwody stałej funkcji kolor łączenia sprzętu nieprzewidywalnych grafiki. Sprzęt graficzny nowoczesnych wprowadził jeszcze więcej rodzaje programów do cieniowania możliwe —*programów do cieniowania powłoki są*, *domeny programów do cieniowania*, i *programów do cieniowania geometrycznego* obliczeń graficznych i *obliczeniowe programów do cieniowania* do obliczenia i grafiki. Z tych etapów nie jest jeszcze dostępna żadna sprzętu nieprzewidywalnych grafiki. Programów do cieniowania zostały pierwotnie utworzone przy użyciu języka zestawu przypominającej zapewnianej równoległe danych (SIMD) oraz instrukcje skoncentrowane grafiki (skalarnego). Teraz programów do cieniowania jest zwykle tworzony przy użyciu wysokiego poziomu, notacji języka C w językach HLSL (język programu do cieniowania poziom).  
  
 Projektant programu do cieniowania służy do tworzenia programów do cieniowania pikseli interaktywnie zamiast elementu wprowadzając i kompilowanie kodu. W projektancie programu do cieniowania programu do cieniowania jest zdefiniowany przez liczbę węzłów, które reprezentują danych i działań i połączeń między węzły, które reprezentują przepływ wartości danych i pośrednich wyników za pomocą programu do cieniowania. Przy użyciu tej metody i Podgląd w czasie rzeczywistym w projektancie programu do cieniowania, można łatwiej wizualizacji wykonywanie programu do cieniowania i "wykryć" interesujące odmiany programu do cieniowania poprzez eksperymenty.  
  
## <a name="dgsl-documents"></a>DGSL dokumentów  
 Projektant programu do cieniowania programów do cieniowania jest zapisywany w formacie skierowane wykres programu do cieniowania języka (DGSL), który jest w formacie XML, który jest oparty na przekierowanie wykres znaczników języka DGML (). DGSL programów do cieniowania można zastosować bezpośrednio do modeli 3-w edytorze modeli. Jednak zanim użyjesz cieniowania DGSL w aplikacji, należy go wyeksportować do formatu, który obsługuje usługę DirectX — na przykład HLSL.  
  
 Ponieważ DGSL jest zgodny z DGML, można użyć narzędzia, które są przeznaczone do analizowania dokumenty DGML do analizy sieci DGSL programów do cieniowania. Aby uzyskać informacje o DGML, zobacz [opis skierowane wykres znaczników języka DGML ()](http://msdn.microsoft.com/library/ee842619.aspx).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Projektant programu do cieniowania](../designers/shader-designer.md)|Informacje dotyczące używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Designer programu do cieniowania do pracy z programów do cieniowania.|  
|[Węzły projektanta programu do cieniowania](../designers/shader-designer-nodes.md)|W tym artykule omówiono rodzaje projektanta programu do cieniowania węzłów, które służy do osiągnięcia efekty graficzne.|  
|[Przykłady projektanta programu do cieniowania](../designers/shader-designer-examples.md)|Zawiera łącza do tematów, które pokazują, jak uzyskać typowe efekty grafiki za pomocą projektanta programu do cieniowania.|