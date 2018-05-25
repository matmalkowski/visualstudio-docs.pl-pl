---
title: 'Porady: Dodaj węzły do obszaru roboczego z Eksploratora schematu XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 487cb4fe5ea15c2186f9284c557a1e9377ac801f
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Porady: Dodaj węzły do obszaru roboczego z Eksploratora schematu XML

W tym temacie opisano sposób dodawania węzłów do [obszaru roboczego projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md) z **Eksploratora schematu XML**. Można to osiągnąć poprzez przeciągnięcie i upuszczenie węzłów z **Eksploratora schematu XML** na widok projektanta XSD lub za pomocą **Eksploratora schematu XML** menu kontekstowego. Możesz także dodać węzłów, które są wyróżnione wyniku wyszukiwania z zastosowaniem **Eksploratora schematu XML**. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie węzłów wynik wyszukiwania zestawu schematu do obszaru roboczego](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Tylko węzły globalnego mogą być dodawane do [obszaru roboczego projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Aby dodać węzły za pomocą menu kontekstowego Eksploratora XML

1.  Postępuj zgodnie z instrukcjami [porady: tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzła w Eksploratorze XSD. Wybierz **Pokaż w widoku wykresu**.

     `purchaseOrderType` Węzeł jest dostępny na powierzchni projektu w widoku wykresu.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Aby przeciągnąć i upuścić węzła do widoku

1.  Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzła w widoku wykresu. Wybierz **Pokaż w Eksploratorze schematu XML**.

     Węzeł zostanie wyróżniona w **Eksploratora schematu XML**.

2.  Kliknij prawym przyciskiem myszy `PurchaseOrderType` w węźle **Eksploratora schematu XML** i wybierz **Pokaż wszystkie odwołania**.

     `purchaseOrder` Węzeł zostanie wyróżniona.

3.  Przeciągnij `purchaseOrder` węzła do widoku wykresu.

     `purchaseOrder` Węzła i `PurchaseOrderType` węźle są wyświetlane obok siebie na powierzchni projektu w widoku wykresu. Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), Strzałka jest rysowany między nimi.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Aby dodać węzły przy użyciu Eksploratora schematu możliwości wyszukiwania

1.  W polu tekstowym wyszukiwania wpisz "purchaseOrder" [XML Explorer](../xml-tools/xml-schema-explorer.md) narzędzi i kliknij przycisk wyszukiwania.

     ![Wyszukiwanie słów kluczowych Eksploratora schematu XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Wyniki wyszukiwania są wyróżnione **Eksploratora schematu XML** i oznaczone przez znaczniki na pionowy pasek przewijania.

2.  Wyniki wyszukiwania można dodać do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku podsumowania wyników.

     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     `purchaseOrder` Węzła i `PurchaseOrderType` węźle są wyświetlane obok siebie na powierzchni projektu [widok wykresu](../xml-tools/graph-view.md). Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), Strzałka jest rysowany między nimi.

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)