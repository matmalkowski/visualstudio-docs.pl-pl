---
title: 'Porady: pobieranie określonych wersji DataRow | Dokumentacja firmy Microsoft'
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
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: ed409bdafaa15052a7190480a7cbc46ac766de84
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631266"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Porady: pobieranie określonych wersji DataRow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy zostaną wprowadzone zmiany do wierszy danych, zestaw danych zachowuje zarówno oryginał (<xref:System.Data.DataRowVersion>) i nowe (<xref:System.Data.DataRowVersion>) wersje wiersza. Na przykład przed wywołaniem `AcceptChanges` metody, Twoja aplikacja ma dostęp do różnych wersji rekordu (zgodnie z definicją w <xref:System.Data.DataRowVersion> wyliczenie) i odpowiednio przetworzyć zmiany.  
  
> [!NOTE]
>  Istnieją różne wersje wiersza po jego edycji i przed miał `AcceptChanges` metodę o nazwie. Po `AcceptChanges` wywołano metodę, bieżąca i oryginalna wersja są takie same.  
  
 Przekazywanie <xref:System.Data.DataRowVersion> wartości wraz z indeks kolumny (lub nazwy kolumny jako ciąg) zwraca wartość z tej kolumny określonego wiersza wersji. Zmieniona kolumna jest określana w trakcie <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia, więc to dobry moment, aby sprawdzić różniące się wersje wierszy do celów sprawdzania poprawności. Jednak jeśli ograniczenia zostały tymczasowo zawieszone, te zdarzenia nie zostaną wywołane i trzeba będzie programowo określić kolumny, które zostały zmienione. Można to zrobić przez iterację <xref:System.Data.DataTable.Columns%2A> zbieranie i porównywanie różnych <xref:System.Data.DataRowVersion> wartości.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>Uzyskiwanie dostępu do oryginalnej wersji DataRow  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Aby uzyskać oryginalną wersję rekordu  
  
-   Dostęp do wartości kolumny przechodząc w <xref:System.Data.DataRowVersion> wiersza mają być zwracane.  
  
     Poniższy przykład pokazuje, jak można użyć <xref:System.Data.DataRowVersion> wartości, aby uzyskać oryginalnej wartości elementu `CompanyName` pole <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>Uzyskiwanie dostępu do bieżącej wersji DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Aby uzyskać bieżącą wersję rekordu  
  
-   Dostęp do wartości kolumny, a następnie dodaj parametr do indeksu wskazującego, którą wersję wiersza należy zwrócić.  
  
     Poniższy przykład pokazuje, jak można użyć <xref:System.Data.DataRowVersion> wartości, aby uzyskać bieżącą wartość `CompanyName` pole <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Przegląd aplikacji w programie Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)