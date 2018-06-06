---
title: Składnia ścieżki domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 984b27b65b251a1e87c72962e488fd0d4036a4d0
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749547"
---
# <a name="domain-path-syntax"></a>Składnia ścieżki domeny
Definicje DSL używać składni języka XPath można znaleźć określone elementy w modelu.

 Zwykle nie trzeba pracować bezpośrednio przy użyciu tej składni. Gdzie jest dostępny w oknie właściwości, lub szczegóły DSL można kliknij strzałkę w dół i za pomocą edytora ścieżki. Jednak ścieżka pojawia się w tym formularzu w polu, po zastosowaniu edytora.

 Ścieżka domeny ma następującą postać:

 *RelationshipName.PropertyName/!Role*

 ![Odwołania obiektu CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 Składnia jest przesyłany drzewa modelu. Na przykład relacji domeny **CommentReferencesSubjects** na ilustracji powyżej ma **tematy** roli. Segment ścieżki **/! Subjectt** Określa, że ścieżka kończy się na elementy dostępne za pośrednictwem **tematy** roli.

 Każdy z segmentów zaczyna się od nazwy relacji domeny. W przypadku przechodzenia z elementu do relacji, segment ścieżki jest wyświetlany jako *Relationship.PropertyName*. W przypadku przeskoków z łączem do elementu, segment ścieżki jest wyświetlany jako *relacji /! RoleName*.

 Ukośniki oddzielne składnia ścieżki. Każdy z segmentów ścieżki jest albo przeskoku z elementu link (wystąpienia relacji) lub łącze do elementu. Segmenty ścieżki często są wyświetlane w parach. Jeden segment ścieżki reprezentuje przeskoku w elemencie łącza, a następny segment reprezentuje przeskoku z linku do elementu na drugim końcu. (Łącze może być również źródłowa lub docelowa relacji, sam).

 Nazwa, której użyjesz dla przeskoku element do łącza jest wartością roli `Property Name`. Nazwa, której użyjesz dla elementu łącza przeskoku jest nazwa roli docelowej.

## <a name="see-also"></a>Zobacz też

- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)