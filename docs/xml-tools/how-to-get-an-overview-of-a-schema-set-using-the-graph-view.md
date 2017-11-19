---
title: "Porady: Zapoznaj się z omówieniem zestawu schematu przy użyciu widoku wykresu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 88f2f9f565afef2cc3f8d3f6e9e9397fe5ce6955
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Porady: Zapoznaj się z omówieniem zestawu schematu przy użyciu widoku wykresu
W tym temacie opisano sposób użycia [widok wykresu](../xml-tools/graph-view.md) Aby wyświetlić widok ogólny węzłów w zestawie schematów i relacje między węzłami.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości  
  
1.  Utwórz nowy plik schematu XML, a następnie zapisz plik jako Relationships.xsd.  
  
2.  Kliknij przycisk **Użyj edytora XML możesz wyświetlać i edytować pliku schematu XML** łącza w widoku startowego.  
  
3.  Skopiuj schematu XML przykładowego kodu z [schematu XML próbki: relacje](../xml-tools/sample-xsd-file-relationships.md) i wklej go w celu zastąpienia kodu, który został dodany do nowego pliku XSD domyślnie.  
  
4.  Kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz **Widok projektanta**.  
  
5.  Wybierz widok wykresu z paska narzędzi XSD.  
  
6.  Wybierz **zestawu schematu** węzła w Eksploratora schematu XML i przeciągnij węzeł projektowania suface w widoku wykresu. Powinny pojawić się wszystkie węzły globalne i strzałki łączące węzły, które mają relacji.  
  
     ![Widok wykresu](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Kliknij w dowolnym węźle na powierzchni projektu i przyjrzyj się na pasku stron nadrzędnych, aby sprawdzić, gdzie znajduje się wybrany węzeł w zestawie schematów.  
  
8.  Rick kliknięciem na dowolnym węźle elementu na desing powierzchni i wybierz pozycję **Generowanie XML próbki** można znaleźć w dokumencie wystąpienia XML.