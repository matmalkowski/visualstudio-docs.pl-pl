---
title: Sortowanie, filtrowanie i grupowanie w Eksploratora schematu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a3e281f8e3995cf22100d328089f1993110f756
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693672"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortowanie, filtrowanie i grupowania (Eksploratora schematu XML)

W tym temacie opisano opcje, które są dostępne za pośrednictwem **sortowanie, filtrowanie i opcje grupowania** menu **Eksploratora schematu XML** paska narzędzi.

## <a name="filter-options"></a>Opcje filtru

 Dostępne są następujące opcje filtru. Domyślnie **Pokaż obszary nazw** i **Pokaż pliki schematu** są zaznaczone opcje.

-   **Pokaż obszary nazw**.

-   **Pokaż pliki schematów**.

-   **Pokaż Kompozytory (sekwencji/choice/all)**.

## <a name="sorting-options"></a>Opcje sortowania

 Dostępne są następujące opcje sortowania. Wartość domyślna to **sortowania według typu**. **Sortuj według** opcje nie dotyczą plików i przestrzenie nazw.

-   **Sortuj według typu**.

-   **Sortuj według nazwy**.

-   **Dokument kolejności**.

### <a name="sort-by-type"></a>Sortuj według typu

 Gdy **sortowania według typu** opcja jest zaznaczona, globalne węzły są sortowane w następującej kolejności. Węzły są następnie sortowana alfabetycznie w każdej grupie.

1.  `import` węzły.

2.  `include` węzły.

3.  `redefine` węzły.

4.  `attribute` węzły.

5.  `attributeGroup` węzły.

6.  `complexType` węzły.

7.  `simpleType` węzły.

8.  `element` węzły.

9. `group` węzły.

### <a name="sort-by-name"></a>Sortuj według nazwy

 Gdy **sortowania według nazwy** opcja jest zaznaczona, globalne węzły są sortowane w następującej kolejności:

1.  `import` węzły (w kolejności alfabetycznej przestrzeni nazw).

2.  `include` węzły (w kolejności alfabetycznej `schemaLocation` atrybutów).

3.  `redefine` węzły (w kolejności alfabetycznej `schemaLocation` atrybutów).

4.  Inne węzły globalne w kolejności alfabetycznej.

### <a name="document-order"></a>Kolejności dokumentów

 **Kolejności dokumentu** opcja jest dostępna, gdy **Pokaż pliki schematu** opcja jest zaznaczona. Gdy **kolejności dokumentu** jest zaznaczone, globalne węzły są wyświetlane w kolejności, w jakiej występują w pliku schematu.

## <a name="persisting-sortfilter-options"></a>Utrwalanie opcje sortowania/filtrowania

 Sortowanie, filtrowanie i opcje grupowania są zapisywane w rejestrze dla poszczególnych użytkowników, niezależnie od tego, które rozwiązanie lub pliki były otwarte podczas ustawienia zostały zmienione.