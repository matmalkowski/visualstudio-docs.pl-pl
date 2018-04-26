---
title: 'Porady: wyświetlanie istniejących typów (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fc5180d770575ae92c65b4124d928da5a518799
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-view-existing-types-class-designer"></a>Porady: wyświetlanie istniejących typów (Projektant klas)

Aby wyświetlić istniejącego typu i jej elementów członkowskich, należy dodać jego kształtu do diagramu klas.

Można zobaczyć typy lokalne i typy odwołania. Typ lokalny istnieje w aktualnie otwartym projekcie i jest do odczytu/zapisu. Typ odwołania istnieje w innym projekcie lub w zestawie odwołania i jest tylko do odczytu.

Projektowanie nowych typów w diagramach klas, zobacz [porady: Tworzenie typów za pomocą projektanta klas](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Aby wyświetlić typy w projekcie na diagramie klasy

1.  Z projektu w **Eksploratora rozwiązań**, otwórz istniejący plik diagramu (.cd) klasy. Lub jeśli nie istnieje żaden diagram klas, dodaj nowy diagram klas do projektu. Zobacz [porady: Dodawanie diagramów klasy do projektów](how-to-add-class-diagrams-to-projects.md).

2.  Z projektu w **Eksploratora rozwiązań**, przeciągnij pliku kodu źródłowego do diagramu klas.

    > [!WARNING]
    > Jeśli rozwiązanie zawiera projekt, który udostępnia kod wielu aplikacjom, można przeciągnąć plików lub kodu do diagramu klas tylko z tych źródeł:
    >
    > -   Projekt aplikacji, który zawiera diagramu
    > -   Udostępnionego projektu, które zostały zaimportowane na podstawie projektu aplikacji
    > -   Projekt odwołania
    > -   Zestaw

    Kształty przedstawiające typy zdefiniowane w pliku kodu źródłowego są wyświetlane na diagramie w miejscu, gdzie przeciągnąłeś plik.

Możesz również wyświetlić typów w projekcie, przeciągając je z węzła projektu w co najmniej jeden typ **widoku klasy** do diagramu klas.

> [!TIP]
> Jeśli **widoku klasy** nie jest otwarte, otwórz **widoku klasy** z **widoku** menu.

Aby wyświetlić typy w lokalizacji domyślnej na diagramie, wybierz jeden lub więcej typów w **widoku klasy**, kliknij prawym przyciskiem myszy wybranych typów i wybierz **widoku diagramu klas**.

> [!NOTE]
> Jeśli zamknięty diagram klas zawierający typ już istnieje w projekcie, diagram klas się otworzy, aby wyświetlić kształt typu. Jeśli jednak nie klasy diagram zawierający typ istnieje w projekcie, **Projektant klas** tworzy nowy diagram klas do projektu i otwarcie go, aby wyświetlić typu.

Przy pierwszym wyświetleniu typu na diagramie, jego kształt pojawia się domyślnie zwinięty. Można rozwinąć kształt, aby wyświetlić jego zawartość.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Aby wyświetlić zawartość projektu na diagramie klas

- W **Eksploratora rozwiązań** lub **widoku klasy**, kliknij prawym przyciskiem myszy projekt i wybierz **widoku**, a następnie wybierz **widoku diagramu klas**.

     Tworzony jest automatycznie wypełniony Diagram klas.

## <a name="see-also"></a>Zobacz także

- [Porady: wyświetlanie dziedziczenia pomiędzy typami](how-to-view-inheritance-between-types.md)
- [Porady: dostosowywanie diagramów klasy](how-to-customize-class-diagrams.md)
- [Wyświetlanie typów i relacji](viewing-types-and-relationships.md)