---
title: Wyszukiwanie zestawu schematu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6328e3febf8d7279ad0a4bcac3ca4be54eb42c20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="searching-the-schema-set"></a>Wyszukiwanie zestawu schematów
Eksploratora schematu XML umożliwia wyszukiwanie schematu ustawiony w następujący sposób:  
  
-   Wyszukiwanie słów kluczowych.  
  
-   Wyszukiwania specyficznego dla schematu.  
  
## <a name="keyword-search"></a>Wyszukiwanie słów kluczowych  
 Wyszukiwanie słów kluczowych, wprowadzając podciągu w **SchemaSet wyszukiwania** pole tekstowe narzędzi Eksploratora schematu XML.  
  
 ![Wyszukiwanie słów kluczowych Eksploratora schematu XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 Eksploratora schematu XML wyszukuje zestawie dla następujących schematów:  
  
-   Wszelkie `name` lub `ref` atrybuty, które odpowiada określonym słowem kluczowym. Dzięki temu można znaleźć elementy, atrybuty, typy, i tak dalej według nazwy.  
  
-   `schemaLocation` Atrybuty instrukcji #include.  
  
-   `namespace` Atrybuty instrukcje importu.  
  
## <a name="schema-specific-search"></a>Wyszukiwanie określonego schematu  
 Eksploratora schematu XML zawiera również wbudowane wyszukiwania, które mogą korzystać za pomocą menu kontekstowego Eksploratora schematu XML. Aby uzyskać więcej informacji na temat menu kontekstowe dostępne, zobacz [menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md). Można również wykonać wyszukiwanie określonego schematu z widoku startowego; Aby uzyskać więcej informacji, zobacz sekcję "Schematu Określanie szczegółów" w [widoku startowego](../xml-tools/start-view.md) tematu.  
  
## <a name="displaying-and-navigating-search-results"></a>Wyświetlanie i przechodząc wyniki wyszukiwania  
 Po zakończeniu wyszukiwania w okienku wyników podsumowania jest dodawany do paska narzędzi z wynikami wyszukiwania. Wyniki wyszukiwania są również wyróżnione Eksploratora schematu XML i oznaczone przez znaczniki na pionowy pasek przewijania. Wyniki wyszukiwania można przejść za pomocą **przejdź do następnego wyniku wyszukiwania** i **przejdź do wyników poprzedniego wyszukiwania** przycisków w okienku wyników podsumowania narzędzi Eksploratora schematu XML; za pomocą klawiszy klawiatury F3 i Shift + F3; lub przez kliknięcie przycisku znaczników na pasku przewijania.  
  
 Wyniki wyszukiwania można dodać do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku podsumowania wyników.  
  
 ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Czyszczenie wyników wyszukiwania  
 Wyczyść wyniki wyszukiwania, kliknij przycisk **x** przycisku w okienku wyników podsumowania narzędzi wyszukiwanie Eksploratora schematu XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)