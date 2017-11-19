---
title: Dodawanie walidacji do warstwowego zestawu danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b4c204c7515e8bb178ba1ee541650593c0281f15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Dodawanie walidacji do warstwowego zestawu danych
Dodawanie walidacji do zestawu danych, który jest dzielony stanowi rozwiązanie warstwowe zasadniczo jest taka sama jak dodawanie walidacji do pojedynczego pliku zestawu danych (dataset w jednym projekcie). Sugerowane lokalizacją sprawdzaniu poprawności danych jest podczas <xref:System.Data.DataTable.ColumnChanging> i/lub <xref:System.Data.DataTable.RowChanging> zdarzenia tabeli danych.  
  
 Zestaw danych udostępnia funkcje umożliwiające tworzenie klasy częściowe, do których można dodać kod użytkownika na zdarzenia Zmiana kolumn i wierszy w tabelach danych w zestawie danych. Aby uzyskać więcej informacji na temat Dodawanie kodu do zestawu danych w n warstwowa rozwiązania, zobacz [Dodawanie kodu do zestawów danych w aplikacjach warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md), i [Dodawanie kodu do TableAdapters w aplikacjach warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Aby uzyskać więcej informacji na temat klas częściowych, zobacz [porady: podział klas na klasy częściowe (Projektant klas)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) lub [klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
> [!NOTE]
>  Po oddzieleniu zestawów danych z TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące klasy częściowe dataset w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowy zestaw danych należy przenieść ręcznie do projektu dataset.  
  
> [!NOTE]
>  Zestaw danych w projektancie nie tworzy automatycznie programów obsługi zdarzeń w języku C# dla <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> zdarzenia. Należy ręcznie utworzyć program obsługi zdarzeń i dołączenie obsługi zdarzeń, który ma odpowiadające mu zdarzenie. Poniższe procedury zawierają opis sposobu tworzenia obsługi wymaganych zdarzeń w Visual Basic i C#.  
  
## <a name="validate-changes-to-individual-columns"></a>Sprawdzanie poprawności zmiany poszczególnych kolumn  
 Sprawdź poprawność wartości w poszczególnych kolumnach Obsługa <xref:System.Data.DataTable.ColumnChanging> zdarzeń. <xref:System.Data.DataTable.ColumnChanging> Zdarzenie jest zgłaszane, gdy wartość w kolumnie jest modyfikowana. Tworzenie procedury obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> zdarzeń, klikając dwukrotnie odpowiednie kolumny **Projektant obiektów Dataset**.  
  
 Kliknij dwukrotnie kolumnę, po raz pierwszy projektanta generuje programu obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> zdarzeń. `If...Then` Instrukcji tworzona jest również sprawdzający dla określonej kolumny. Na przykład następujący kod jest generowany po dwukrotnym kliknięciu DataDostawy kolumny z tabeli zamówienia Northwind:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  W języku C# projektów Projektant obiektów Dataset tworzy tylko częściowej klasy dla zestawu danych i poszczególnych tabel w zestawie danych. Projektant obiektów Dataset nie tworzy automatycznie obsługi zdarzeń <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> zdarzeń w języku C# jak w języku Visual Basic. W języku C# projektów należy ręcznie utworzyć metody obsługi zdarzenia i dołączenie metoda odpowiadające mu zdarzenie. Poniższa procedura zawiera kroki umożliwiające utworzenie obsługi wymaganych zdarzeń w Visual Basic i C#.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Aby dodać sprawdzania poprawności podczas zmiany wartości poszczególnych kolumn  
  
1.  Otwórz zestaw danych, klikając dwukrotnie **XSD** w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Kliknij dwukrotnie kolumnę, którą chcesz zweryfikować. Ta akcja tworzy <xref:System.Data.DataTable.ColumnChanging> obsługi zdarzeń.  
  
    > [!NOTE]
    >  Projektant obiektów Dataset nie tworzy automatycznie program obsługi zdarzeń dla zdarzenia C#. Kodu, które są niezbędne do obsługi zdarzeń w języku C# jest uwzględniony w następnej sekcji. `SampleColumnChangingEvent`zostanie utworzona i argumentów podłączono do <xref:System.Data.DataTable.ColumnChanging> zdarzenia w <xref:System.Data.DataTable.EndInit%2A> metody.  
  
3.  Dodaj kod, aby sprawdzić, czy `e.ProposedValue` zawiera dane, które spełnia wymagania aplikacji. Jeśli proponowaną wartość jest nieodpowiednia, należy ustawić kolumny, aby wskazać, że zawiera on wystąpił błąd.  
  
     Poniższy przykład kodu sprawdza, czy **ilość** kolumna zawiera wartość większą niż 0. Jeśli **ilość** jest mniejsza lub równa 0, kolumna ma ustawioną wartość wystąpił błąd. `Else` Klauzuli czyści błąd, jeśli **ilość** jest większa niż 0. Kod w obsłudze zdarzeń zmiany kolumna powinna wyglądać w następujący sposób:  
  
    ```vb  
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then  
        If CType(e.ProposedValue, Short) <= 0 Then  
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")  
        Else  
            e.Row.SetColumnError(e.Column, "")  
        End If  
    End If  
    ```    
    ```csharp  
    // Add this code to the DataTable partial class.  
  
    public override void EndInit()  
    {  
        base.EndInit();  
        // Hook up the ColumnChanging event  
        // to call the SampleColumnChangingEvent method.  
        ColumnChanging += SampleColumnChangingEvent;  
    }  
  
    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)  
    {  
        if (e.Column.ColumnName == QuantityColumn.ColumnName)  
        {  
            if ((short)e.ProposedValue <= 0)  
            {  
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
            }  
            else  
            {  
                e.Row.SetColumnError("Quantity", "");  
            }  
        }  
    }  
    ```  
  
## <a name="validate-changes-to-whole-rows"></a>Sprawdzanie poprawności zmiany do całego wierszy  
 Sprawdź poprawność wartości w wierszach całego Obsługa <xref:System.Data.DataTable.RowChanging> zdarzeń. <xref:System.Data.DataTable.RowChanging> Zdarzenie jest zgłaszane, gdy wartości wszystkie kolumny są zatwierdzone. Należy zweryfikować w <xref:System.Data.DataTable.RowChanging> zdarzenie, gdy wartość w jednej kolumnie opiera się na wartości w innej kolumny. Rozważmy na przykład OrderDate i DataDostawy w tabeli poleceń w bazie danych Northwind.  
  
 Po wprowadzeniu zamówień sprawdzania poprawności upewnia się, czy zamówienie nie zostanie wprowadzona z DataDostawy, który jest późniejsze niż OrderDate. W tym przykładzie wartości dla kolumny zarówno DataDostawy i OrderDate należy porównać, dlatego sprawdzanie poprawności zmiany poszczególnych kolumn nie ma sensu.  
  
 Tworzenie procedury obsługi zdarzeń dla <xref:System.Data.DataTable.RowChanging> zdarzeń, klikając dwukrotnie nazwę tabeli w pasku tytułu tabeli **Projektant obiektów Dataset**.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Aby dodać sprawdzania poprawności podczas zmiany do całego wierszy  
  
1.  Otwórz zestaw danych, klikając dwukrotnie **XSD** w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Kliknij dwukrotnie ikonę na pasku tytułu tabeli danych w projektancie.  
  
     Klasy częściowe jest tworzony z `RowChanging` obsługi zdarzeń i zostanie otwarty w edytorze kodu.  
  
    > [!NOTE]
    >  Projektant obiektów Dataset nie tworzy automatycznie programu obsługi zdarzeń dla <xref:System.Data.DataTable.RowChanging> zdarzeń w projektach C#. Należy utworzyć metody obsługi <xref:System.Data.DataTable.RowChanging> zdarzeń i wykonywania kodu następnie podpinanie zdarzeń w metodzie inicjowania tabeli.  
  
3.  Dodaj kod użytkownika wewnątrz deklaracji klasy częściowej.  
  
4.  Poniższy kod przedstawia dodania kodu użytkownika do sprawdzania poprawności podczas <xref:System.Data.DataTable.RowChanging> zdarzeń. Przykład C# zawiera również umożliwia utworzenie punktu zaczepienia metoda obsługi zdarzeń do kodu `OrdersRowChanging` zdarzeń.  
  
    ```vb  
    Partial Class OrdersDataTable  
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging  
            ' Add logic to validate columns here.  
            If e.Row.RequiredDate <= e.Row.OrderDate Then  
                ' Set the RowError if validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"  
            Else  
                ' Clear the RowError when validation passes.  
                e.Row.RowError = ""  
            End If  
        End Sub  
    End Class  
    ```  
    ```csharp  
    partial class OrdersDataTable  
    {  
        public override void EndInit()  
        {  
            base.EndInit();  
            // Hook up the event to the  
            // RowChangingEvent method.  
            OrdersRowChanging += RowChangingEvent;  
        }  
  
        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)  
        {  
            // Perform the validation logic.  
            if (e.Row.RequiredDate <= e.Row.OrderDate)  
            {  
                // Set the row to an error when validation fails.  
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";  
            }  
            else  
            {  
                // Clear the RowError if validation passes.  
                e.Row.RowError = "";  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie aplikacji warstwowych](../data-tools/n-tier-data-applications-overview.md)   
 [Wskazówki: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md)