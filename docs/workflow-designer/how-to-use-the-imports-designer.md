---
title: "Porady: Użyj projektanta importów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 3873e444f3d9c68b632d52ab98bee07bf14af679
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-imports-designer"></a>Porady: Użyj projektanta importów
Projektanta importów umożliwia wprowadzanie przestrzeni nazw dla typów, które będą używane w wyrażeniach utworzonych przez użytkownika. Podobnie jak **importuje** lub **przy użyciu** słów kluczowych w języku Visual Basic .NET i C#, określenie obszarów nazw w projektanta importów umożliwiają wystarczy wprowadzić w wyrażeniu a nie w pełni kwalifikowaną nazwę typu Nazwa typu wersji.  
  
 Projektanta importów reaguje na zmiany w interfejsie użytkownika i zmian wprowadzonych po zapisaniu przepływ pracy. Po zapisaniu przepływu pracy przestrzeni nazw można automatycznie dodawane do projektanta importów. Należą do nich między innymi:  
  
-   Przestrzenie nazw dla wszystkich typów, używany w deklaracji zmiennej i argument.  
  
-   Przestrzenie nazw dla wszystkich typów używane w wyrażeniach.  
  
-   Wszystkie inne obszary nazw wymagane dla serializacji przepływu pracy (na przykład przestrzenie nazw używane przez niestandardowe działania w przepływie pracy).  
  
 Po zapisaniu przepływu pracy można zauważyć pewne przestrzeni nazw ręcznie usuwać są automatycznie ponownie dodać do projektanta importów z powodu logiki opisane w powyższej listy.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Aby dodać przestrzeni nazw na liście importowane przestrzenie nazw  
  
1.  Otwórz aplikację usługi przepływu pracy WCF, aplikacja konsoli przepływu pracy lub działania projektu biblioteki w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] lub aplikacja rehosted przepływu pracy.  
  
2.  Kliknij przycisk **importów** w dolnej części obszaru głównego. Projektanta importów będą wyświetlane.  
  
3.  Wprowadź lub wybierz z listy rozwijanej formantu w górnej części projektanta importów przestrzeni nazw.  
  
     Podczas wpisywania, zostanie wyświetlona lista prawidłowy przestrzenie nazw, które odpowiada wpisane znaki.  
  
4.  Naciśnij klawisz **Enter** do dodania do listy przestrzeni nazw.  
  
5.  Jeśli chcesz usunąć przestrzeń nazw z listy, wybierz obszar nazw, a następnie naciśnij klawisz **usunąć** klucza na klawiaturze. Należy pamiętać, że przestrzeń nazw można usunąć tylko jeśli przestrzeń nazw jest nieprawidłowy z jakiejkolwiek przyczyny, na przykład jeśli zestaw, który zawiera przestrzeń nazw jest już odwołuje się projekt.