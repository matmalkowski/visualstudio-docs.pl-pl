---
title: "Karta węzła System.Activities wybierz elementy przybornika — okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ba4078a903c1e30b968928e13c8d160c898bbf0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Karta węzła System.Activities wybierz elementy przybornika — okno dialogowe
Ta karta **wybierz elementy przybornika** okno dialogowe zostanie wyświetlona lista [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] działań, szablony i elementy dostępne dla Ciebie. Do wyświetlania tej listy, wybierz **wybierz elementy przybornika** z **narzędzia** menu lub klikając prawym przyciskiem myszy **przybornika** i wybierając **wybierz elementy**do wyświetlenia **wybierz elementy przybornika** okno dialogowe, a następnie wybierz jego **elementu System.Activities** kartę. Fabrycznej lista zawiera działania przepływu pracy z zestawów węzła System.Activities, System.ServiceModel.Activities i System.Activities.Core.Presentation; jednak tylko dostarczane przez system działania wyświetlane i działań dodane za pośrednictwem innych zestawów wyświetlane w **przybornika** są domyślnie wybrane. Ostatnio dodane działania są automatycznie sprawdzane i są wyświetlane w **przybornika** po kliknięciu **OK** w oknie dialogowym. Ponadto te elementy są wyświetlane w **przybornika** pod nową kategorię, która odpowiada przestrzeni nazw, w którym znajduje się działanie / / szablon elementu.  
  
> [!WARNING]
>  Jeśli próbujesz dodać zestawu, który nie zawiera żadnych działań przepływu pracy, zostanie wyświetlone okno dialogowe błędu, wyjaśniający, że zestaw nie zawiera żadnych działań.  
  
 To okno dialogowe jest niezależny od projektu i dlatego **elementu System.Activities** kartę nadal wyświetlane w autonomiczny kod XAML lub typ projektu bez przepływu pracy.  
  
 Filtrowanie odbywa się na poszczególnych kartach. Oznacza to, nie można dodać działania przepływu pracy za pośrednictwem **składnika .NET** kartę. Muszą być dodane za pośrednictwem **elementu System.Activities** karcie samej siebie.  
  
 Można usunąć zaznaczenie wszystkie elementy, które chcesz wyświetlić w **przybornika** z tego okna dialogowego kartę lub alternatywnie można to zrobić za pomocą **usunąć** menu kontekstowego w **przybornika** i usuwania odwołania do zestawu nie powoduje usunięcia elementu z **przybornika**.  
  
 Utworzenie wystąpienia działania przez przeciąganie i upuszczanie go w Projektancie dodaje zestaw zawierający element do listy zestawów występujących w odwołaniach automatycznie. Także jeśli działania odwołuje się do zestawu C, nie dodaje C do listy przywoływanego zestawu. Zestaw C musi być w pamięci podręcznej GAC lub w tym samym katalogu co działania B. W przypadku autonomicznego zestawu musi być w pamięci podręcznej GAC lub sondowania ścieżek VS. Następnie możesz przeciągać i upuszczać działania na powierzchni projektanta przepływów pracy.  
  
 **Przybornik** ustawienia są domyślnie zapisywane jako opcji użytkownika, więc następnym razem po otwarciu **przybornika**, wyświetla listę niestandardowych działań przepływu pracy. Jeden ubocznym tego jest to, że po dodaniu elementów do określonej domeny **przybornika** za pośrednictwem **wybierz elementy przybornika** okno dialogowe, nadal możesz znaleźć te elementy podczas pracy Aplikacja Konsolowa przepływu pracy oraz. Jeśli nie chcesz je wyświetlić, usuń je za pomocą menu kontekstowego lub usuń zaznaczenie pola wyboru je za pomocą **wybierz elementy przybornika** okno dialogowe, jak podano wcześniej.  
  
 Kolumny w tym oknie dialogowym zawiera następujące informacje:  
  
 Nazwa  
 Wyświetla nazwy działania przepływu pracy, w obecnie zarejestrowane na komputerze lokalnym.  
  
 Przestrzeń nazw  
 Wyświetla hierarchię przestrzeni nazw Biblioteka klas programu .NET Framework, która definiuje strukturę działania.  
  
 Nazwa zestawu  
 Wyświetla nazwę i wersję zestawu .NET Framework, który zawiera działanie.  
  
 Katalog  
 Wyświetla lokalizację zestawu .NET Framework, który zawiera działania przepływu pracy. Domyślna lokalizacja dla wszystkich zestawów to Global Assembly Cache.  
  
 Aby posortować wymienione składniki, wybierz nagłówek dowolnej kolumny.