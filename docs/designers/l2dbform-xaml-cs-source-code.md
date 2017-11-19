---
title: "Kod źródłowy L2DBForm.XAML.CS | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f34917cf5138201b1668e2800bc4ae1fd8e73a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="l2dbformxamlcs-source-code"></a>Kod źródłowy L2DBForm.XAML.CS
Ten temat zawiera zawartość i opis kodu źródłowego C# w pliku L2DBForm.xaml.cs. Klasy częściowe L2XDBForm zawarte w tym pliku mogą być podzielone trzy części logiczne: elementy członkowskie danych i `OnRemove` i `OnAddBook` przycisk kliknięcie uchwytów zdarzeń.  
  
## <a name="data-members"></a>Elementy członkowskie danych  
 Dwa elementy członkowskie danych prywatne są używane do kojarzenia klasę okna Zasoby L2DBForm.xaml.  
  
-   Zmienna przestrzeni nazw `myBooks` jest ustawiana na `"http://www.mybooks.com"`.  
  
-   Element członkowski `bookList` został zainicjowany w Konstruktorze ciągu CDATA w L2DBForm.xaml o następujący wiersz:  
  
    ```  
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
    ```  
  
## <a name="onaddbook-event-handler"></a>Program obsługi zdarzeń OnAddBook  
 Ta metoda zawiera trzy następujące instrukcje:  
  
-   Pierwsze wyrażenie warunkowe służy do sprawdzania poprawności danych wejściowych.  
  
-   Druga instrukcja tworzy nowy <xref:System.Xml.Linq.XElement> z ciągu wartości wprowadzone w **Dodawanie nowej książki** sekcji interfejsu użytkownika.  
  
-   Ostatnią instrukcją dodaje ten nowy element książki do dostawcy danych w L2DBForm.xaml. W rezultacie powiązania danych dynamicznego automatycznie zaktualizuje interfejsu użytkownika tego nowego elementu; Brak kodu bardzo dostarczone przez użytkownika jest wymagana.  
  
## <a name="onremove-event-handler"></a>Program obsługi zdarzeń OnRemove  
 `OnRemove` Program obsługi jest bardziej skomplikowane niż `OnAddBook` obsługi dwóch powodów. Najpierw ponieważ raw XML zawiera zachowanego biały znak, dopasowania newlines musi zostać usunięty z wpisu książki. Po drugie, jako udogodnienie zaznaczenia, który został usunięty element, zostanie zresetowany do poprzedniego na liście.  
  
 Jednak usunięcie elementu zaznaczoną książkę pracy core odbywa się przy tylko dwie instrukcje:  
  
-   Po pierwsze element book skojarzony z aktualnie wybranego elementu w polu listy są pobierane:  
  
    ```  
    XElement selBook = (XElement)lbBooks.SelectedItem;   
    ```  
  
-   Następnie ten element zostanie usunięty z dostawcy danych:  
  
    ```  
    selBook.Remove();  
    ```  
  
 Ponownie powiązania danych dynamicznego zapewnia interfejsu użytkownika programu jest automatycznie aktualizowany.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
  
### <a name="code"></a>Kod  
  
```csharp  
using System;  
using System.Linq;  
using System.Collections;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Input;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace LinqToXmlDataBinding {  
    /// <summary>  
    /// Interaction logic for L2XDBForm.xaml  
    /// </summary>  
  
    public partial class L2XDBForm : System.Windows.Window   
    {  
        XNamespace mybooks = "http://www.mybooks.com";  
        XElement bookList;  
  
        public L2XDBForm()   
        {  
            InitializeComponent();  
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
        }  
  
        void OnRemoveBook(object sender, EventArgs e)   
        {  
            int index = lbBooks.SelectedIndex;  
            if (index < 0) return;  
  
            XElement selBook = (XElement)lbBooks.SelectedItem;  
            //Get next node before removing element.  
            XNode nextNode = selBook.NextNode;  
            selBook.Remove();  
  
            //Remove any matching newline node.  
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))  
            { nextNode.Remove(); }  
  
            //Set selected item.   
            if (lbBooks.Items.Count > 0)  
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }  
        }  
  
        void OnAddBook(object sender, EventArgs e)   
        {  
            if (String.IsNullOrEmpty(tbAddID.Text) ||  
                String.IsNullOrEmpty(tbAddValue.Text))  
            {  
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");  
                return;   
            }  
            XElement newBook = new XElement(  
                                mybooks + "book",  
                                new XAttribute("id", tbAddID.Text),  
                                tbAddValue.Text);  
            bookList.Add("  ", newBook, "\r\n");  
        }  
    }  
}  
  
```  
  
### <a name="comments"></a>Komentarze  
 Dla skojarzonego źródła XAML te programy obsługi, zobacz [kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Przykład LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Kod źródłowy L2DBForm.XAML](../designers/l2dbform-xaml-source-code.md)