---
title: "Omówienie wstążki | Dokumentacja firmy Microsoft"
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
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fcf026af4877ee2aefe17551763752d385b63493
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ribbon-overview"></a>Wstążka ― Omówienie
  Wstążka jest sposób organizowania pokrewnych poleceń, dzięki czemu są one łatwiej znaleźć. Polecenia są wyświetlane jako formantów na Wstążce. Formanty są podzielone na *grup* wzdłuż poziomych pasków do górnej krawędzi okna aplikacji. Powiązane grupy są podzielone na kartach.  
  
 Większość funkcji, które były dostępne za pośrednictwem menu i pasków zadań w starszych wersjach systemu Microsoft Office teraz są dostępne za pomocą wstążki. Aby uzyskać więcej informacji, zobacz artykuł techniczny [Developer Przegląd interfejsu użytkownika dla pakietu Microsoft Office 2007](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customizing-the-microsoft-office-ribbon"></a>Dostosowywanie Wstążki pakietu Microsoft Office  
 Aby dostosować na Wstążce, należy dodać jedną z następujących elementów wstążki do projektu pakietu Office:  
  
-   **Wstążka (projektanta)**  
  
-   **Wstążki (XML)**  
  
 Na przykład do dostosowywania Wstążki programu Excel, Dodaj element wstążki do projektu dodatków VSTO programu Excel.  
  
### <a name="ribbon-visual-designer-item"></a>Element wstążki (projektanta)  
 **Wstążki (projektanta wizualnego)** elementu udostępnia zaawansowane narzędzia, która ułatwia projektowanie i tworzenie niestandardowych wstążki. Użyj **wstążki (projektanta wizualnego)** element, aby dostosować na Wstążce w następujący sposób:  
  
-   Dodawanie kart niestandardowych i wbudowanych do wstążki.  
  
-   Dodawanie grup niestandardowych do karty niestandardowych i wbudowanych.  
  
    > [!NOTE]  
    >  Karty wbudowane lub grupy jest już istnieje na Wstążce aplikacji pakietu Microsoft Office. Na przykład **danych** karta jest wbudowanej karty w programie Excel. **Połączeń** grupa jest wbudowana grupa na **danych** kartę.  
  
-   Dodawanie formantów niestandardowych do grupy niestandardowej.  
  
-   Dodawanie formantów niestandardowych do widoku Backstage.  
  
 Aby uzyskać więcej informacji o dostosowywaniu wstążki za pomocą **wstążki (projektanta wizualnego)** elementów, zobacz [projektanta wstążki](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Element wstążki (XML)  
 Użyj **wstążki (XML)** elementu, jeśli chcesz dostosować na Wstążce w taki sposób, który nie jest obsługiwany przez **wstążki (projektanta wizualnego)** elementu. Użyj **wstążki (XML)** element, aby dostosować na Wstążce w następujący sposób:  
  
-   Dodaj *wbudowanych* grupy kart niestandardowych lub wbudowanej karty.  
  
-   Dodawanie formantów wbudowanych do grupy niestandardowej.  
  
-   Dodaj niestandardowy kod do przesłonięcia obsługi zdarzeń formantów wbudowanych.  
  
-   Dostosowywanie paska narzędzi Szybki dostęp.  
  
-   Udostępnianie dostosowanie wstążki między dodatku VSTO za pomocą kwalifikowanego identyfikatora.  
  
 Aby uzyskać więcej informacji o dostosowywaniu wstążki za pomocą **wstążki (XML)** elementów, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
## <a name="exporting-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Eksportowanie wstążki z projektanta wstążki do XML wstążki  
 Jeśli utworzysz wstążki za pomocą projektanta wstążki i zdecyduj, czy chcesz dostosować na Wstążce w sposób który **wstążki (projektanta wizualnego)** element nie obsługuje, możesz wyeksportować do pliku XML wstążki.  
  
 Program Visual Studio automatycznie tworzy **wstążki (XML)** element i wypełnia pliku XML wstążki z elementów i atrybutów dla każdego formantu na Wstążce.  
  
 Nie wszystkie właściwości, które znajdują się w **właściwości** okna projektanta wstążki są przekazywane do pliku XML wstążki.  Na przykład Visual Studio nie eksportuje wartości **obrazu** lub **tekst** właściwości. To, ponieważ metoda wywołania zwrotnego należy utworzyć w pliku kodu wstążki wyeksportowanego projektu można przypisać obrazu lub ustawić tekst formantu. Program Visual Studio nie generuje automatycznie metody wywołania zwrotnego w ramach procesu eksportu.  
  
 Ponadto domyślna niezmienione wartości właściwości są niewidoczne w wynikowym pliku XML wstążki.  
  
 Aby uzyskać więcej informacji na temat eksportowania wstążki do XML, zobacz [porady: eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="updating-the-code"></a>Aktualizowanie kodu  
 Nowy plik kodu wstążki jest dodawany do **Eksploratora rozwiązań**. Ten plik zawiera klasę kodu XML wstążki. Należy utworzyć w metody wywołania zwrotnego `Ribbon Callbacks` tej klasy do obsługi akcje użytkownika, takie jak kliknięcie przycisku. Przenieś swój kod z obsługi zdarzeń do tych metod wywołania zwrotnego i zmodyfikuj kod do działania z modelu programowania rozszerzalności wstążki (RibbonX). Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
 Musisz również dodać kod, aby `ThisAddIn`, `ThisWorkbook`, lub `ThisDocument` klasę, która zastępuje metodę CreateRibbonExtensibilityObject i zwraca klasy XML wstążki do aplikacji pakietu Office.  
  
 Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
## <a name="adding-multiple-ribbon-items-to-a-project"></a>Dodawanie wielu elementów wstążki do projektu  
 Można dodać więcej niż jeden element wstążki do pojedynczego projektu. Jest to przydatne, jeśli chcesz wykonać jedną z poniższych czynności:  
  
-   Utwórz wstążek dla programu Outlook *inspektorzy*. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Inspektora jest oknem, które otwiera użytkowników wykonywania niektórych zadań, takich jak tworzenie wiadomości e-mail.  
  
-   Wybierz, które wstążki do wyświetlenia w czasie wykonywania.  
  
### <a name="selecting-which-ribbons-to-display-at-run-time"></a>Wybieranie, który wstęgami do wyświetlenia w czasie wykonywania  
 Ponieważ projekt może zawierać kilka Wstążce, należy wybrać wstążki, które można wyświetlić w czasie wykonywania.  
  
 Aby wybrać wstążki do wyświetlenia w czasie wykonywania, Zastąp metodę CreateRibbonExtensibilityObject w `ThisAddin`, `ThisWorkbook`, lub `ThisDocument` klasy z projektu i przywrócenie wstążki, które mają być wyświetlane. Poniższy przykład sprawdza wartość pola o nazwie `myCondition` i zwraca odpowiednie wstążki.  
  
> [!NOTE]  
>  Składnia używana w tym przykładzie zwraca wstążki, który został utworzony przy użyciu **wstążki (projektanta wizualnego)** elementu. Składnia dla zwracania wstążki, która jest tworzona przy użyciu **wstążki (XML)** elementu różni się nieznacznie. Aby uzyskać więcej informacji na temat zwracanie **wstążki (XML)** elementów, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
 Dodaj następujący kod:  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)|Pokazuje, jak dostosować Wstążki aplikacji pakietu Microsoft Office, dodawanie **wstążki (projektanta wizualnego)** lub **wstążki (XML)** elementu do projektu pakietu Office.|  
|[Projektant wstążki](../vsto/ribbon-designer.md)|W tym artykule opisano, jak można użyć projektanta wstążki, aby dodać niestandardowe karty, grupy i formantów na Wstążce aplikacji pakietu Microsoft Office.|  
|[Przewodnik: Tworzenie kart niestandardowych za pomocą Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Pokazuje, jak utworzyć niestandardowe karty wstążki za pomocą projektanta wstążki. Projektant wstążki służy do dodawania i formanty pozycji na karcie niestandardowe.|  
|[Model obiektu Wstążka — omówienie](../vsto/ribbon-object-model-overview.md)|Omówienie modelu silnie typizowany obiekt, który służy do pobierania i ustawiania właściwości formantów wstążki w czasie wykonywania.|  
|[Przewodnik: Aktualizowanie kontrolek na wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Pokazuje, jak model obiektu Wstążka umożliwia aktualizowanie formantów na Wstążce po załadowaniu wstążki do aplikacji pakietu Office.|  
|[Dostosowywanie Wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Zawiera wskazówki dotyczące dostosowywania na Wstążce w programie Microsoft Office Outlook.|  
|[Dostosowywanie Wstążki do InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Zawiera wskazówki dotyczące dostosowywania na Wstążce w programie Microsoft Office InfoPath.|  
|[Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)|Przedstawia sposób Pokaż, Ukryj, zmodyfikuj Wstążki i umożliwić użytkownikom uruchomić kod z kontrolek w niestandardowego okienka zadań, w okienku Akcje lub regionów formularzy programu Outlook.|  
|[Instrukcje: Zmiana położenia zakładki na wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Pokazuje, jak zmienić kolejność kart na Wstążce.|  
|[Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|Przedstawiono sposób dodawania grup i kontroli do wbudowanej karty.|  
|[Instrukcje: Dodawanie kontrolek do widoku zakulisowego](../vsto/how-to-add-controls-to-the-backstage-view.md)|Pokazuje, jak dodać kontrolki do menu dostępnym po kliknięciu **pliku**.|  
|[Instrukcje: Dodawanie przycisku Uruchom okno dialogowe do grupy wstążki](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Pokazuje, aby dodać do żadnej grupy na Wstążce przycisk Uruchom okno dialogowe.|  
|[Instrukcje: Eksportowanie wstążki z Projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Przedstawia sposób zaawansowane metody dostosowywania wstążki przez eksportowanie wstążki z projektanta do pliku XML wstążki.|  
|[XML — wstążka](../vsto/ribbon-xml.md)|W tym artykule wyjaśniono, jak dostosować wstążki za pomocą XML wstążki.|  
|[Przewodnik: Tworzenie kart niestandardowych za pomocą Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Pokazuje, jak utworzyć niestandardowe karty wstążki za pomocą **wstążki (XML)** elementu.|  
  
  