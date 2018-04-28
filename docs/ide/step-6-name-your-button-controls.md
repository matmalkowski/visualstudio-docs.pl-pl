---
title: 'Krok 6: Nazw formantom przycisków'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57fec877b968873cb4571fe060572ffb2e6aeba3
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="step-6-name-your-button-controls"></a>Krok 6: Nazw formantom przycisków
Istnieje tylko jeden <xref:System.Windows.Forms.PictureBox> w formularzu. Podczas dodawania go IDE automatycznie o nazwie go **pictureBox1**. Istnieje tylko jeden <xref:System.Windows.Forms.CheckBox>, który o nazwie **pole wyboru 1**. Najszybciej jak napisać kod i ten kod będzie odnosić się do pola wyboru i PictureBox. Ponieważ istnieje tylko jeden z tych kontrolek, będzie wiadomo, co oznacza to, gdy zostanie wyświetlony **pictureBox1** lub **pole wyboru 1** w kodzie.  

> [!NOTE]
>  W języku Visual Basic domyślne pierwszą literę dowolną nazwę formantu jest początkowej centralnych zasad dostępu, więc nazwy są **PictureBox1**, **pole wyboru 1**i tak dalej.  

 Istnieją cztery przyciski w formularzu i nazwane IDE **button1**, **button2**, **button3**, i **button4**. Tylko na podstawie ich bieżącej nazwy, nie wiadomo, przycisk **Zamknij** przycisk i która jest **Pokaż obraz** przycisku. Dlatego warto zapewniając większą przyjazność nazw formantom przycisków.  
  
 ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersję wideo tego tematu, zobacz [samouczek 1: Tworzenie podglądu obrazów w języku Visual Basic - 3 wideo](http://go.microsoft.com/fwlink/?LinkId=205213) lub [samouczek 1: Tworzenie podglądu obrazów w języku C# — Wideo 3](http://go.microsoft.com/fwlink/?LinkId=205202). Tych klipów wideo korzysta z wcześniejszej wersji programu Visual Studio, dlatego są niewielkie różnice w niektórych poleceń menu i inne elementy interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
## <a name="to-name-your-button-controls"></a>Do nazw formantom przycisków  
  
1.  W formularzu, należy wybrać **Zamknij** przycisku. (Jeśli nadal masz wszystkie przyciski wybrana, wybierz **Esc** klawisz, aby anulować wybór.) Przewiń w **właściwości** okna, aż zostanie wyświetlony **(nazwa)** właściwości. ( **(Nazwa)** właściwość jest u góry, gdy właściwości są alfabetycznym.) Zmień nazwę, aby **closeButton**, jak pokazano na poniższej ilustracji.  
  
     ![Okno właściwości o nazwie closeButton](../ide/media/express_setnameproperty.png "Express_SetNameProperty")  
**Właściwości** okna z **closeButton** nazwy  
  
    > [!NOTE]
    >  Jeśli spróbujesz się zmiana nazwy przycisk Tak, aby **closeButton**, ze spacją między Zamknij słów i przycisk IDE wyświetla komunikat o błędzie: "wartość właściwości jest nieprawidłowa." Spacji (i kilka innych znaków) nie są dozwolone w nazwach formantu.  

2.  Zmień nazwę trzy przyciski do **backgroundButton**, **clearButton**, i **Pokaż przycisk**. Sprawdź nazwy, wybierając z listy rozwijanej selektora kontroli w **właściwości** okna. Wyświetlane nazwy przycisk Nowy.  
  
3.  Kliknij dwukrotnie **Pokaż obraz** przycisk w formularzu. Alternatywnie, wybierz **Pokaż obraz** znajdującego się na formularzu, a następnie wybierz **Enter** klucza. Po wykonaniu czynności IDE spowoduje otwarcie dodatkowe karty w oknie głównym o nazwie **pliku Form1.cs** (**Form1.vb** Jeśli używasz programu Visual Basic). Ta karta przedstawia pliku kodu za formularz, jak pokazano na poniższej ilustracji.  
  
     ![Karta pliku Form1.CS z Visual C&#35; kod](../ide/media/express_showbuttoncode.png "Express_ShowButtonCode")  
**Pliku Form1.cs** karta z kodu Visual C#  
  
4.  Skoncentruj się na tej części kodu. (Wybierz **VB** karcie poniżej, jeśli używasz programu Visual Basic, aby wyświetlić wersję języka Visual Basic kodu.)  

     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]  

     Przeglądasz kod wywołuje `showButton_Click()`. IDE to formularza kodu dodane po otwarciu pliku kodu dla **Pokaż przycisk** przycisku. W czasie projektowania podczas otwierania pliku kodu dla formantu w formularzu generowania kodu dla formantu, jeśli jeszcze nie istnieje. Ten kod, znany jako *metody*, jest uruchamiany, gdy musisz uruchomić program i wybrać formant — w takim przypadku **Pokaż obraz** przycisku.  

    > [!NOTE]
    >  W tym samouczku został uproszczony kod Visual Basic, który jest automatycznie generowany przez usunięcie wszystkich w nawiasach `()`. Jeśli ten problem wystąpi, należy usunąć ten sam kod. Program będzie działać w obu przypadkach. W pozostałej części samouczków automatycznie wygenerowanego kodu jest uproszczone, jeśli to możliwe.  
  
5.  Wybierz **Projektant formularzy systemu Windows** karcie ponownie (**pliku Form1.cs [projekt]** języka Visual C#, **Form1.vb [projekt]** w języku Visual Basic), a następnie otwórz plik kodowy dla **Wyczyść obraz** przycisk, aby utworzyć metodę dla niego w kodzie formularza. Powtórz tę czynność dla pozostałych dwóch przycisków. Zawsze, IDE dodaje nową metodę do pliku kodu formularza.  
  
6.  Aby dodać jedna metoda, otwórz plik kodowy dla **wyboru** kontroli w **Projektant formularzy systemu Windows** Aby dodać IDE `checkBox1_CheckedChanged()` — metoda. Ta metoda jest wywoływana, gdy użytkownik zaznaczy lub wyczyszczenie pola wyboru.  
  
    > [!NOTE]
    >  Podczas pracy w programie, często przenoszenia między edytora kodu i **Projektant formularzy systemu Windows**. IDE ułatwia nawigowanie w projekcie. Użyj **Eksploratora rozwiązań** otworzyć **Projektant formularzy systemu Windows** przez dwukrotne kliknięcie *pliku Form1.cs* języka Visual C# lub *Form1.vb* w języku Visual Basic lub na pasku menu wybierz **widoku** > **projektanta**.  
  
     Oto nowy kod zostanie wyświetlony w edytorze kodu.  

     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]  

     Pięć metod, które zostały dodane są nazywane *procedury obsługi zdarzeń*, ponieważ program wywołuje je zawsze, gdy zachodzi zdarzenie (np. wybranie przycisku lub zaznaczenie pola użytkownika).  
  
     Po wyświetleniu kod dla formantu w IDE w czasie projektowania Visual Studio dodaje metoda obsługi zdarzeń dla formantu, jeśli jeden nie ma. Dodaje na przykład po dwukrotnym kliknięciu przycisku środowiska IDE programu obsługi zdarzeń dla jego <xref:System.Windows.Forms.Control.Click> zdarzenia (która jest wywoływana, gdy użytkownik wybierze przycisk). Dwukrotne kliknięcie pola wyboru IDE dodaje program obsługi zdarzeń dla jego <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia (która jest wywoływana, gdy użytkownik zaznaczy lub czyści okno).  
  
     Po dodaniu obsługi zdarzeń dla formantu, można powrócić do niego w dowolnym momencie z **Projektant formularzy systemu Windows** klikając dwukrotnie formant lub z menu, wybierając **widoku**  >  **Kod**.  
  
     Nazwy są ważne podczas tworzenia programów i metody (w tym obsługi zdarzeń) może mieć dowolną nazwę, która ma. Po dodaniu obsługi zdarzeń z IDE tworzy nazwę, na podstawie nazwy formantu i zdarzenia są obsługiwane. Na przykład zdarzenie kliknięcia przycisku o nazwie **Pokaż przycisk** jest nazywany `showButton_Click()` metoda obsługi zdarzeń. Ponadto nawiasy otwierające i zamykające `()` zazwyczaj są dodawane po nazwę metody, aby wskazać opisano metody. Jeśli zdecydujesz, aby zmienić nazwę zmiennej kodu, kliknij prawym przyciskiem myszy zmienną w kodzie, a następnie wybierz pozycję **Refaktoryzuj** > **zmienić**. Wszystkie wystąpienia tej zmiennej w kodzie zostały zmienione. Zobacz [Refaktoryzacja zmiany nazwy](../ide/reference/rename.md) Aby uzyskać więcej informacji.
  
## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 7: Dodawanie składników okna dialogowego do formularza](../ide/step-7-add-dialog-components-to-your-form.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: dodawanie formantów do formularza](../ide/step-5-add-controls-to-your-form.md).
