---
title: Testowanie aplikacji SharePoint z kodowanych testów interfejsu użytkownika w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 5a23ed3a56c0d4b8daf8086e07ae04206c52ac4a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979454"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Testowanie aplikacji SharePoint z kodowanych testów interfejsu użytkownika

W tym kodowane testy interfejsu użytkownika w aplikacji programu SharePoint umożliwia Sprawdź, czy całej aplikacji, w tym jego formantów interfejsu użytkownika działa poprawnie. Kodowane testy interfejsu użytkownika można zweryfikować wartości i logika interfejsu użytkownika.

Aby dowiedzieć się więcej na temat korzyści wynikające ze stosowania kodowane testy interfejsu użytkownika, zobacz [automatyzacji interfejsu użytkownika używana do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

**Wymagania**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji programu SharePoint

[Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) dla aplikacji programu SharePoint jest taka sama jak tworzenie testów dla innych typów aplikacji. Rekord i odtwarzanie jest obsługiwana dla wszystkich kontrolek interfejsu sieci Web edycji. Interfejs do wybierania kategorii i części sieci web są wszystkie formanty standardowe sieci web.

![— składniki Web Part programu SharePoint](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Rejestrowania akcji, należy sprawdzić poprawność działania przed wygenerowaniem kodu. Ponieważ istnieje kilka zachowania skojarzone z przesuwania myszy, jest on domyślnie. Należy zachować ostrożność usunąć nadmiarowe ruchów z kodowanych testów interfejsu użytkownika. Można to zrobić, edytując kod dla testu lub za pomocą [edytorze testu kodowanego interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Formanty Office testu w aplikacji SharePoint

Aby włączyć automatyzacji dla niektórych części sieci web pakietu office w aplikacji programu SharePoint, konieczne będzie wprowadzenie pewnych modyfikacji kodu pomocniczych.

> [!NOTE]
> Testowanie Visio i PowerPoint formantów w aplikacji programu SharePoint nie jest obsługiwane.

### <a name="excel-cell-controls"></a>Formanty komórki programu Excel

Aby uwzględnić formanty komórki programu Excel, należy pewnych zmian w kodzie kodowanego testu interfejsu użytkownika.

> [!WARNING]
> Wprowadzanie tekstu w komórce programu Excel, następuje akcję klucza strzałkę nie rejestruje poprawnie. Zaznacz komórki za pomocą myszy.

Rejestrowania akcji w pustej komórce, należy zmodyfikować kod przez podwójne kliknięcie komórki, a następnie wykonuje operację tekstu. Jest to niezbędne, ponieważ aktywuje kliknij komórkę następuje dowolną akcję klawiatury `textarea` wewnątrz komórki przy realizacji. Po prostu rejestrowania `setvalue` w pustej komórce czy Wyszukaj `editbox` które nie jest obecne, dopóki nie zostanie kliknięta komórki. Na przykład:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Jeśli rejestrowania akcji w komórce pusty, a następnie rejestrowania pobiera nieco bardziej skomplikowane, ponieważ obecnie dodać tekst w komórce, nowy \<div > formant został dodany jako element podrzędny komórki. Nowe \<div > formant zawiera tylko wprowadzony tekst. Rejestrator musi zarejestrować akcje na nowym \<div > kontrolować; jednak nie ponieważ nowe \<div > formant nie istnieje dopiero po wprowadzeniu testu. Należy ręcznie wprowadzić następujące zmiany kodu do uwzględnienia ten problem.

1. Przejdź do inicjowania komórki i wprowadź `RowIndex` i `ColumnIndex` właściwości podstawowego:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Znajdź `HtmlDiv` podrzędnym komórki:

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

3. Dodaj kod dla myszy kliknij dwukrotnie działanie `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Dodaj kod, aby ustawić tekst na `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI Automation To Test Your Code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint Solutions](/office-dev/office-dev/create-sharepoint-solutions)
- [Verifying and Debugging SharePoint Code](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)
- [Building and Debugging SharePoint Solutions](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)
- [Profiling the Performance of SharePoint Applications](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)
