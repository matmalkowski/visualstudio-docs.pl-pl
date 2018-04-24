---
title: Węzły Shader Designer
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7d4bb2633571a552c13bda0795d05447f9e340c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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
|[Stałe węzły](../designers/constant-nodes.md)|W tym artykule opisano węzły, które służą do reprezentowania wartości literałów i interpolowane informacji o stanie wierzchołków w obliczeniach cieniowania. Ponieważ wierzchołek stanu są interpolowane — i w związku z tym jest różne dla każdego piksela — każde wystąpienie programu do cieniowania pikseli odbiera innej wersji stałej.|
|[Węzły parametrów](../designers/parameter-nodes.md)|W tym artykule opisano węzły, które służą do reprezentowania pozycji aparatu fotograficznego, właściwości materiału oświetlenia parametry, czas i inne informacje stan aplikacji w obliczeniach cieniowania.|
|[Węzły tekstury](../designers/texture-nodes.md)|W tym artykule opisano węzły, które służy do próbkowania różne typy tekstury i mają geometrię i do utworzenia lub Przekształcanie współrzędnych tekstury typowe sposoby.|
|[Węzły matematyczne](../designers/math-nodes.md)|W tym artykule opisano węzły, które służy do wykonywania algebraicznych, logiki trygonometryczne i innych operacji matematycznych, które mapują bezpośrednio do instrukcji HLSL.|
|[Węzły narzędzi](../designers/utility-nodes.md)|W tym artykule opisano węzły, które służy do wykonywania typowych obliczeń oświetlenia i innymi typowymi operacjami, które mapują bezpośrednio do instrukcji HLSL.|
|[Węzły filtrów](../designers/filter-nodes.md)|W tym artykule opisano węzły, które służy do filtrowania tekstury i filtrowanie kolorów.|