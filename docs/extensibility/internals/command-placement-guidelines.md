---
title: Polecenie wytyczne umieszczania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e74bda24459bedeef007b451c7fabe3922e7ab37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="command-placement-guidelines"></a>Wskazówki dotyczące umieszczania polecenia
Najlepsze rozwiązania dotyczące rozmieszczania poleceń w Visual Studio zintegrowane środowisko programistyczne (IDE) różni się zależnie od rozmiaru zestawu poleceń. Polecenia są zdefiniowane i pozycjonować względem informacji w plikach vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Najlepsze rozwiązania dotyczące wszystkie zestawy poleceń  
 Dla każdego zestawu poleceń zgodna z tymi wytycznymi:  
  
-   Przygotuj wcześniej wykres strukturę polecenia. Zidentyfikuj poleceń, pola kombi, grupy poleceń i menu skrótów, które będą używane w więcej niż jednej lokalizacji.  
  
-   Polecenia, które pojawiają się w tej samej grupy musi być powiązana.  
  
-   Grupy, które zawierają tylko jedno polecenie są dozwolone.  
  
-   Pakietów nie należy dodawać wielu poleceń do istniejącego menu programu Visual Studio. Zamiast tego należy ich tworzyć menu i podmenu do obsługi nowych poleceń.  
  
-   Po umieszczeniu polecenia w istniejącego menu, nazwa polecenia, aby jego celem jest wyczyszczone i nie należy mylić z istniejących poleceń.  
  
## <a name="best-practices-for-small-command-sets"></a>Najlepsze rozwiązania w zakresie polecenia małych zestawów  
 Jeśli tworzysz pakiet VSPackage, który ma kilka poleceń również zgodna z tymi wytycznymi:  
  
-   Jeśli to możliwe, użyj [elementu nadrzędnego](../../extensibility/parent-element.md) polecenia, pole kombi, grupy lub menu podrzędne go umieścić w odpowiedniej grupie.  
  
-   Przypisz te grupy do menu wyświetlane przez pakiet VSPackage.  
  
-   Element nadrzędny polecenia lub menu podrzędne muszą być [elementu grupy](../../extensibility/group-element.md). Przypisz do grupy poleceń i menu podrzędne, a następnie przypisz grupy do menu nadrzędnego.  
  
-   Polecenie można umieścić w dodatkowych grup, dodając [elementu CommandPlacements](../../extensibility/commandplacements-element.md) sekcji po definicji polecenia, a następnie dodanie do `CommandPlacements Element` [CommandPlacement elementu](../../extensibility/commandplacement-element.md) dla każdego dodatkowe grupy.  
  
## <a name="best-practices-for-large-command-sets"></a>Najlepsze rozwiązania w zakresie polecenia dużych zestawów  
 Jeśli VSPackage będzie wiele poleceń, które będą widoczne w wielu sytuacjach, również zgodna z tymi wytycznymi:  
  
-   Upewnij się, menu, grup i poleceń własnym elementy nadrzędne. Oznacza to, że nie należy przypisywać `Parent Element` w definicji elementu.  
  
-   Użyj `CommandPlacement Element` wpisów w `CommandPlacements Element` sekcji mają zostać umieszczone w ich grupy nadrzędnej menu i menu, grup i poleceń.  
  
-   W `CommandPlacements` sekcji wpisów, które wypełnienia danego menu lub grupa powinna być sąsiadujących ze sobą. To pomaga zwiększyć czytelność, a sprawia, że `Priority` ułatwia ustalenie klasyfikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)