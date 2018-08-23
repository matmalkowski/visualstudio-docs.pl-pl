---
title: Wyszukiwanie zestawu schematów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6ce05cbaf203649ce62d13285f7304c04be6497
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680538"
---
# <a name="searching-the-schema-set"></a>Wyszukiwanie zestawu schematów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wyszukiwania zestawu schematu](https://docs.microsoft.com/visualstudio/xml-tools/searching-the-schema-set).  
  
  
Eksplorator schematu XML umożliwia wyszukiwanie schematu ustawiony w następujący sposób:  
  
-   Wyszukiwanie słów kluczowych.  
  
-   Wyszukiwanie specyficzne dla schematu.  
  
## <a name="keyword-search"></a>Wyszukiwanie słów kluczowych  
 Wyszukiwanie słów kluczowych, wprowadzając podciągu w **SchemaSet wyszukiwania** pola tekstowego, na pasku narzędzi Eksploratora schematu XML.  
  
 ![Wyszukiwanie słów kluczowych Eksploratora schematu XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 Eksplorator schematu XML przeszukuje zestawie dla następujących schematów:  
  
-   Wszelkie `name` lub `ref` atrybuty, które pasują do określonego słowa kluczowego. Dzięki temu można znaleźć elementy, atrybuty, typy, i tak dalej według nazwy.  
  
-   `schemaLocation` Atrybuty instrukcji #include.  
  
-   `namespace` Atrybuty instrukcje importowania.  
  
## <a name="schema-specific-search"></a>Wyszukiwanie określonego schematu  
 Eksplorator schematu XML zawiera także wbudowaną wyszukiwania, które mogą uzyskać dostęp za pomocą menu kontekstowego Eksploratora schematu XML. Aby uzyskać więcej informacji na temat menu kontekstowe dostępne zobacz [menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md). Można również wykonać wyszukiwanie specyficzne dla schematu z widoku startowego; Aby uzyskać więcej informacji, zobacz sekcję "Szczegóły zestawu schematów" w [widoku Start](../xml-tools/start-view.md) tematu.  
  
## <a name="displaying-and-navigating-search-results"></a>Wyświetlanie i nawigowanie wyników wyszukiwania  
 Po zakończeniu wyszukiwania w okienku wyników podsumowania jest dodawany do paska narzędzi z wynikami wyszukiwania. Wyniki wyszukiwania są również wyróżnione Eksploratora schematu XML i oznaczony za znaczniki na pionowy pasek przewijania. Wyniki wyszukiwania można nawigować przy użyciu **przejdź do następnego wyniku wyszukiwania** i **przejdź do poprzedniego wyniku wyszukiwania** przycisków w okienku wyników podsumowania na pasku narzędzi Eksploratora schematu XML; za pomocą klawiszy F3 i Shift + F3 lub klikając znaczniki na pasku przewijania.  
  
 Wyniki wyszukiwania można dodać do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku wyników podsumowania.  
  
 ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Czyszczenie wyników wyszukiwania  
 Aby wyczyścić wyniki wyszukiwania, kliknij pozycję **x** przycisk na pasku wyszukiwania Eksploratora schematu XML, w okienku wyników podsumowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)



