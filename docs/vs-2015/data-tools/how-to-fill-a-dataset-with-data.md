---
title: 'Porady: wypełnianie zestawu danych danymi | Dokumentacja firmy Microsoft'
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
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c2bba5c7bcdf1453129c6c3677e750c0e5599bac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684970"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Porady: wypełnianie zestawu danych danymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fraza "wypełnianie zestawu danych danymi" odnosi się do ładowania danych do poszczególnych <xref:System.Data.DataTable> obiektów, które składają się dataset. Wypełnij tabel danych przez wykonywanie zapytań TableAdapter lub wykonując adapter danych (na przykład <xref:System.Data.SqlClient.SqlDataAdapter>) polecenia.  
  
 Czy należy używać adapterów TableAdapter lub danych zależy od tego, jak utworzyć zestaw danych. Jeśli używasz narzędzi projektowania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], takich jak [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), zestaw danych zawiera adapterów TableAdapter. Aby uzyskać więcej informacji na temat elementów TableAdapter, zobacz [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md). Jeśli zestaw danych został utworzony programowo, będzie zazwyczaj należy utworzyć adapterów danych do ładowania danych do tabel danych.  
  
> [!NOTE]
>  Podczas przeciągania elementów z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na formularz, kod w celu wypełnienia tabeli danych z danymi jest automatycznie dodawany do `Form_Load` programu obsługi zdarzeń. Otwórz formularz w edytorze kodu, aby zobaczyć dokładnie składni języka, aby wypełnić określonych tabel. Jeśli nie chcesz wypełnić tabelę podczas ładowania formularza, możesz przenieść ten kod do innej metody lub usuń go całkowicie.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>Wypełnianie zestawu danych za pomocą adaptera TableAdapter  
 Zapytanie może być wywoływany w metodzie TableAdapter do ładowania danych do tabel danych w zestawie danych. Przekaż <xref:System.Data.DataTable> chcesz wypełnić do wykonywania zapytań w TableAdapter. Jeśli zapytanie pobiera parametry, należy przekazać te metody także. Jeśli zestaw danych zawiera wiele tabel, powinny mieć osobne TableAdapters dla każdej tabeli i w związku z tym jest wypełnienie każdej tabeli oddzielnie.  
  
> [!NOTE]
>  Domyślnie za każdym razem, gdy wykonywanie zapytań TableAdapter, dane w tabeli jest czyszczona przed wyniki zapytania są ładowane do tabeli. Możesz zachować istniejące dane w tabeli i Dołącz wyniki, ustawiając TableAdapter `ClearBeforeFill` właściwość `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Aby wypełnić zestaw danych za pomocą adaptera TableAdapter  
  
1.  Otwórz formularz lub składnik **Edytor kodu**.  
  
2.  Dodaj kod w dowolnym miejscu w Twojej aplikacji, w których należy załadować tabelę danych z danymi. Jeśli zapytanie nie przyjmuje parametrów, Przekaż <xref:System.Data.DataTable> chcesz wypełnić. Kod powinien wyglądać podobnie do następującego:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Jeśli zapytanie pobiera parametry, Przekaż <xref:System.Data.DataTable> do wypełnienia a parametry oczekiwany przez zapytanie. W zależności od rzeczywistych parametrów w zapytaniu kod powinien wyglądać podobnie do następujących:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>Wypełnianie zestawu danych za pomocą elementu DataAdapter  
 Wywołania adapter danych `Fill` metody. Powoduje to, że karty wykonać tę instrukcję SQL lub procedury składowanej do którego odwołuje się jego `SelectCommand` właściwość i umieść wyniki do tabeli w zestawie danych. Jeśli zestaw danych zawiera wiele tabel, powinny mieć kart osobne dane dla każdej tabeli i w związku z tym jest wypełnienie każdej tabeli oddzielnie.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>Aby wypełnić zestaw danych z danymi przy użyciu elementu DataAdapter  
  
-   Wywołaj <xref:System.Data.Common.DataAdapter.Fill%2A> metody <xref:System.Data.Common.DataAdapter>, przekazując <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> załadować dane do. Na przykład:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     Zazwyczaj należy podać nazwę <xref:System.Data.DataTable> załadować dane do. Jeśli przekażesz w <xref:System.Data.DataSet> zamiast tabelę danych z konkretnych <xref:System.Data.DataTable> o nazwie `Table1` jest dodawane do zestawu danych i załadowane wyniki z bazy danych (w przeciwieństwie do ładowania danych w istniejącym <xref:System.Data.DataTable> w zestawie danych). Aby uzyskać więcej informacji, zobacz [wypełnianie zestawu danych z elementu DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>Zobacz też  
 [Wypełnij zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)