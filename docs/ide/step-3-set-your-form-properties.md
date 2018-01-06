---
title: "Krok 3: Ustawienie właściwości formularza | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: "18"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e703372a3b59ceee439b234e02e4a2d5a3cb6275
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="step-3-set-your-form-properties"></a>Krok 3. Ustawienie właściwości formularza
Następnie użyj **właściwości** okno, aby zmienić wygląd formularza.  
  
 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersję wideo tego tematu, zobacz [samouczek 1: Tworzenie podglądu obrazów w języku Visual Basic - 1 wideo](http://go.microsoft.com/fwlink/?LinkId=205209) lub [samouczek 1: Tworzenie podglądu obrazów w C# - wideo 1](http://go.microsoft.com/fwlink/?LinkId=205199). Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-set-your-form-properties"></a>Aby ustawić właściwości formularza  
  
1.  Upewnij się, że patrzy Projektant formularzy systemu Windows. W programie Visual Studio zintegrowane środowisko programistyczne (IDE), wybierz opcję **pliku Form1.cs [projekt]** kartę (lub **Form1.vb [projekt]** kartę w języku Visual Basic).  
  
2.  Wybierz dowolne miejsce w formularzu **Form1** aby go wybrać. Przyjrzyj się **właściwości** okna, które powinny teraz pokazujący właściwości formularza. Formularze mają różne właściwości. Na przykład można ustawić pierwszego planu i tła, tekst tytułu, który pojawi się w górnej części formularza, rozmiar formularza i inne właściwości.  
  
    > [!NOTE]
    >  Jeśli **właściwości** nie zostanie wyświetlone okno, Zatrzymaj program, wybierając kwadrat **Zatrzymaj debugowanie** znajdującego się na pasku narzędzi lub Zamknij okna. Jeśli program został zatrzymany, a nadal nie widać **właściwości** okna, na pasku menu wybierz **widoku**, **okna właściwości**.  
  
3.  Po wybraniu formularza, Znajdź **tekst** właściwości w **właściwości** okna. W zależności od tego, jak lista jest sortowana konieczne może być przewiń w dół. Wybierz **tekst**, typ **obraz podglądu**, a następnie wybierz pozycję ENTER.  Formularz powinna mieć teraz tekst **obraz podglądu** na pasku tytułu i **właściwości** okna powinien wyglądać podobnie do poniższej ilustracji.  
  
     ![Okno właściwości](../ide/media/express_edittextproperty.png "Express_EditTextProperty")  
Okno właściwości  
  
    > [!NOTE]
    >  Właściwości może zostać określona przez według kategorii lub alfabetycznej widoku. Można przełączać się między tymi dwoma widokami za pomocą przycisków na **właściwości** okna. W tym samouczku łatwiej znaleźć właściwości za pośrednictwem widoku alfabetycznym.  
  
4.  Wróć do projektanta formularzy systemu Windows. Wybierz uchwyt przeciągania prawym dolnym formularza małych biały kwadrat w prawym dolnym formularza i wygląda następująco.  
  
     ![Przeciągnij uchwyt](../ide/media/express_bottomrt_drag.png "Express_BottomRT_Drag")  
Przeciągnij uchwyt  
  
     Przeciągnij uchwyt zmiany rozmiaru formularza, aby formularz był szersze i nieco większa.  
  
5.  Przyjrzyj się **właściwości** okna i zwróć uwagę, że **rozmiar** właściwość zostanie zmieniona. **Rozmiar** zawsze możesz zmienić rozmiar formularza zmiany właściwości. Spróbuj przeciąganie uchwyt formularza, aby zmienić rozmiar formularza, około 550 350 (nie muszą być dokładnie), które powinny działać dla tego projektu. Alternatywnie, można wprowadzić wartości bezpośrednio w **rozmiar** właściwości, a następnie wybierz klawisz ENTER.  
  
6.  Ponownie uruchom program. Należy pamiętać, że można użyć dowolnej z następujących metod do uruchomienia programu.  
  
    -   Wybierz **F5** klucza.  
  
    -   Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**.  
  
    -   Na pasku narzędzi wybierz **Rozpocznij debugowanie** przycisku, który wygląda następująco.  
  
         ![Rozpocznij debugowanie przycisku paska narzędzi](../ide/media/express_icondebug.png "Express_IconDebug")  
Rozpocznij debugowanie przycisku paska narzędzi  
  
     Podobnie jak przed IDE kompiluje i uruchamia program, a okno.  
  
7.  Przed przejściem do następnego kroku, należy zatrzymać programu, ponieważ IDE nie pozwoli zmienić programu, gdy jest uruchomiona. Należy pamiętać, że można użyć dowolnej z następujących metod można zatrzymać program.  
  
    -   Na pasku narzędzi wybierz **Zatrzymaj debugowanie** przycisku.  
  
    -   Na pasku menu wybierz **debugowania**, **Zatrzymaj debugowanie**.  
  
    -   Kliknij przycisk X w górnym rogu **Form1** okna.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 4: określa się Your formularza przy użyciu formantu TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Uruchom Program Your](../ide/step-2-run-your-program.md).