---
title: "Wybieranie szablonów rozwiązania języka specyficznego dla domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
Tworzenie rozwiązań języka specyficznego dla domeny, wybierz jeden z szablonów rozwiązania, które są dostępne w Kreatorze projektanta języka specyficznego dla domeny. Wybierając szablon najlepiej odpowiadający język, w którym chcesz utworzyć, można zminimalizować zmiany, które należy do początkowej rozwiązania.  
  
 Następujące szablony rozwiązania są dostępne w Kreatorze projektanta języka specyficznego dla domeny.  
  
|Szablon|Funkcje|Opis|  
|--------------|--------------|-----------------|  
|Diagramy klas|-Przedział kształtów<br />— Dziedziczenie klasa<br />-Relacji dziedziczenia<br />-Kształt dziedziczenia<br />— Właściwości relacji|Ten szablon rozwiązania należy użyć, jeśli języka specyficznego dla domeny zawiera jednostki i relacje, które mają właściwości. Ten szablon umożliwia tworzenie diagramów klas UML podobny języka specyficznego dla domeny. Główne jednostki są klasy i interfejsy, wraz z relacji skojarzenia, uogólnianie i implementacji. Klasy lub interfejsu jest wyświetlany jako okno, który zawiera listę atrybutów.|  
|Diagramy składników|-Porty|Jeśli języka specyficznego dla domeny zawiera składniki, to znaczy składnikami systemu oprogramowania, należy użyć tego szablonu rozwiązania. Ten szablon tworzy podobny diagramy składników UML języka specyficznego dla domeny. Główne jednostki są składniki i portów, które są wyświetlane jako małe kształty na zewnątrz składników.|  
|Diagramy przepływu zadań|-Obrazu i geometrii kształtów<br />-   *Ścieżek*|Użyj tego szablonu rozwiązanie, jeśli języka specyficznego dla domeny zawiera przepływy pracy, Stany lub sekwencji. Ten szablon tworzy podobny diagramy aktywności UML języka specyficznego dla domeny. Obiekt główny jest działanie i relacji głównego jest przejścia między działaniami. Szablon zawiera kilka innych elementów, takich jak stan początkowy stan końcowy i pasek synchronizacji.|  
|Minimalny języka|-Jednej klasy i kształtu<br />-Jednej relacji i łącznika|Jeśli języka specyficznego dla domeny wygląda inaczej innych szablonów, należy użyć tego szablonu rozwiązania. Ten szablon tworzy języka specyficznego dla domeny, którego dwóch klas i jednej relacji, które są przedstawiane w **przybornika** jako **pole** i **wiersza**. Klasa, jak i relacji mają przykład właściwość ciągu.|  
|Minimalny projektanta formularza systemu Windows|-Małe modelu.<br />— Windows formularz, który wyświetla modelu.|Jeśli chcesz utworzyć aplikację, w którym DSL jest powiązany z formularza systemu Windows, a nie graficznego projektanta, należy użyć tego szablonu.<br /><br /> Formularz, który działa jako interfejs użytkownika dla języka znajduje się w folderze Dsl\UI.<br /><br /> Przed otwarciem projektanta formularza należy skompilować projekt.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Projektant WPF minimalnego|-Małe modelu<br />— Windows Presentation Foundation interfejsu użytkownika, który wyświetla modelu|Jeśli chcesz utworzyć aplikację, w którym DSL jest powiązany z interfejsem użytkownika WPF, zamiast graficznego projektanta, należy użyć tego szablonu.<br /><br /> Projektant interfejsu użytkownika znajduje się w folderze Dsl\UI.<br /><br /> Przed otwarciem projektanta interfejsu użytkownika należy skompilować projekt.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Biblioteka DSL|-Minimalnego biblioteki|Jeśli chcesz utworzyć częściową definicją DSL, który można zaimportować do innych definicje DSL, należy użyć tego szablonu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie narzędzia języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
