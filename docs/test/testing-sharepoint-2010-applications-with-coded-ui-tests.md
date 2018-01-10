---
title: "Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: fbda836ec423d9a86b51b2334a3015589512d816
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika
W tym kodowane testy interfejsu użytkownika w aplikacji programu SharePoint umożliwia Sprawdź, czy całej aplikacji, w tym jego formantów interfejsu użytkownika działa poprawnie. Kodowane testy interfejsu użytkownika można zweryfikować wartości i logika interfejsu użytkownika.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Co należy wiedzieć o kodowane testy interfejsu użytkownika?  
 Aby dowiedzieć się więcej na temat korzyści wynikające ze stosowania kodowane testy interfejsu użytkownika, zobacz [Użyj interfejsu użytkownika do testów Your kodu automatyzacji](../test/use-ui-automation-to-test-your-code.md) i [testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 - 5 rozdział Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Uwagi**  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") kodowanych testów interfejsu użytkownika dla aplikacji programu SharePoint są obsługiwane tylko w przypadku programu SharePoint 2010.  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnym") pomocy technicznej dla programu PowerPoint 2010 dla programu Visio i formantów w aplikacji programu SharePoint nie jest obsługiwane.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji programu SharePoint  
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) dla aplikacji programu SharePoint 2010 jest taka sama jak tworzenie testów dla innych typów aplikacji. Rekord i odtwarzanie jest obsługiwana dla wszystkich kontrolek interfejsu sieci Web edycji. Interfejs do wybierania kategorii i części sieci web są wszystkie formanty standardowe sieci web.  
  
 ![Części sieci web programu SharePoint](../test/media/cuit_sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  Rejestrowania akcji, sprawdzić poprawność działania przed wygenerowaniem kodu. Ponieważ istnieje kilka zachowania skojarzone z przesuwania myszy, jest on domyślnie. Należy zachować ostrożność usunąć nadmiarowe ruchów z kodowanych testów interfejsu użytkownika. Można to zrobić, edytując kod dla testu lub za pomocą [edytorze testu kodowanego interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Łącznie z testowaniem pakietu Office 2010 formantów w aplikacji SharePoint  
 Aby włączyć automatyzacji dla części sieci web pakietu office 2010 w aplikacji programu SharePoint, konieczne będzie wprowadzenie pewnych modyfikacji kodu pomocnicze.  
  
> [!WARNING]
>  Obsługa kontrolek Visio i PowerPoint 2010 nie jest obsługiwane.  
  
### <a name="excel-2010-cell-controls"></a>Formanty komórki programu Excel 2010  
 Aby uwzględnić formanty komórki programu Excel, należy pewnych zmian w kodzie kodowanego testu interfejsu użytkownika.  
  
> [!WARNING]
>  Wprowadzanie tekstu w komórce programu Excel, następuje akcję klucza strzałkę nie rejestruje poprawnie. Zaznacz komórki za pomocą myszy.  
  
 Rejestrowania akcji w pustej komórce, należy zmodyfikować kod przez podwójne kliknięcie komórki, a następnie wykonuje operację tekstu. Jest to niezbędne, ponieważ aktywuje kliknij komórkę, następuje dowolną akcję klawiatury `textarea` wewnątrz komórki przy realizacji. Po prostu rejestrowania `setvalue` w pustej komórce czy Wyszukaj `editbox` które nie jest obecne, dopóki nie zostanie kliknięta komórki. Na przykład:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Jeśli rejestrowania akcji w komórce pusty, a następnie rejestrowania pobiera nieco bardziej skomplikowane, ponieważ obecnie dodać tekst w komórce, nowy \<div > formant został dodany jako element podrzędny komórki. Nowe \<div > formant zawiera tylko wprowadzony tekst. Rejestrator musi zarejestrować akcje na nowym \<div > kontrolować; jednak nie ponieważ nowe \<div > formant nie istnieje dopiero po wprowadzeniu testu. Należy ręcznie wprowadzić następujące zmiany kodu do uwzględnienia ten problem.  
  
1.  Przejdź do inicjowania komórki i wprowadź `RowIndex` i `ColumnIndex` właściwości podstawowego:  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Znajdź `HtmlDiv` podrzędnym komórki:  
  
    ```csharp  
    private UITestControl getControlToDoubleClick(HtmlCell cell)   
    {   
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;   
         HtmlDiv pane = new HtmlDiv(cell);   
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;   
         // Class is an important property in finding pane   
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";   
         UITestControlCollection panes = pane.FindMatchingControls();   
         return panes[0];   
    }  
  
    ```  
  
3.  Dodaj kod dla myszy kliknij dwukrotnie działanie `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Dodaj kod, aby ustawić tekst na `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Włączanie kodowanych testów UI składników web Part Silverlight w aplikacji SharePoint 2010  
 Testowanie Silverlight nie jest obsługiwany w programie Visual Studio 2012 i nowszych. Jednak jeśli chcesz przetestować składników web Part Silverlight w aplikacji SharePoint 2010, oddzielne wtyczka Silverlight można zainstalować z galerii programu Visual Studio.  
  
#### <a name="setting-up-your-machine"></a>Konfigurowanie komputera  
  
1.  Upewnij się, że masz program Visual Studio 2012.1 lub nowszej.  
  
2.  Zainstaluj [dodatek testu interfejsu użytkownika programu Microsoft Visual Studio dla programu Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3.  Zainstaluj [Fiddler](http://www.fiddler2.com/fiddler2/). Jest to po prostu narzędzie, które powoduje przechwycenie i dzienników ruchu HTTP.  
  
4.  Pobierz [projektu fiddlerXap](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip). Rozpakuj go, skompiluj go i uruchom skrypt "CopySLHelper.bat", aby zainstalować pomocnika DLL, który jest wymagany do testowania składników web Part Silverlight, gdy jest używane narzędzie Fiddler.  
  
 Po skonfigurowaniu komputera, aby rozpocząć testowanie aplikacji SharePoint 2010 ze składnikami web Part Silverlight, wykonaj następujące kroki:  
  
#### <a name="testing-silverlight-web-parts"></a>Testowanie składników web Part Silverlight  
  
1.  Uruchom narzędzie Fiddler.  
  
2.  Wyczyścić pamięć podręczną przeglądarki. Jest to konieczne, ponieważ plik XAP, który zawiera DLL pomocnika automatyzacji interfejsu użytkownika programu Silverlight, zazwyczaj są buforowane. Mamy upewnij się, że zmodyfikowany plik XAP zostaje pobrana, dlatego firma Microsoft Wyczyść pamięć podręczną przeglądarki.  
  
3.  Otwórz stronę sieci web.  
  
4.  Uruchom Rejestrator i generowania kodu, jak w przypadku testowania aplikacji sieci web regularne.  
  
5.  Należy się upewnić, że wygenerowany kod odwołuje się do Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.  
  
     Aby uzyskać więcej informacji, zobacz [interfejsu użytkownika testowania programu SharePoint 2010 z programu Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="blogs"></a>Blogi  
 [Testowanie SharePoint 2010 z programu Visual Studio 2012 interfejsu użytkownika](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Opis logika wyszukiwania dla formantów Silverlight w kodowanego testu interfejsu użytkownika](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Pobieranie właściwości formantu Silverlight](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Indeks zawartości dla kodowanego testu interfejsu użytkownika](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 5 automatyzacji testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Forum  
 [Visual Studio ALM i Team Foundation Server blogu](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Zobacz także

[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)  
[Tworzenie rozwiązań programu SharePoint](/office-dev/office-dev/create-sharepoint-solutions)   
[Weryfikowanie i debugowanie kodu aplikacji programu SharePoint](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)   
[Kompilowanie i debugowanie rozwiązań SharePoint](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)   
[Profilowanie wydajności aplikacji SharePoint](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)
