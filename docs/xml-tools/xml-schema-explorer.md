---
title: Eksplorator schematu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 110cad9883cbb129368dac4d481443a9f5d9813c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751592"
---
# <a name="xml-schema-explorer"></a>Eksplorator schematu XML

**Eksploratora schematu XML** jest zintegrowany z programu Microsoft Visual Studio i edytora XML, aby umożliwić pracę z schematu XML definition language (XSD) schematów. Po otwarciu pliku schematu XML **zestawu schematu** węzeł jest dostępny w **Eksploratora schematu XML**. Wszystkich schematów dołączone, importowany lub ponownie zdefiniowany dla pliku docelowego, a także wszystkie pliki, które są przywoływane przez `include` lub `import` instrukcji, jest również dostępna w **Eksploratora schematu XML**.

 **Eksploratora schematu XML** umożliwia wykonywanie następujących czynności:

-   Pobierz szybki przegląd zestawie schematów.

-   Przeglądaj i przejdź drzewa.

-   Wykonaj — słowo kluczowe i umożliwia wyszukiwanie określonego schematu. Aby uzyskać więcej informacji, zobacz [wyszukiwania zestawu schematu](../xml-tools/searching-the-schema-set.md).

-   Dodaj wyniki wyszukiwania do widoku wykresu lub widok modelu zawartości

-   Sortuj według kolejności dokumentów, typu lub nazwa drzewa. Aby uzyskać więcej informacji, zobacz [sortowanie, filtrowanie i grupowanie](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

-   Otwórz Edytor XML, a następnie przejść do lokalizacji kodu w pliku XSD. Aby uzyskać więcej informacji, zobacz [integracji z edytora XML](../xml-tools/integration-with-xml-editor.md).

-   Generowanie przykładowy kod XML globalnego elementów.

**Eksploratora schematu XML** hierarchiczna Wyświetla schematu ustawiana za pośrednictwem widoku drzewa. **Eksploratora schematu XML** udostępnia również wyszukiwanie, filtrowanie, nawigacji i sortowania. Aby uzyskać dostęp do **Eksploratora schematu XML**, wykonaj jedną z następujących czynności:

-   Jeśli pracujesz w [widoku startowego](../xml-tools/start-view.md), kliknij przycisk **Eksploratora schematu XML** łącza.

-   Jeśli pracujesz w [widok wykresu](../xml-tools/graph-view.md) lub [widoku modelu zawartości](../xml-tools/content-model-view.md) i mieć węzłów w obszarze roboczym, użyj menu kontekstowego, aby wybrać **Eksploratora schematu XML**.

-   Możesz też wybrać **Eksploratora schematu XML** z **widoku** menu.

-   Dostęp można uzyskać **Eksploratora schematu XML** z *.vb* pliku, który został skojarzony z literałem XML w Visual Basic *XSD* pliku. Aby wyświetlić schemat zestawu w **Eksploratora schematu XML**, kliknij prawym przyciskiem myszy węzeł XML w literał XML lub importu przestrzeni nazw XML i wybierz **Pokaż w Eksploratorze schematu** polecenia. Aby uzyskać więcej informacji, zobacz [literały integracji XML z Eksploratora schematu XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Widok drzewa
 **Eksploratora schematu XML** schematu Wyświetla wstępnie skompilowany ustawić informacji w strukturze drzewa. Struktura drzewa jest zorganizowana w następujący sposób:

-   Na najwyższym poziomie schematu ustawiono węzła.

-   Drugi poziom zawiera przestrzenie nazw.

-   Trzeci poziom zawiera pliki.

-   Poziom czwarty zawiera węzły globalnego. Może to obejmować elementy, grupy, typy złożone, proste typy atrybutów, grupy atrybutów i `include`, `import`, i `redefine` instrukcje.

Poniżej przedstawiono przykład struktury drzewa:

![Eksplorator schematu XML](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Wybór i aktywacji
 Aby wyróżnić, a następnie wybierz węzeł, kliknij raz w Eksploratorze schematu.

 Aby aktywować węzeł, kliknij go dwukrotnie lub naciśnij klawisz **Enter** po wybraniu węzła.

-   Aktywowanie węzła otwiera plik, w którym ten węzeł jest zdefiniowany (Jeśli plik nie jest już otwarty) i wybiera węzeł w pliku.

-   Aktywowanie węzeł pliku Otwiera wybrany plik (Jeśli nie jest już otwarty) i zaznacza `<schema>` węzła.

-   Aktywowanie SchemaSet lub węzła przestrzeni nazw nie działa.

## <a name="drag-and-drop-nodes"></a>Przeciągnij i upuść węzłów
 Możesz przeciągać i upuszczać globalne węzłów, węzły plików i węzłów przestrzeni nazw na widok projektanta XSD. Jeśli bieżący widok jest [widoku startowego](../xml-tools/start-view.md), przeciąganie węzła do widoku spowoduje otwarcie [widok wykresu](../xml-tools/graph-view.md). Jeśli bieżący widok jest [widoku modelu zawartości](../xml-tools/content-model-view.md) lub widok wykresu widoku nie zmieni się po upuszczeniu węzła na niego.

 Upuszczanie plików w widoku doda wszystkie węzły globalne w pliku [obszaru roboczego projektanta XSD](../xml-tools/xml-schema-designer-workspace.md). Usunięcie przestrzeni nazw w widoku doda wszystkie węzły globalne w przestrzeni nazw do obszaru roboczego. Obszar roboczy jest współużytkowana przez wszystkie widoki.

 Nie można przeciągania i upuszczania węzły lokalne lub importowania.

## <a name="see-also"></a>Zobacz także

- [Porady: Dodaj węzły do obszaru roboczego z Eksploratora schematu XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)