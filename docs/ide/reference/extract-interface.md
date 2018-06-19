---
title: Wyodrębnij interface Refaktoryzacja w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6afc2acab36be88b4eb554d1900e6b314e395bd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948174"
---
# <a name="extract-an-interface-refactoring"></a>Wyodrębnij refaktoryzacji — interfejs

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

**Co:** umożliwia tworzenie interfejs przy użyciu istniejących elementów członkowskich z klasy, struktury lub interfejsu.

**Kiedy:** ma kilka klasy, struktury lub interfejsy z metod, które można podjąć typowe i używane przez inne klasy, struktury lub interfejsów.

**Dlaczego:** interfejsy są doskonałe konstrukcje zorientowane obiektowo projektów. Wyobraź sobie o klasy dla różnych zwierząt (Dog, Cat, ptak), które mogą mieć metody wspólne, takie jak Eat, napoju, uśpienia. Przy użyciu interfejsu, takich jak IAnimal umożliwia Dog Cat i ptak mają wspólny "podpis" dla tych metod.

## <a name="how-to"></a>Porada

1. Zaznacz nazwę klasy, które można wykonać akcji na lub po prostu umieść kursor tekstu gdzieś w nazwie klasy.

   - C#:

    ![Wyróżniony kod - C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony kod - języka Visual Basic](media/extractinterface-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + I**. (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **wyodrębniania interfejsu** z menu podręcznego okna podglądu.
   - **Myszy**
     - Wybierz **Edytuj > Refaktoryzuj > wyodrębniania interfejsu**.
     - Kliknij prawym przyciskiem myszy nazwę klasy, wybierz opcję **szybkie akcje i Refaktoryzacje** menu i wybierz **wyodrębniania interfejsu** z menu podręcznego okna podglądu.

1. W **wyodrębniania interfejsu** okno dialogowe, które pojawia się, wprowadź informacje poproszony:

   ![Wyodrębnij interface](media/extractinterface-dialog-cs.png)

   | Pole | Opis |
   | --- | --- |
   | **Nowa nazwa interfejsu** | Nazwa interfejsu, który ma zostać utworzony. To domyślnie zostanie ustawiona I*ClassName*, gdzie *ClassName* jest nazwa klasy wybranej powyżej. |
   | **Nowa nazwa pliku** | Nazwa pliku, który zostanie wygenerowany i który będzie zawierać interfejsu. Zgodnie z nazwą interfejsu, to domyślnie zostanie ustawiona I*ClassName*, gdzie *ClassName* jest nazwa klasy wybranej powyżej. |
   | **Wybierz publiczne elementy członkowskie, aby utworzyć interfejs** | Elementy do wyodrębnienia w interfejsie. Można wybrać dowolną liczbę, zgodnie z wymaganiami. |

1. Wybierz **OK**.

   Gdy interfejs został utworzony w pliku określona nazwa. Ponadto wybranej klasy implementuje ten interfejs.

   - C#:

    ![Wynikowa klasy - C#](media/extractinterface-class-cs.png)
    ![wynikowy interfejs - C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

    ![Wynikowa klasy - Visual Basic](media/extractinterface-class-vb.png)
    ![wynikowy interfejs - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)