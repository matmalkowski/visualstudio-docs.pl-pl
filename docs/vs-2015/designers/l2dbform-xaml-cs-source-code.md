---
title: Kod źródłowy L2DBForm.XAML.CS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 741c91f290b7e509110c0320013965f8cf9bef0e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685478"
---
# <a name="l2dbformxamlcs-source-code"></a>Kod źródłowy L2DBForm.XAML.CS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [kod źródłowy L2DBForm.xaml.cs](https://docs.microsoft.com/visualstudio/designers/l2dbform-xaml-cs-source-code).  
  
Ten temat zawiera zawartość i opis kodu źródłowego języka C# w pliku L2DBForm.xaml.cs. Klasy częściowe L2XDBForm zawarte w tym pliku można podzielić na trzy logiczne sekcje: elementy członkowskie danych i `OnRemove` i `OnAddBook` procedury obsługi zdarzeń kliknięcia przycisku.  
  
## <a name="data-members"></a>Elementy członkowskie danych  
 Dwie prywatne składowe danych są używane do kojarzenia tej klasy, aby zasoby, okno L2DBForm.xaml.  
  
-   Zmienna przestrzeni nazw `myBooks` jest inicjowany do `"http://www.mybooks.com"`.  
  
-   Element członkowski `bookList` jest inicjowana w Konstruktorze ciąg CDATA w L2DBForm.xaml o następujący wiersz:  
  
    ```  
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
    ```  
  
## <a name="onaddbook-event-handler"></a>Program obsługi zdarzeń OnAddBook  
 Ta metoda zawiera trzy następujące instrukcje:  
  
-   Pierwsza instrukcja warunkowego jest używany do sprawdzania poprawności danych wejściowych.  
  
-   Druga instrukcja tworzy nową <xref:System.Xml.Linq.XElement> z ciągu wartości które użytkownik wprowadził w **Dodawanie nowej książki** sekcji interfejsu użytkownika.  
  
-   Ostatnią instrukcją dodaje ten nowy element książki do dostawcy danych w L2DBForm.xaml. W związku z tym dane dynamiczne powiązanie automatycznie aktualizuje interfejsu użytkownika za pomocą tego nowego elementu; bardzo dostarczone przez użytkownika jest wymagany żaden kod.  
  
## <a name="onremove-event-handler"></a>Program obsługi zdarzeń OnRemove  
 `OnRemove` Program obsługi jest bardziej skomplikowane niż `OnAddBook` obsługi dwóch powodów. Po pierwsze ponieważ nieprzetworzonym kodzie XML zawiera zachowanych biały znak, dopasowania oddzielane należy również usunąć wpis książki. Po drugie dla wygody zaznaczoną opcję spowodowało na usunięty element jest resetowany do poprzedniego na liście.  
  
 Jednak pracy core usunięcia elementu zaznaczoną książkę odbywa się przez tylko dwóch instrukcji:  
  
-   Po pierwsze element książki, skojarzone z aktualnie wybranego elementu w polu listy są pobierane:  
  
    ```  
    XElement selBook = (XElement)lbBooks.SelectedItem;   
    ```  
  
-   Następnie ten element zostanie usunięty z dostawcy danych:  
  
    ```  
    selBook.Remove();  
    ```  
  
 Ponownie wiązania danych dynamicznego gwarantuje interfejsu użytkownika programu jest automatycznie aktualizowana.  
  
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
 [Wskazówki: Elementu linqtoxmldatabinding — przykład](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)



