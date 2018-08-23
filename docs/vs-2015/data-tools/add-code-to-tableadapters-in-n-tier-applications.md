---
title: Dodawanie kodu do TableAdapters w aplikacjach n warstwowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd46596ff474a33be42b8c5118404845a39c2b7d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683890"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Dodawanie kodu do TableAdapters w aplikacjach n warstwowych](https://docs.microsoft.com/visualstudio/data-tools/add-code-to-tableadapters-in-n-tier-applications).  
  
  
Możesz rozszerzyć funkcjonalność `TableAdapter` przez utworzenie pliku częściowej klasy dla `TableAdapter` i dodając kod do jego (zamiast opcji dodawania kodu *DatasetName*. Plik DataSet.Designer). Klasy częściowe Włącz kod dla określonej klasy do podzielone między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) lub [partial (typ)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
 Kod, który definiuje `TableAdapter` jest generowana za każdym razem, gdy zmiany zostały wprowadzone `TableAdapter` (w [tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md)). Ten kod zostanie również wygenerowany, gdy zostaną wprowadzone zmiany podczas uruchamiania dowolnego kreatora, który modyfikuje konfigurację `TableAdapter`. Aby zapobiec usunięciu podczas ponownego generowania o kodzie `TableAdapter`, Dodaj kod do pliku częściowej klasy `TableAdapter`.  
  
 Domyślnie po rozdzielenie zestawu danych i `TableAdapter` kod, wynik jest plik klasy dyskretnych w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName*. Designer.VB (lub *DatasetName*. Designer.cs narzędzie), który zawiera `TableAdapter` kodu. Projekt, który jest wyznaczone w **projektu Dataset** właściwość ma w pliku o nazwie *DatasetName*. DataSet.Designer.vb (lub *DatasetName*. DataSet.Designer.cs) zawierający kod zestawu danych.  
  
> [!NOTE]
>  Kiedy oddzielisz zestawy danych i `TableAdapter`s (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie zostaną automatycznie przeniesione. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.  
  
> [!NOTE]
>  [Tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md) oferuje funkcję do generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń, gdy sprawdzanie poprawności jest potrzebny. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aby dodać kod użytkownika do TableAdapter w aplikacji n-warstwowej  
  
1.  Znajdź projekt, który zawiera plik XSD ( [tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Kliknij dwukrotnie **XSD** plik, aby otworzyć [tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Kliknij prawym przyciskiem myszy `TableAdapter` , którą chcesz dodać kod, a następnie wybierz**Wyświetl kod**.  
  
     Klasy częściowe, zostanie utworzona i zostanie otwarty w edytorze kodu.  
  
4.  Dodaj kod wewnątrz deklaracji klasy częściowej.  
  
5.  Poniższy kod przedstawia gdzie dodać kod do `CustomersTableAdapter` w `NorthwindDataSet`:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)   
 [Dodawanie kodu do zestawów danych w aplikacjach n warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [TableAdapterManager — Przegląd](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Hierarchiczna aktualizacja — Przegląd](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Tworzenie aplikacji do danych](../data-tools/creating-data-applications.md)

