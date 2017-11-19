---
title: "Krok 11: Uruchom Program i próbowanie innych funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: "12"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 0f1146b590e66c5f8c08dd58c858b2d50326a2ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11: Uruchom Program i próbowanie innych funkcji
Program jest gotowy i gotowa do uruchomienia. Możesz uruchomić program i ustawić kolor tła w elemencie PictureBox. Aby dowiedzieć się więcej, spróbuj zwiększyć program zmiana koloru formularza, dostosowywanie przycisków i pola wyboru i zmiana właściwości formularza.  
  
 Aby pobrać ukończoną wersję przykładu, zobacz [przykładowy samouczek pełny obraz podglądu](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersję wideo tego tematu, zobacz [samouczek 1: Tworzenie podglądu obrazów w języku Visual Basic - 5 wideo](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Tworzenie podglądu obrazów w C# — wideo 5](http://go.microsoft.com/fwlink/?LinkId=205206). Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Aby uruchomić program i kolor tła  
  
1.  Wybierz F5 lub na pasku menu **debugowania**, **Rozpocznij debugowanie**.  
  
2.  Przed otwarciem obrazu wybierz **kolor tła** przycisku. **Kolor** zostanie otwarte okno dialogowe.  
  
     ![Okno dialogowe kolorów](../ide/media/express_colordialog.png "Express_ColorDialog")  
Okno dialogowe kolorów  
  
3.  Wybierz kolor, aby ustawić kolor tła PictureBox. Należy dokładnie przejrzeć `backgroundButton_Click()` metodę, aby zrozumieć, jak to działa.  
  
    > [!NOTE]
    >  Można załadować obrazu z Internetu przez wklejenie jej adres URL do **Otwórz plik** okno dialogowe. Spróbuj odnaleźć obrazu z przeźroczystym tłem, dlatego przedstawia kolor tła.  
  
4.  Wybierz **Wyczyść obraz** przycisk, aby upewnić się, usuwa ją. Następnie, zamknij program, wybierając **Zamknij** przycisku.  
  
### <a name="to-try-other-features"></a>Aby wypróbować inne funkcje  
  
-   Zmiana koloru formularz i przyciski, za pomocą **BackColor** właściwości.  
  
-   Dostosowywanie przycisków i pola wyboru przy użyciu **czcionki** i **ForeColor** właściwości.  
  
-   Zmień formularza **FormBorderStyle** i **ControlBox** właściwości.  
  
-   Użyj formularza **AcceptButton** i **CancelButton** właściwości, gdy użytkownik wybierze klawisz ENTER lub ESC automatycznie wybrano tego przycisków. Ten program był otwarty **Otwieranie pliku** okno dialogowe, gdy użytkownik wybierze wprowadź i zamknąć okno, gdy użytkownik wybierze ESC.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby dowiedzieć się więcej na temat programowania w programie Visual Studio, zobacz [koncepcje programowania](http://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
-   Aby dowiedzieć się więcej na temat języka Visual Basic, zobacz [opracowywanie aplikacji za pomocą Visual Basic](/dotnet/visual-basic/developing-apps/index).  
  
-   Aby dowiedzieć się więcej na temat języka Visual C#, zobacz [wprowadzenie do języka C# i .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).  
  
-   Aby przejść do następnego samouczek, zobacz [samouczek 2: tworzenie upłynął matematyczne quizu](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [kroku 10: pisanie kodu dla dodatkowych przycisków i pola wyboru](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).