---
title: Aktualizowanie danych za pomocą TableAdapter | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c5188f56e440f7ec00f7537602aff10723441c3a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualizowanie danych za pomocą TableAdapter
Po ukończeniu zmodyfikowane i sprawdzić poprawności danych w zestawie danych, możesz wysłać zaktualizowane dane do bazy danych przez wywołanie metody `Update` metody [TableAdapter](../data-tools/create-and-configure-tableadapters.md). `Update` Metody aktualizacji jednej tabeli danych i uruchamia polecenie poprawne (INSERT, UPDATE lub DELETE) na podstawie <xref:System.Data.DataRow.RowState%2A> każdego wiersza danych w tabeli. Zestaw danych ma powiązane tabele, Visual Studio generuje klasę TableAdapterManager, która służy do aktualizacji. Klasa TableAdapterManager gwarantuje, że aktualizacje zostały wprowadzone we właściwej kolejności, w oparciu o ograniczenia klucza obcego, które są zdefiniowane w bazie danych. Korzystając z formantów powiązanych z danymi, architektura wiązania danych tworzy zmienną członkowską klasy TableAdapterManager, o nazwie tableAdapterManager. 
  
> [!NOTE]
>  Podczas próby aktualizacji źródła danych z zawartością zestawu danych, można uzyskać błędów. Aby uniknąć błędów, zaleca się umieszczenie kod, który wywołuje karty `Update` metody w ramach `try` / `catch` bloku.  
  
 Dokładne procedurę aktualizacji źródła danych może się różnić w zależności od potrzeb firmy, ale obejmuje następujące kroki:  
  
1.  Wywołaj karty `Update` metody w `try` / `catch` bloku.  
  
2.  Jeśli wystąpił wyjątek odszukaj wiersz danych, który spowodował błąd. 
  
3.  Uzgadnianie problem w danych wiersza (programowo, jeśli to możliwe, lub z uwzględnieniem nieprawidłowy wiersz do użytkownika w celu modyfikacji), a następnie ponów próbę aktualizacji (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="save-data-to-a-database"></a>Zapisywanie danych w bazie danych  
 Wywołanie `Update` metody TableAdapter. Podaj nazwę tabeli danych, która zawiera wartości, które mają być zapisane w bazie danych.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Aby zaktualizować bazę danych za pomocą TableAdapter  
  
-   Umieść element TableAdapter`Update` metody w `try` / `catch` bloku. Poniższy przykład pokazuje, jak zaktualizować zawartość `Customers` tabeli w `NorthwindDataSet` z poziomu `try` / `catch` bloku.  
  
     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)