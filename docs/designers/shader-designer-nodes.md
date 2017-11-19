---
title: "Węzły projektanta programu do cieniowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2393d254ee2864291a0a3ae5bbed6e78d80d3863
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="shader-designer-nodes"></a>Węzły Shader Designer
Artykuły w tej sekcji dokumentacji zawierają informacje o różnych węzłach Projektant programu do cieniowania, które umożliwia tworzenie efektów grafiki.  
  
## <a name="nodes-and-node-types"></a>Węzły i typy węzłów  
 Projektant programu do cieniowania reprezentuje efekty wizualne jako wykresu. Wykresy te są tworzone z węzłów, które w szczególności wybrany i połączenia dokładne sposoby na osiągnięcie zamierzonego efektu domina. Każdy węzeł odpowiada informacji lub funkcji matematycznych, a sposób informacje przechodzi przez wykres w celu utworzenia wyniku połączenia między nimi. Projektant programu do cieniowania udostępnia sześciu różnych typów węzłów — filtry, węzłów tekstury, parametry, stałe, narzędzie węzłów i węzłów matematyczne — i kilka poszczególne węzły należą do każdego typu. Te węzły i typy węzłów, które zostały opisane w inne artykuły w tej sekcji — Zobacz łącza na końcu niniejszego dokumentu.  
  
## <a name="node-structure"></a>Struktura węzła  
 Wszystkie węzły składają się z kombinacji wspólne elementy. Każdy węzeł ma co najmniej jedno wyjście terminali po jego prawej stronie (z wyjątkiem węzła ostateczny kolor, który reprezentuje dane wyjściowe programu do cieniowania). Węzły, które reprezentują obliczeń lub próbników tekstury ma wejściowych terminale na swoich stronach po lewej stronie, ale węzły, które reprezentują informacji ma nie terminale wejściowego. Terminale dane wyjściowe są połączone z danych wejściowych terminale, aby przenieść informacji z jednego węzła.  
  
### <a name="promotion-of-inputs"></a>Podwyższanie poziomu danych wejściowych  
 Projektant programu do cieniowania musi ostatecznie generować kod źródłowy HLSL tak, aby skutki mogą być używane w aplikacji lub grę, dlatego węzłach projektanta programu do cieniowania podlegają reguł promocja typu, które używa HLSL. Ponieważ sprzęt graficzny działa przede wszystkim na wartości zmiennoprzecinkowe, wpisz podwyższania poziomu między różnymi typami — na przykład z `int` do `float`, lub z `float` do `double`— jest rzadko. Zamiast tego ponieważ sprzęt graficzny korzysta z tej samej operacji na wielu rodzajów informacji jednocześnie, innego rodzaju podwyższania poziomu mogą wystąpić, w którym krótszego liczbę wejść jest dłużej, aby był zgodny z rozmiarem najdłuższy wejściowych. Jak jest dłużej zależy od typu danych wejściowych, a także na samą operacją:  
  
-   **Jeśli na mniejszy typ jest wartością skalarną:**  
  
     Wartości skalarnych są replikowane do wektora, który jest taki sam rozmiar większy danych wejściowych. Na przykład skalarne wprowadzania 5.0 staje się wektora (5.0, 5.0, 5.0) podczas największego danych wejściowych operacji jest wektorem trzech elementu, niezależnie od tego, jakie działanie.  
  
-   **Jeśli mniejszy typ jest wektorem, a operacja jest mnożenia (\*, /, % i tak dalej), następnie:**  
  
     Wartość wektora jest kopiowana do początku elementów wektora, który jest taki sam rozmiar większy dane wejściowe i końcowe elementy są ustawione na 1.0. Na przykład wektor danych wejściowych (5.0, 5.0) staje się wektora (5.0, 5.0, 1.0, 1.0) gdy iloczyn wektor czterech elementu. Pozwala to zachować trzeci i czwarty elementy danych wyjściowych przy użyciu tożsamości mnożenia, 1.0.  
  
-   **Jeśli mniejszy typ jest wektorem, a operacja dodawania (+, - i tak dalej), następnie:**  
  
     Wartość wektora jest kopiowana do początku elementów wektora, który jest taki sam rozmiar większy dane wejściowe i końcowe elementy są wartość 0,0. Na przykład wektor danych wejściowych (5.0, 5.0) staje się wektora (5.0, 5.0, 0.0, 0.0) po dodaniu do wektora czterech elementu. Pozwala to zachować trzeci i czwarty elementy danych wyjściowych przy użyciu tożsamości dodatku, 0,0.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Węzły stałej](../designers/constant-nodes.md)|W tym artykule opisano węzły, które służą do reprezentowania wartości literałów i interpolowane informacji o stanie wierzchołków w obliczeniach cieniowania. Ponieważ wierzchołek stanu są interpolowane — i w związku z tym jest różne dla każdego piksela — każde wystąpienie programu do cieniowania pikseli odbiera innej wersji stałej.|  
|[Parametr węzłów](../designers/parameter-nodes.md)|W tym artykule opisano węzły, które służą do reprezentowania pozycji aparatu fotograficznego, właściwości materiału oświetlenia parametry, czas i inne informacje stan aplikacji w obliczeniach cieniowania.|  
|[Węzły tekstury](../designers/texture-nodes.md)|W tym artykule opisano węzły, które służy do próbkowania różne typy tekstury i mają geometrię i do utworzenia lub Przekształcanie współrzędnych tekstury typowe sposoby.|  
|[Węzły matematyczne](../designers/math-nodes.md)|W tym artykule opisano węzły, które służy do wykonywania algebraicznych, logiki trygonometryczne i innych operacji matematycznych, które mapują bezpośrednio do instrukcji HLSL.|  
|[Narzędzie węzłów](../designers/utility-nodes.md)|W tym artykule opisano węzły, które służy do wykonywania typowych obliczeń oświetlenia i innymi typowymi operacjami, które mapują bezpośrednio do instrukcji HLSL.|  
|[Węzły filtru](../designers/filter-nodes.md)|W tym artykule opisano węzły, które służy do filtrowania tekstury i filtrowanie kolorów.|