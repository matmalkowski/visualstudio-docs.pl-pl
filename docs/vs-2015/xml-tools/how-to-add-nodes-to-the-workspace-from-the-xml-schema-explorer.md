---
title: 'Porady: Dodawanie węzłów do obszaru roboczego z Eksploratora schematu XML | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58bad7de0b907881b4fe6f21fd5c7957e692d33a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631772"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Porady: Dodawanie węzłów do obszaru roboczego z Eksploratora schematu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Dodawanie węzłów do obszaru roboczego z Eksploratora schematu XML](https://docs.microsoft.com/visualstudio/xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer).  
  
  
W tym temacie opisano sposób dodawania węzłów do [obszar roboczy Projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md) z Eksploratora schematu XML. Można to osiągnąć przez przeciąganie i upuszczanie węzłów z Eksploratora schematu XML na widok Projektant XSD lub za pomocą menu kontekstowego Eksploratora schematu XML. Można również dodać węzły, które są wyróżnione w wyniku wyszukiwania z zastosowaniem Eksploratora schematu XML. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie zestawu węzłów wyników wyszukiwania schematu do obszaru roboczego](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Tylko globalne węzły mogą być dodawane do [obszar roboczy Projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Aby dodać węzły za pomocą Menu kontekstowego Eksploratora XML  
  
1.  Postępuj zgodnie z instrukcjami w [porady: tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzła w Eksploratorze pliku XSD. Wybierz **Pokaż w widoku wykresu**.  
  
     `purchaseOrderType` Węzeł jest wyświetlany na powierzchni projektowej w widoku wykresu.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Przeciąganie i upuszczanie węzła do widoku  
  
1.  Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzeł w widoku wykresu. Wybierz **Pokaż w Eksplorator schematu XML**.  
  
     Węzeł jest wyróżniony w Eksplorator schematu XML.  
  
2.  Kliknij prawym przyciskiem myszy `PurchaseOrderType` węzła w Eksplorator schematu XML, a następnie wybierz pozycję **Pokaż wszystkie odwołania**.  
  
     `purchaseOrder` Węzeł zostanie wyróżniona.  
  
3.  Przeciągnij `purchaseOrder` węzła do widoku wykresu.  
  
     `purchaseOrder` Węzła i `PurchaseOrderType` węzła wyświetlane obok siebie na powierzchni projektowej w widoku wykresu. Ponieważ dwa węzły, które widać ( `purchaseOrder` element jest `PurchaseOrderType` typu), Strzałka jest rysowana między nimi.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Aby dodać węzły za pomocą funkcji wyszukiwania Eksploratora schematu  
  
1.  W polu tekstowym wyszukiwania wpisz "purchaseOrder" [Eksplorator XML](../xml-tools/xml-schema-explorer.md) paska narzędzi i kliknij przycisk wyszukiwania.  
  
     ![Wyszukiwanie słów kluczowych Eksploratora schematu XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Wyniki wyszukiwania są wyróżnione Eksploratora schematu XML i oznaczone przez znaczniki na pionowy pasek przewijania.  
  
2.  Dodaj wyniki wyszukiwania do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku wyników podsumowania.  
  
     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` Węzła i `PurchaseOrderType` węzła wyświetlane obok siebie na powierzchni projektowania [widoku wykresu](../xml-tools/graph-view.md). Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), Strzałka jest rysowana między nimi.  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)



