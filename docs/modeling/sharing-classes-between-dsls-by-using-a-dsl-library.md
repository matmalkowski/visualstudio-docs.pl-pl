---
title: "Udostępnianie klas między DSLs przy użyciu biblioteki DSL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: "7"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: ed225f315c92cf9276eb97fcb78e1730250ecd4c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Udostępnianie klas między językami DSL za pomocą biblioteki DSL
W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania zestawu SDK, można utworzyć definicji DSL niekompletne, który można zaimportować do innej DSL. Dzięki temu można współczynnika typowych części podobnych modeli.  
  
## <a name="creating-and-using-dsl-libraries"></a>Tworzenie i używanie biblioteki DSL  
  
#### <a name="to-create-a-dsl-library"></a>Aby utworzyć bibliotekę DSL  
  
1.  Utwórz nowy projekt DSL, a następnie wybierz szablon rozwiązania DSL biblioteki.  
  
     Jeden projekt DSL zostanie utworzony pusty model.  
  
2.  Można dodać klasy, relacje, kształtów i tak dalej.  
  
     Elementy w bibliotece nie trzeba tworzyć jedno drzewo osadzania.  
  
     Aby zdefiniować relację, która służy importerów, Utwórz dwie klasy domeny i utworzyć relacji między nimi.  
  
     Rozważ ustawienie **modyfikator dziedziczenia** klas domeny do `Abstract`.  
  
3.  Możesz dodawać elementy zdefiniowane w Eksploratorze DSL, takich jak połączenia konstruktorów.  
  
4.  Możesz dodać dostosowania, które wymagają dodatkowych kodu, na przykład ograniczenia sprawdzania poprawności.  
  
5.  Kliknij przycisk **Przekształć wszystkie szablony**.  
  
6.  Skompiluj projekt.  
  
7.  Podczas dystrybucji DSL dla użytkowników w sieci, należy podać zarówno w skompilowanym zestawie (dynamicznie DLL), jak i plik `DslDefinition.dsl`. Skompilowanego zestawu można znaleźć w folderze w`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Aby zaimportować bibliotekę DSL  
  
1.  W innej definicji DSL w **DSL Explorer**, kliknij prawym przyciskiem myszy klasy głównym DSL, a następnie kliknij przycisk **Dodaj nowy DslLibrary Import**.  
  
2.  W oknie właściwości ustaw **ścieżka pliku** biblioteki. Można użyć względny lub ścieżką bezwzględną.  
  
     Biblioteka importowanych jest widoczny w Eksploratorze DSL, w trybie tylko do odczytu.  
  
3.  Importowany klasy można użyć jako klasy podstawowe. Utwórz klasę domeny w importującym DSL, i w oknie właściwości ustaw **klasa podstawowa** do importowanych klasy.  
  
4.  Kliknij przycisk Przekształć wszystkie szablony.  
  
5.  Dodaj do projektu DSL odwołanie do zestawu, który został utworzony przez projektu biblioteki DSL (dynamicznie DLL).  
  
6.  Skompiluj rozwiązanie.  
  
 Biblioteka DSL można importować innych bibliotek. Podczas importowania biblioteki jego procesów importu są automatycznie wyświetlane w Eksploratorze DSL.  
  
## <a name="see-also"></a>Zobacz też  
 [Sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
