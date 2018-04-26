---
title: Menu kontekstowe w Eksploratora schematu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79f128968d810120c40b797715bd0df325116414
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="context-menus-xml-schema-explorer"></a>Menu kontekstowe (Eksploratora schematu XML)

Następujące elementy menu kontekstowego są używane do wykonywania wyszukiwania dotyczące schematu i inne operacje.

## <a name="node-type-schema-set"></a>Typ węzła: Zestawie schematów

W poniższej tabeli opisano opcje, które są dostępne dla węzła zestawu schematu.

|Opcja|Opis|
|------------|-----------------|
|**Pokaż najbardziej prawdopodobne elementy główne**|Wyszukuje i prezentuje wszystkie elementy globalne, które nie są wywoływane z globalnego elementów innego niż on sam.|
|**Pokaż typy globalne**|Wyszukuje i prezentuje wszystkie typy globalne w zestawie schematów.|
|**Pokaż elementy globalne**|Wyszukuje i prezentuje wszystkie elementy globalne w zestawie schematów.|
|**Okno właściwości**|Otwiera **właściwości** okna (Jeśli nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

## <a name="node-type-namespace"></a>Typ węzła: Namespace
 W poniższej tabeli opisano opcje, które są dostępne dla węzła przestrzeni nazw.

|Opcja|Opis|
|------------|-----------------|
|**Pokaż wszystkie odwołania dla ruchu przychodzącego**|Wyszukuje i zaznacza pliki, które importują wybranego obszaru nazw.|
|**Pokaż wszystkie odwołania ruchu wychodzącego**|Dla każdego pliku w wybranej przestrzeni nazw wyszukuje i wyróżnia się następujące:<br /><br /> -Wszystkie obszary nazw, do którego odwołuje się zaimportować instrukcje bez `schemaLocation` atrybutu.<br />-Wszystkie pliki w przestrzeniach nazw innych niż wybrana, które są określone w `schemaLocation` atrybutu podczas importowania i instrukcji #include.|
|**Pokaż typy globalne**|Wyszukuje i prezentuje wszystkie typy globalne w wybranej przestrzeni nazw.|
|**Pokaż elementy globalne**|Wyszukuje i prezentuje wszystkie elementy globalne w wybranej przestrzeni nazw.|
|**Okno właściwości**|Otwiera **właściwości** okna (Jeśli nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

## <a name="node-type-file"></a>Typ węzła: plik
 W poniższej tabeli opisano opcje, które są dostępne dla węzła pliku.

|Opcja|Opis|
|------------|-----------------|
|**Pokaż wszystkie odwołania dla ruchu przychodzącego**|Wyszukuje i prezentuje wszystkie pliki, które określają wybrany plik w `schemaLocation` atrybuty ich instrukcje include i importowania.|
|**Pokaż wszystkie odwołania ruchu wychodzącego**|Wyszukuje i wyróżnione są następujące:<br /><br /> -Wszystkie przestrzenie nazw określona w wszystkie atrybuty przestrzeni nazw zaimportować instrukcji, które nie mają `schemaLocation` atrybutu.<br />-Wszystkie pliki określone w `schemaLocation` wszystkie atrybuty zaimportować i instrukcji #include.|
|**Pokaż typy globalne**|Wyszukuje i prezentuje wszystkie typy globalne w tym pliku.|
|**Pokaż elementy globalne**|Wyszukuje i prezentuje wszystkie elementy globalne w tym pliku.|
|**Kod widoku**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w Eksploratora schematu XML zostaną również wybrane w edytorze XML.|
|**Okno właściwości**|Otwiera **właściwości** okna (Jeśli nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

## <a name="all-global-node-types"></a>Wszystkie typy węzłów globalne
 W poniższej tabeli opisano opcje, które są dostępne dla wszystkich węzłów globalnego.

|Opcja|Opis|
|------------|-----------------|
|**Pokaż w widoku wykresu**|Otwiera widok wykresu. Jeśli wybrany węzeł nie jest w obszarze roboczym, dodaje go do obszaru roboczego i wybiera węzeł.|
|**Pokaż w widoku modelu zawartości**|Otwiera widok modelu zawartości. Jeśli wybrany węzeł nie jest w obszarze roboczym, dodaje go do obszaru roboczego i wybiera węzeł.|
|**Kod widoku**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w Eksploratora schematu XML zostaną również wybrane w edytorze XML.|
|**Okno właściwości**|Otwiera **właściwości** okna (Jeśli nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

## <a name="node-type-element"></a>Typ węzła: Element
 Oprócz opcji do globalnego węzła opisane powyżej menu kontekstowe dla węzłów elementów ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Przejdź do definicji typu**|Przechodzi do definicji typu wybranego elementu. Ma to zastosowanie, gdy typ, który jest używany dla elementu jest typu globalnego.|
|**Przejdź do oryginalnego elementu**|Odwołania elementu przechodzi do rzeczywistego definicji elementu.|
|**Pokaż wszystkie odwołania**|Globalne elementów znajduje i zaznacza wszystkie odwołania (elementów, które mają `ref="selectedElement"`) do wybranego elementu.|
|**Pokaż elementy członkowskie grupy podstawienia**|Dla głowic grupy podstawienia, wyszukuje i zaznacza wszystkie elementy, które są elementami członkowskimi wybrany element jest elementem członkowskim grupy podstawienia. Oznacza to, bezpośrednie i pośrednie uczestników.|
|**Grupa podstawienia Pokaż głowic**|Dla elementów globalne, które są elementami członkowskimi grupy podstawienia, wyszukuje i prezentuje wszystkie głowic bezpośrednie i pośrednie dla wybranego elementu, takie jak następujące:<br /><br /> -Grupy podstawienia head określonego dla wybranego elementu.<br />-Określone w jego element head head grupy podstawienia.|
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnego. Generuje przykładowy plik XML dla elementu globalnego.|

## <a name="node-type-global-types"></a>Typ węzła: Typy globalne
 Oprócz opcji do globalnego węzła opisane powyżej menu kontekstowe węzłów typu globalnego ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Pokaż typu podstawowego**|Jeśli wybrany typ pochodzi z typu globalnego, przechodzi do typu podstawowego wybranego typu.|
|**Pokaż wszystkie odwołania**|Wyszukuje i prezentuje wszystkie odwołania do wybranego typu. W tym elementów i atrybutów wybranego typu i typy pochodzące od wybranego typu.|
|**Pokaż wszystkie typy pochodne**|Wyszukuje i prezentuje wszystkie typy, które są bezpośrednio i pośrednio pochodzi od wybranego typu.|
|**Pokaż wszystkich elementów nadrzędnych**|Pokaż wszystkie typy nadrzędnego (podstawowy).|

## <a name="node-type-attribute"></a>Typ węzła: atrybut
 Oprócz opcji do globalnego węzła opisane powyżej menu kontekstowe węzłów atrybutu ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Przejdź do definicji typu**|Jeśli typ, który jest używany dla atrybutu jest typu globalnego, przechodzi do definicji typu wybranego atrybutu.|
|**Przejdź do oryginalny atrybut**|Atrybut odwołania przechodzi do rzeczywistego definicji atrybutu.|
|**Pokaż wszystkie odwołania**|Dla atrybutami globalnymi, wyszukuje i zaznacza wszystkie odwołania (inne atrybuty, które mają `ref="selectedAttribute"`) do wybranego atrybutu.|

## <a name="node-type-attribute-group"></a>Typu węzła: Grupa atrybutów
 Oprócz opcji do globalnego węzła opisane powyżej menu kontekstowego dla węzłów grupy atrybutów ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Przejdź do definicji**|Dla odwołań przechodzi do rzeczywistego definicji atrybutu.|
|**Pokaż wszystkie elementy członkowskie**|Wyszukuje i zaznacza wszyscy członkowie grupy atrybutów.|
|**Pokaż wszystkie odwołania**|Wyszukuje i prezentuje wszystkie odwołania (grup, które mają atrybut `ref="selectedAttributeGroup"`) do wybranej grupy atrybutów.|

## <a name="node-type-named-group"></a>Typu węzła: Grupa o nazwie
 Oprócz opcji do globalnego węzła opisane powyżej menu kontekstowego dla węzłów grupy o nazwie ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Przejdź do definicji**|Dla odwołań przechodzi do rzeczywistego definicji atrybutu.|
|**Pokaż wszystkie elementy członkowskie**|Wyszukuje i zaznacza wszyscy członkowie grupy o nazwie.|
|**Pokaż wszystkie odwołania**|Wyszukuje i prezentuje wszystkie odwołania (grup, które mają `ref="selectedGroup"`) do wybranej grupy.|

## <a name="see-also"></a>Zobacz też

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)
- [Wyszukiwanie zestawu schematów](../xml-tools/searching-the-schema-set.md)