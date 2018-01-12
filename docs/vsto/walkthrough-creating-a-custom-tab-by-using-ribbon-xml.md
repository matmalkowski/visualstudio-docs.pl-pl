---
title: "Wskazówki: Tworzenie kart niestandardowych za pomocą XML wstążki | Dokumentacja firmy Microsoft"
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
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b736ace651854b3b6a527685e150f6f1ec7194c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-ribbon-xml"></a>Wskazówki: tworzenie kart niestandardowych za pomocą XML wstążki
  W tym przewodniku pokazano, jak utworzyć niestandardowe karty wstążki za pomocą **wstążki (XML)** elementu.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie przycisków do **Add-Ins** kartę. **Add-Ins** karta jest karcie domyślnej, która jest zdefiniowana w pliku XML wstążki.  
  
-   Automatyzowanie programu Microsoft Office Word za pomocą przycisków na **Add-Ins** kartę.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Word.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO programu Word. Później będzie można dostosować **Add-Ins** kartę tego dokumentu.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Utwórz **-programu Word** projektu o nazwie **MyRibbonAddIn**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** pliku kodu i dodaje **MyRibbonAddIn** projektu do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-vsto-add-ins-tab"></a>Tworzenie kart dodatków narzędzi VSTO  
 Aby utworzyć **Add-Ins** , Dodaj **wstążki (XML)** elementu do projektu. W dalszej części tego przewodnika niektóre przyciski zostaną dodane do tej karty.  
  
#### <a name="to-create-the-add-ins-tab"></a>Aby utworzyć karta dodatki  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (XML)**.  
  
3.  Zmień nazwę nowego wstążki do **MyRibbon**i kliknij przycisk **Dodaj**.  
  
     **MyRibbon.cs** lub **MyRibbon.vb** plik zostanie otwarty w projektancie. Plik XML o nazwie **MyRibbon.xml** jest także dodawane do projektu.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisAddin.cs** lub **ThisAddin.vb**, a następnie kliknij przycisk **kod widoku**.  
  
5.  Dodaj następujący kod do **thisaddin —** klasy. Ten kod zastępuje metodę CreateRibbonExtensibilityObject i zwraca klasy XML wstążki do aplikacji pakietu Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyRibbonAddIn** projektu, a następnie kliknij przycisk **kompilacji**. Upewnij się, że projekt tworzy się bez błędów.  
  
## <a name="adding-buttons-to-the-add-ins-tab"></a>Dodawanie przycisków do karta dodatki  
 Celem tego dodatku VSTO jest umożliwić użytkownikom umożliwiają dodawanie tekstu standardowego lub konkretnej tabeli do aktywnego dokumentu. Zapewnia interfejs użytkownika, należy dodać dwa przyciski **Add-Ins** kartę przez zmodyfikowanie pliku XML wstążki. W dalszej części tego przewodnika zdefiniujesz metody wywołania zwrotnego dla przycisków. Aby uzyskać więcej informacji o pliku XML wstążki, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-buttons-to-the-add-ins-tab"></a>Aby dodać przyciski do karta dodatki  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyRibbon.xml** , a następnie kliknij przycisk **Otwórz**.  
  
2.  Zastąp zawartość **kartę** elementu za pomocą następujących XML. Plik XML zmiany etykiety domyślnej grupy formant do **zawartości**, i dodaje dwie nowe przyciski z etykietami **Wstaw tekst** i **Wstaw tabelę**.  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automating-the-document-by-using-the-buttons"></a>Automatyzowanie dokumentu za pomocą przycisków  
 Należy dodać `onAction` metody wywołania zwrotnego dla **Wstaw tekst** i **Wstaw tabelę** przyciski do wykonania akcji, gdy użytkownik kliknie je. Aby uzyskać więcej informacji na temat metody wywołania zwrotnego dla formantów wstążki, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-callback-methods-for-the-buttons"></a>Aby dodać wywołanie zwrotne metody przycisków  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyRibbon.cs** lub **MyRibbon.vb**, a następnie kliknij przycisk **Otwórz**.  
  
2.  Dodaj następujący kod do góry **MyRibbon.cs** lub **MyRibbon.vb** pliku. Ten kod tworzy alias dla <xref:Microsoft.Office.Interop.Word> przestrzeni nazw.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Dodaj następującą metodę do `MyRibbon` klasy. Jest to metoda wywołania zwrotnego dla **Wstaw tekst** przycisku, który dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji kursora.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Dodaj następującą metodę do `MyRibbon` klasy. Jest to metoda wywołania zwrotnego dla **Wstaw tabelę** przycisk umożliwiający Dodawanie tabeli do aktywnego dokumentu w bieżącej lokalizacji kursora.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Testowanie dodatku narzędzi VSTO  
 Po uruchomieniu projektu, zostanie otwarty program Word i kartę o nazwie **Add-Ins** pojawia się na Wstążce. Kliknij przycisk **Wstaw tekst** i **Wstaw tabelę** przyciski na **Add-Ins** kartę do testowania kodu.  
  
#### <a name="to-test-your-vsto-add-in"></a>Aby przetestować użytkownika dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Upewnij się, że **Add-Ins** karta jest widoczna na Wstążce.  
  
3.  Kliknij przycisk **Add-Ins** kartę.  
  
4.  Upewnij się, że **zawartości** grupa jest widoczna na Wstążce.  
  
5.  Kliknij przycisk **Wstaw tekst** przycisk **zawartości** grupy.  
  
     Ciąg jest dodawany do dokumentu w bieżącej lokalizacji kursora.  
  
6.  Kliknij przycisk **Wstaw tabelę** przycisk **zawartości** grupy.  
  
     Tabela jest dodawany do dokumentu w bieżącej lokalizacji kursora.  
  
## <a name="next-steps"></a>Następne kroki  
 Można poznać więcej informacji na temat sposobu dostosowywania interfejsu użytkownika pakietu Office z tych tematów:  
  
-   Dostosowywanie Wstążki różnych aplikacji pakietu Office. Aby uzyskać więcej informacji o aplikacjach, które obsługują Dostosowywanie Wstążki, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
-   Dostosowywanie Wstążki aplikacji pakietu Office za pomocą projektanta wstążki. Aby uzyskać więcej informacji, zobacz [projektanta wstążki](../vsto/ribbon-designer.md).  
  
-   Utwórz okienko akcji niestandardowych. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Microsoft Office Outlook przy użyciu regionów formularzy programu Outlook. Aby uzyskać więcej informacji, zobacz [wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  