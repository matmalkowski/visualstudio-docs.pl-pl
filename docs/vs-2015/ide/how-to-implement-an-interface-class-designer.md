---
title: 'Porady: Implementowanie interfejsu (Projektant klas) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3626d35867902f96b7f3d48d0b7528fa16fc7a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681192"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Porady: implementowanie interfejsu (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Implementowanie interfejsu (Projektant klas)](https://docs.microsoft.com/visualstudio/ide/how-to-implement-an-interface-class-designer).  
  
W Projektancie klas można zaimplementować interfejsu na diagramie klas, łącząc je do klasy, która zawiera kod dla metody interfejsu. Projektant klas generuje implementację interfejsu i wyświetla relacji między interfejsem i klasy jako relacji dziedziczenia. Można zaimplementować interfejs, za pomocą rysowania linii dziedziczenia między interfejsem i klasy lub przeciągnąć interfejs z widoku klasy.  
  
> [!TIP]
>  Można utworzyć taki sam sposób utworzyć inne typy interfejsów. Jeśli interfejs istnieje, ale nie jest wyświetlane na diagramie klasy, następnie najpierw wyświetlamy go. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie typów za pomocą projektanta klas](../ide/how-to-create-types-by-using-class-designer.md) i [porady: wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Aby zaimplementować interfejs, za pomocą rysowania linię dziedziczenia  
  
1.  Na diagramie klas wyświetlić interfejs i klasa, która będzie implementować interfejs.  
  
2.  Rysuj linię dziedziczenia z klasy i interfejsu.  
  
     Lizak pojawia się dołączony do klasy i etykietę o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje namiastki dla wszystkich członków interfejsu.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>Aby zaimplementować interfejs w oknie widoku klas  
  
1.  Na diagramie klasy można wyświetlić klasę, która ma zostać zaimplementowany interfejs.  
  
2.  Otwórz widok klas i wyszukaj interfejs.  
  
    > [!TIP]
    >  Jeśli widok klas nie jest otwarty, otwórz widok klas z **widoku** menu. Aby uzyskać więcej informacji dotyczących widoku klas, zobacz [Viewing Classes and Their Members](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Przeciągnij węzeł interfejsu klasa kształt na diagramie.  
  
     Lizak pojawia się dołączony do klasy i etykietę o nazwie interfejsu identyfikuje relacji dziedziczenia. Program Visual Studio generuje namiastki dla wszystkich członków interfejsu; w tym momencie interfejs jest implementowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie typów za pomocą projektanta klas](../ide/how-to-create-types-by-using-class-designer.md)   
 [Porady: wyświetlanie istniejących typów (Projektant klas)](../ide/how-to-view-existing-types-class-designer.md)   
 [Porady: Tworzenie dziedziczenia między typami (Projektant klas)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refaktoryzacja klas i typów (Projektant klas)](../ide/refactoring-classes-and-types-class-designer.md)



