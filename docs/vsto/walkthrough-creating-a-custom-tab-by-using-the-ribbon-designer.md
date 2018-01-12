---
title: "Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cdbbd7ee286c97a986e89ccdb5bdcfdde4ef7578
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer"></a>Wskazówki: tworzenie kart niestandardowych za pomocą Projektanta wstążki
  Za pomocą projektanta wstążki, można tworzenie kart niestandardowych, a następnie dodaj i ustawianie formantów na nim.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   [Tworzenie okienka akcji](#BKMK_CreateActionsPanes).  
  
-   [Tworzenie kart niestandardowych](#BKMK_CreateCustomTab).  
  
-   [Wyświetlanie i ukrywanie okienka akcji za pomocą przycisków na karcie niestandardowe](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Excel  
  
## <a name="creating-an-excel-workbook-project"></a>Tworzenie projektu skoroszyt programu Excel  
 W przypadku korzystania z projektanta wstążki są niemal identyczne dla wszystkich aplikacji pakietu Office. W tym przykładzie użyto skoroszytu programu Excel.  
  
#### <a name="to-create-an-excel-workbook-project"></a>Aby utworzyć projekt skoroszytu programu Excel  
  
-   Tworzenie projektu skoroszyt programu Excel o nazwie **MyExcelRibbon**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt w Projektancie i dodaje **MyExcelRibbon** projektu do **Eksploratora rozwiązań**.  
  
##  <a name="BKMK_CreateActionsPanes"></a>Tworzenie okienka akcji  
 Dodaj dwa okienka Akcje niestandardowe do projektu. Pokazywanie i ukrywanie okienka te akcje na karcie niestandardowe przyciski później zostaną dodane.  
  
#### <a name="to-create-actions-panes"></a>Aby utworzyć okienka akcji  
  
1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **ActionsPaneControl**, a następnie wybierz pozycję **Dodaj**.  
  
     **ActionsPaneControl1.cs** lub **ActionsPaneControl1.vb** plik zostanie otwarty w projektancie.  
  
3.  Z **formanty standardowe** karcie **przybornika**, Dodaj etykietę powierzchnię projektanta.  
  
4.  W **właściwości** ustaw **tekst** właściwości label1 do **1 okienka Akcje**.  
  
5.  Powtórz kroki od 1 do 5, aby utworzyć drugi okienka Akcje i etykiety. Ustaw **tekst** właściwości drugi etykiety w celu **2 okienka Akcje**.  
  
##  <a name="BKMK_CreateCustomTab"></a>Tworzenie kart niestandardowych  
 Jednym z wytycznymi projektowania aplikacji pakietu Office jest użytkowników powinien zawsze mieć formantu interfejsu użytkownika aplikacji pakietu Office. Aby dodać tę możliwość dla okienka akcji, można dodać przyciski pokazać lub ukryć poszczególnych okienkach akcji z kart niestandardowych na Wstążce. Aby utworzyć kart niestandardowych, Dodaj **wstążki (projektanta wizualnego)** elementu do projektu. Projektant pomaga Dodaj formanty pozycji, ustaw właściwości kontrolki i obsługę zdarzeń formantu.  
  
#### <a name="to-create-a-custom-tab"></a>Aby utworzyć kart niestandardowych  
  
1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (projektanta wizualnego)**.  
  
3.  Zmień nazwę nowego wstążki do **MyRibbon**i wybierz polecenie **Dodaj**.  
  
     **MyRibbon.cs** lub **MyRibbon.vb** plik zostanie otwarty w Projektancie Wstążki i wyświetla kartę domyślne i grupy.  
  
4.  W Projektancie wstążki wybierz kartę domyślne.  
  
5.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie ustawić **ControlIdType** właściwości **niestandardowy**.  
  
6.  Ustaw **etykiety** właściwości **Moja karta niestandardowe**.  
  
7.  Projektant wstążki, wybierz **grupa1**.  
  
8.  W **właściwości** ustaw **etykiety** do **Menedżera okienka Akcje**.  
  
9. Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij przycisk na **grupa1**.  
  
10. Wybierz **button1**.  
  
11. W **właściwości** ustaw **etykiety** do **Pokaż 1 okienka Akcje**.  
  
12. Dodawanie drugiego przycisku do **grupa1**i ustaw **etykiety** właściwości **Pokaż 2 okienka Akcje**.  
  
13. Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij **ToggleButton** kontrolować na **grupa1**.  
  
14. Ustaw **etykiety** właściwości **ukrywanie okienka Akcje**.  
  
##  <a name="BKMK_HideShowActionsPane"></a>Wyświetlanie i ukrywanie okienka akcji za pomocą przycisków na karcie niestandardowe  
 Ostatnim krokiem jest Dodaj kod, który odpowiada użytkownik. Dodawanie obsługi zdarzeń <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenia dwóch przycisków i <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzeń przycisk przełącznika. Dodaj kod, aby te programy obsługi zdarzeń, aby umożliwić wyświetlanie i ukrywanie okienka akcji.  
  
#### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Aby ukryć i pokazać za pomocą przycisków na niestandardowej karcie okienka akcji  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów MyRibbon.cs lub MyRibbon.vb, a następnie wybierz **kod widoku**.  
  
2.  Dodaj następujący kod do góry `MyRibbon` klasy. Ten kod tworzy dwa obiekty w okienku Akcje.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Zastąp `MyRibbon_Load` metodę z następującym kodem. Ten kod dodaje obiekty w okienku Akcje <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> kolekcji i ukrywa obiektów z widoku. Kod Visual C# również dołącza delegatów na kilka wstążce kontroli zdarzenia.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Dodaj następujące metody obsługi zdarzeń trzy do `MyRibbon` klasy. Te metody obsługi <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenia dwóch przycisków i <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzeń przycisk przełącznika. Programy obsługi zdarzeń dla button1 i button2 wyświetlenie okienka akcji alternatywny. Program obsługi zdarzeń dla toggleButton1 pokazuje i ukrywa ją w okienku Akcje active.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="testing-the-custom-tab"></a>Testowanie kart niestandardowych  
 Po uruchomieniu projektu, uruchamia program Excel i **Moja karta niestandardowe** zostanie wyświetlona karta na Wstążce. Wybierz przyciski na **Moja karta niestandardowe** by pokazać lub ukryć okienka akcji.  
  
#### <a name="to-test-the-custom-tab"></a>Aby przetestować kart niestandardowych  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Wybierz **Moja karta niestandardowe** kartę.  
  
3.  W **Menedżera okienka Akcje niestandardowe** grupy, wybierz **Pokaż 1 okienka Akcje**.  
  
     Zostanie wyświetlony w okienku Akcje i etykiety **1 okienka Akcje**.  
  
4.  Wybierz **Pokaż okienko akcji 2**.  
  
     Zostanie wyświetlony w okienku Akcje i etykiety **2 okienka Akcje**.  
  
5.  Wybierz **ukrywanie okienka Akcje**.  
  
     Okienka akcji nie są już widoczne.  
  
## <a name="next-steps"></a>Następne kroki  
 Można poznać więcej informacji na temat sposobu dostosowywania interfejsu użytkownika pakietu Office z tych tematów:  
  
-   Dodaj kontekstowa interfejsu użytkownika do dostosowania dowolnym poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
-   Rozszerzenie standardowych lub niestandardowych formularzy programu Microsoft Office Outlook. Aby uzyskać więcej informacji, zobacz [wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Porady: zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Porady: dodawanie formantów do widoku Zakulisowego](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Model obiektu Wstążka — omówienie](../vsto/ribbon-object-model-overview.md)  
  
  