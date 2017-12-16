---
title: 'Porady: Implementowanie interfejsu (Projektant klas) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 469e7876900c61589afac089b848bd712703b1e6
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="how-to-implement-an-interface-class-designer"></a>Porady: implementowanie interfejsu (Projektant klas)
W Projektancie klas można zaimplementować interfejsu na diagramie klas, łącząc go z klasy, która udostępnia kod dla metody interfejsu. Projektant klas generuje implementacji interfejsu i relacji między interfejs i klasa będzie wyświetlany jako relację dziedziczenia. Można zaimplementować interfejs, za pomocą rysowania linii dziedziczenia między interfejs i klasy lub przeciągając je z widoku klasy interfejsu.  
  
> [!TIP]
>  Można utworzyć ten sam sposób utworzyć innych typów interfejsów. Jeśli interfejs istnieje, ale nie są wyświetlane na diagramie klas, następnie najpierw go wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md) i [porady: wyświetlanie istniejących typów](how-to-view-existing-types.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs za pomocą rysowania linii dziedziczenia  
  
1.  Na diagramie klas wyświetlić interfejs i klasy, która będzie implementowany interfejs.  
  
2.  Rysowanie linii dziedziczenia z klasy i interfejsu.  
  
     Jest wyświetlany lizak dołączonego do klasy, a etykieta o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje klas zastępczych dla wszystkich członków interfejsu.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Tworzenie dziedziczenia pomiędzy typami](how-to-create-inheritance-between-types.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejsu z okno widoku klas  
  
1.  Na diagramie klas wyświetlanie klasy, która ma zostać zaimplementowany interfejs.  
  
2.  Otwórz widok klas i Znajdź interfejsu.  
  
    > [!TIP]
    >  Jeśli widoku klasy nie jest otwarte, otwórz widok klas z **widoku** menu. Aby uzyskać więcej informacji na temat klasy widoku, zobacz [wyświetlanie klas i członków ich](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Przeciągnij węzeł interfejsu klasy kształt na diagramie.  
  
     Jest wyświetlany lizak dołączonego do klasy, a etykieta o nazwie interfejsu identyfikuje relacji dziedziczenia. Visual Studio generuje klas zastępczych dla wszystkich członków interfejsu; w tym momencie zaimplementowano interfejs.  
  
## <a name="see-also"></a>Zobacz także
[Porady: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md)   
[Porady: wyświetlanie istniejących typów](how-to-view-existing-types.md)   
[Porady: Tworzenie dziedziczenia pomiędzy typami](how-to-create-inheritance-between-types.md)   
[Refaktoryzacja klas i typów](refactoring-classes-and-types.md)