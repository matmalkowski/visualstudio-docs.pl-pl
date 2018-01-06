---
title: "Wyodrębnij interface — refaktoryzacji (Visual Basic) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: db857fb1-3e22-46e2-b15a-56ef9f329235
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 08bbae629dbd0e1098eca67107926d290ffe7fb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extract-an-interface-in-visual-basic"></a>Wyodrębnij interfejs w języku Visual Basic
**Co:** umożliwia tworzenie interfejs przy użyciu istniejących elementów członkowskich z klasy, struktury lub interfejsu.

**Kiedy:** ma kilka klasy, struktury lub interfejsy z metod, które można podjąć typowe i używane przez inne klasy, struktury lub interfejsów.

**Dlaczego:** interfejsy są doskonałe konstrukcje zorientowane obiektowo projektów.  Wyobraź sobie o klasy dla różnych zwierząt (Dog, Cat, ptak), które mogą mieć metody wspólne, takie jak Eat, napoju, uśpienia.  Przy użyciu interfejsu, takich jak IAnimal umożliwia Dog Cat i ptak mają wspólny "podpis" dla tych metod.  

**Jak:**

1. Zaznacz nazwę klasy, które można wykonać akcji na lub po prostu umieść kursor tekstu gdzieś w nazwie klasy.

   ![Wyróżniony kod](media/extractinterface_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + I**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **wyodrębniania interfejsu** z menu podręcznego okna podglądu.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > wyodrębniania interfejsu**.
     * Kliknij prawym przyciskiem myszy nazwę klasy, wybierz opcję **szybkie akcje i Refaktoryzacje** menu i wybierz **wyodrębniania interfejsu** z menu podręcznego okna podglądu.

1. W **wyodrębniania interfejsu** okno dialogowe, które pojawia się, wprowadź informacje zadawane: ![Wyodrębnij Interface](media/extractinterface_dialog.png)
   | Pole | Opis |
   | --- | --- |
   | **Nowa nazwa interfejsu** | Nazwa interfejsu, który ma zostać utworzony. To domyślnie zostanie ustawiona I*ClassName*, gdzie *ClassName* jest nazwa klasy wybranej powyżej. |
   | **Nowa nazwa pliku** | Nazwa pliku, który zostanie wygenerowany i który będzie zawierać interfejsu. Zgodnie z nazwą interfejsu, to domyślnie zostanie ustawiona I*ClassName*, gdzie *ClassName* jest nazwa klasy wybranej powyżej. |
   | **Wybierz publiczne elementy członkowskie, aby utworzyć interfejs** | Elementy do wyodrębnienia w interfejsie.  Można wybrać dowolną liczbę, zgodnie z wymaganiami. |

1. Kliknij przycisk **OK**.

   Interfejs zostanie utworzony bezpośrednio w pliku określona nazwa.  Ponadto wybranej klasy będzie teraz implementuje ten interfejs.

   ![Wynikowa klasy](media/extractinterface_class.png)
   ![wynikowy — interfejs](media/extractinterface_interface.png)

## <a name="see-also"></a>Zobacz też
[Refaktoryzacji (Visual Basic)](../refactoring-vb.md)