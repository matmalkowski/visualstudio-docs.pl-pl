---
title: 'Instrukcje: badanie modelu zawartości węzłów przy użyciu widoku modelu zawartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25e47eed752a78caebcbae66a527cc847ac7d8f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628140"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Instrukcje: badanie modelu zawartości węzłów przy użyciu widoku modelu zawartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: zbadanie zawartości modelu z węzłów przy użyciu widoku modelu zawartości](https://docs.microsoft.com/visualstudio/xml-tools/how-to-examine-the-content-model-of-nodes-using-the-content-model-view).  
  
  
W tym temacie opisano sposób zapoznaj się z węzłów za pomocą [widoku modelu zawartości](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości  
  
1.  Utwórz nowy plik schematu XML.  
  
2.  Kliknij przycisk **Użyj edytora XML możesz wyświetlać i edytować podstawowego pliku schematu XML** w widoku startowego.  
  
3.  Skopiuj przykładowy kod XML schematu z [próbki schematu XML: schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md) i wklej go w celu zastąpienia kodu, który został dodany do nowego pliku XSD domyślnie.  
  
4.  Wybierz `purchaseOrder` element w Eksploratorze schematu, klikając prawym przyciskiem myszy `purchaseOrder` element w edytorze XML i wybierając polecenie **Pokaż w Eksploratorze XML**.  
  
5.  Kliknij prawym przyciskiem myszy `purchaseOrder` w Eksploratorze XML, a następnie wybierz pozycję **Pokaż w widoku modelu zawartości**.  
  
     Wyświetla widok modelu zawartości `purchaseOrder` elementu po jego powierzchni projektowej.  
  
6.  Rozwiń `shipTo`, `billTo`, i `items` węzłów przez dwukrotne kliknięcie każdego węzła lub klikając podwójną strzałkę z prawej strony każdego węzła.  
  
     Węzły `purchaseOrder` element teraz zostaną rozwinięte i można zobaczyć model zawartości elementu.  
  
7.  Kliknij w dowolnym węźle `purchaseOrder` elementu i spójrz na pasku nawigacji, aby zobaczyć, gdzie w zestawie schematów wybrany węzeł znajduje się.  
  
8.  Kliknij przycisk **Pokaż dokumentacji** przycisk na pasku narzędzi XSD, aby przełączyć zawiera. Możesz również prawym przyciskiem myszy powierzchnię projektu, aby przełączyć się z dokumentacją.  
  
9. Kliknij przycisk Rick `purchaseOrder` a następnie wybierz węzeł **Generowanie XML przykładowe** można znaleźć w dokumencie wystąpienia XML.



