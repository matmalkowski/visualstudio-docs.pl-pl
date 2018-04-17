---
title: 'Porady: zbadanie modelu zawartości węzłów przy użyciu widoku modelu zawartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4b2430cd90a63d02503a99e26c893a3f59a5246
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Porady: zbadanie modelu zawartości węzłów przy użyciu widoku modelu zawartości
W tym temacie opisano sposób Eksploruj węzły za pomocą [widoku modelu zawartości](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości  
  
1.  Utwórz nowy plik schematu XML.  
  
2.  Kliknij przycisk **Użyj edytora XML możesz wyświetlać i edytować pliku schematu XML** w widoku startowego.  
  
3.  Skopiuj schematu XML przykładowego kodu z [próbki schematu XML: schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md) i wklej go w celu zastąpienia kodu, który został dodany do nowego pliku XSD domyślnie.  
  
4.  Wybierz `purchaseOrder` elementu w Eksploratorze schematu, klikając prawym przyciskiem myszy `purchaseOrder` elementu w edytorze XML i wybierając **Pokaż w Eksploratorze XML**.  
  
5.  Kliknij prawym przyciskiem myszy `purchaseOrder` w Eksploratorze XML i wybierz **Pokaż w widoku modelu zawartości**.  
  
     Wyświetla widok modelu zawartości `purchaseOrder` elementu na jego powierzchnię.  
  
6.  Rozwiń węzeł `shipTo`, `billTo`, i `items` węzłów przez dwukrotne kliknięcie każdego węzła lub klikając Podwójna strzałka w prawo każdego węzła.  
  
     Węzły `purchaseOrder` element teraz zostaną rozwinięte, aby zobaczyć model zawartości elementu.  
  
7.  Kliknij w dowolnym węźle `purchaseOrder` elementu i znajduje się w pasku stron nadrzędnych, na którym w zestawie schematów wybrany węzeł znajduje się w temacie.  
  
8.  Kliknij przycisk **Pokaż dokumentacji** przycisku w pasku narzędzi XSD, aby przełączyć dokumentacja zawiera. Można również kliknąć prawym przyciskiem myszy powierzchnię projektu, aby przełączyć się z dokumentacją.  
  
9. Kliknij Rick `purchaseOrder` a następnie wybierz węzeł **Generowanie XML próbki** można znaleźć w dokumencie wystąpienia XML.