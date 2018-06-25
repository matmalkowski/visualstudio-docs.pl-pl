---
title: 'Projektant przepływu pracy — porady: Użyj projektanta importów'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d50267ca8899343d2b704aa28beabc07ed432936
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755865"
---
# <a name="how-to-use-the-imports-designer"></a>Porady: Użyj projektanta importów

Projektanta importów umożliwia wprowadzanie przestrzeni nazw dla typów, które będą używane w wyrażeniach utworzonych przez użytkownika. Podobnie jak **importuje** lub **przy użyciu** słów kluczowych w języku Visual Basic i C#, określenie obszarów nazw w projektanta importów umożliwiają wystarczy wprowadzić w wyrażeniu a nie w pełni kwalifikowaną nazwę typu Nazwa typu wersji.

Projektanta importów reaguje na zmiany w interfejsie użytkownika i zmian wprowadzonych po zapisaniu przepływ pracy. Po zapisaniu przepływu pracy przestrzeni nazw można automatycznie dodawane do projektanta importów. Należą do nich między innymi:

-   Przestrzenie nazw dla wszystkich typów, używany w deklaracji zmiennej i argument.

-   Przestrzenie nazw dla wszystkich typów używane w wyrażeniach.

-   Wszystkie inne obszary nazw wymagane dla serializacji przepływu pracy (na przykład przestrzenie nazw używane przez niestandardowe działania w przepływie pracy).

 Po zapisaniu przepływu pracy można zauważyć pewne przestrzeni nazw ręcznie usuwać są automatycznie ponownie dodać do projektanta importów z powodu logiki opisane w powyższej listy.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Aby dodać przestrzeni nazw na liście importowane przestrzenie nazw

1.  Otwórz aplikację usługi przepływu pracy WCF, aplikacja konsoli przepływu pracy lub działania projektu biblioteki w programie Visual Studio lub aplikacja rehosted przepływu pracy.

2.  Kliknij przycisk **importów** w dolnej części obszaru głównego. Projektanta importów będą wyświetlane.

3.  Wprowadź lub wybierz z listy rozwijanej formantu w górnej części projektanta importów przestrzeni nazw.

     Podczas wpisywania, zostanie wyświetlona lista prawidłowy przestrzenie nazw, które odpowiada wpisane znaki.

4.  Naciśnij klawisz **Enter** do dodania do listy przestrzeni nazw.

5.  Jeśli chcesz usunąć przestrzeń nazw z listy, wybierz obszar nazw, a następnie naciśnij klawisz **usunąć** klucza na klawiaturze. Należy pamiętać, że przestrzeń nazw można usunąć tylko jeśli przestrzeń nazw jest nieprawidłowy z jakiejkolwiek przyczyny, na przykład jeśli zestaw, który zawiera przestrzeń nazw jest już odwołuje się projekt.