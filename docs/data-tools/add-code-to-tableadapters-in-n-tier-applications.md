---
title: Dodawanie kodu do TableAdapters w aplikacjach warstwowych | Dokumentacja firmy Microsoft
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 54df2144511e847988c6f11212e9c9a4941d0b38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Dodawanie kodu do TableAdapters w aplikacjach warstwowych
Pozwala na poszerzanie funkcjonalności TableAdapter, tworząc plik częściowej klasy dla TableAdapter oraz dodawanie kodu do niego (zamiast Dodawanie kodu do *DatasetName*. Plik DataSet.Designer). Klasy częściowe Włącz kod dla określonej klasy podzielony między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [partial (typ)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
Kod, który definiuje TableAdapter jest generowany za każdym razem, gdy zmian w TableAdapter w zestawie danych. Ten kod jest również wygenerowany podczas wprowadzania zmian podczas wykonywania żadnych kreatora, który modyfikuje konfiguracji TableAdapter. Aby zapobiec usunięciu podczas ponownego generowania TableAdapter kodu, Dodaj kod do pliku częściowej klasy TableAdapter.  
  
Domyślnie po oddzieleniu zestawu danych i kod TableAdapter, wynik jest plik odrębny klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName*. Designer.VB (lub *DatasetName*. Designer.cs narzędzie) zawierający kod TableAdapter. Projekt, który jest oznaczany **projektu Dataset** właściwość zawiera plik o nazwie *DatasetName*. DataSet.Designer.vb (lub *DatasetName*. DataSet.Designer.cs) zawiera kod zestawu danych.  
  
> [!NOTE]
>  Po oddzieleniu zestawów danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące klasy częściowe dataset w projekcie nie zostaną automatycznie przeniesione. Istniejące klasy częściowy zestaw danych należy przenieść ręcznie do projektu dataset.  
  
> [!NOTE]
>  Zestaw danych udostępnia funkcje generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń, gdy potrzebny jest sprawdzania poprawności. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aby dodać kod użytkownika do TableAdapter w aplikacji warstwowych  
  
1.  Zlokalizuj projektu, który zawiera plik XSD.
  
2.  Kliknij dwukrotnie **XSD** plik, aby otworzyć **Projektant obiektów Dataset**.  
  
3.  Kliknij prawym przyciskiem myszy obiekt TableAdapter, który chcesz dodać kod, a następnie wybierz **kod widoku**.  
  
     Klasy częściowe zostanie utworzona i zostanie otwarty w edytorze kodu.  
  
4.  Dodaj kod wewnątrz deklaracji klasy częściowej.  
  
5.  W poniższym przykładzie pokazano kod w celu dodania `CustomersTableAdapter` w `NorthwindDataSet`:  
  
    ```vb  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```csharp  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz także
[Omówienie aplikacji warstwowych](../data-tools/n-tier-data-applications-overview.md)   
[Dodawanie kodu do zestawów danych w aplikacjach warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[Tworzenie i konfigurowanie TableAdapters](create-and-configure-tableadapters.md)   
[Hierarchiczna aktualizacja — Przegląd](hierarchical-update.md)   
