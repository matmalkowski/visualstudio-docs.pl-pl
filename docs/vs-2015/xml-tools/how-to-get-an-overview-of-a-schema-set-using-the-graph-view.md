---
title: 'Porady: Zapoznaj się z omówieniem zestawu schematu przy użyciu widoku wykresu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b7c3d1d9f351e496469e5b13552ec78e1548f5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42695584"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Porady: Zapoznaj się z omówieniem zestawu schematu przy użyciu widoku wykresu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Zapoznaj się z omówieniem schematu ustawiony przy użyciu widoku wykresu](https://docs.microsoft.com/visualstudio/xml-tools/how-to-get-an-overview-of-a-schema-set-using-the-graph-view).  
  
  
W tym temacie opisano sposób użycia [widoku wykresu](../xml-tools/graph-view.md) Aby wyświetlić widok wysokiego poziomu węzłów w zestawie schematów i relacje między węzłami.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Aby utworzyć nowy plik XSD i wyświetlić element główny w widoku modelu zawartości  
  
1.  Utwórz nowy plik schematu XML, a następnie zapisz plik jako Relationships.xsd.  
  
2.  Kliknij przycisk **Użyj edytora XML możesz wyświetlać i edytować podstawowego pliku schematu XML** link widoku startowego.  
  
3.  Skopiuj przykładowy kod XML schematu z [schematu XML przykładowych: relacje](../xml-tools/sample-xsd-file-relationships.md) i wklej go w celu zastąpienia kodu, który został dodany do nowego pliku XSD domyślnie.  
  
4.  Kliknij prawym przyciskiem myszy w edytorze XML, a następnie wybierz pozycję **Projektant widoków**.  
  
5.  Wybierz widok wykresu z paska narzędzi XSD.  
  
6.  Wybierz **schemat ustawiony** węzła w Eksplorator schematu XML i przeciągnij węzeł projektowania suface widoku wykresu. Powinien zostać wyświetlony wszystkie węzły globalnych i strzałki Łączenie węzłów, które mają relacje.  
  
     ![Widoku wykresu](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Kliknij dowolny węzeł na powierzchni projektowej i spójrz na pasku nawigacji, aby zobaczyć, gdzie wybrany węzeł znajduje się w zestawie schematów.  
  
8.  Rick kliknąć dowolny węzeł elementu na desing powierzchni i wybierz **Generowanie XML przykładowe** można znaleźć w dokumencie wystąpienia XML.



