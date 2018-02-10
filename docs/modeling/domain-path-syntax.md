---
title: "Składnia ścieżki domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: fb2b1dfa13bf00c29452798253198b2ad0e72e97
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="domain-path-syntax"></a>Składnia ścieżki domeny
Definicje DSL używać składni języka XPath można znaleźć określone elementy w modelu.  
  
 Zwykle nie trzeba pracować bezpośrednio przy użyciu tej składni. Gdzie jest dostępny w oknie właściwości, lub szczegóły DSL można kliknij strzałkę w dół i za pomocą edytora ścieżki. Jednak ścieżka pojawia się w tym formularzu w polu, po zastosowaniu edytora.  
  
 Ścieżka domeny ma następującą postać:  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![Relacja odwołania CommentReferencesSubjects](../modeling/media/dsl_reference.png "dsl_reference")  
  
 Składnia jest przesyłany drzewa modelu. Na przykład relacji domeny **CommentReferencesSubjects** na ilustracji powyżej ma **tematy** roli. Segment ścieżki **/! Subjectt** Określa, że ścieżka kończy się na elementy dostępne za pośrednictwem **tematy** roli.  
  
 Każdy z segmentów zaczyna się od nazwy relacji domeny. W przypadku przechodzenia z elementu do relacji, segment ścieżki jest wyświetlany jako *Relationship.PropertyName*. W przypadku przeskoków z łączem do elementu, segment ścieżki jest wyświetlany jako *relacji /! RoleName*.  
  
 Ukośniki oddzielne składnia ścieżki. Każdy z segmentów ścieżki jest albo przeskoku z elementu link (wystąpienia relacji) lub łącze do elementu. Segmenty ścieżki często są wyświetlane w parach. Jeden segment ścieżki reprezentuje przeskoku w elemencie łącza, a następny segment reprezentuje przeskoku z linku do elementu na drugim końcu. (Łącze może być również źródłowa lub docelowa relacji, sam).  
  
 Nazwa, której użyjesz dla przeskoku element do łącza jest wartością roli `Property Name`. Nazwa, której użyjesz dla elementu łącza przeskoku jest nazwa roli docelowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)