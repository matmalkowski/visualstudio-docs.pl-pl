---
title: "Porady: dane z pamięci podręcznej do użycia w trybie Offline lub na serwerze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a8da60aa9d9dc3ab7becb56b3b4c7701494daef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Porady: dane z pamięci podręcznej do użycia w trybie offline lub na serwerze
  Można oznaczyć elementu danych w pamięci podręcznej w dokumencie, aby była ona dostępna w trybie offline. To również umożliwia dane w dokumencie ustawianych przez inny kod, gdy dokument jest przechowywany na serwerze.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Można oznaczyć elementu danych można buforować, gdy element danych jest zadeklarowany w kodzie lub, jeśli używasz <xref:System.Data.DataSet>, ustawiając właściwość w **właściwości** okna. Jeśli są buforowanie elementu danych, która nie jest <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>, upewnij się, że spełnia kryteria dotyczące pamięci podręcznej w dokumencie. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Zestawy danych utworzone za pomocą języka Visual Basic, które są oznaczone jako **pamięci podręcznej** i **WithEvents** (łącznie z zestawów danych, które są przeciągnięte z **źródeł danych** okna lub **Przybornika** zawierających **CacheInDocument** ustawioną właściwość **True**) ma podkreślenia prefiksem nazwy w pamięci podręcznej. Na przykład można utworzyć zestawu danych i nadaj mu nazwę **klientów**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nazwa będzie **_Customers** w pamięci podręcznej. Jeśli używasz <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Aby uzyskać dostęp do tego elementu pamięci podręcznej, należy określić **_Customers** zamiast **klientów**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Do pamięci podręcznej danych w dokumencie przy użyciu kodu  
  
1.  Zadeklaruj pola publicznego lub właściwości elementu danych jako element członkowski klasy elementu hosta w projekcie, takich jak `ThisDocumen`t klasy w projekcie programu Word lub `ThisWorkbook` klasy w projekcie programu Excel.  
  
2.  Zastosuj <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu do elementu członkowskiego, aby oznaczyć element danych, które mają być przechowywane w pamięci podręcznej danych dokumentu. Poniższy przykład dotyczy deklaracji pola dla tego atrybutu <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Dodaj kod, aby utworzyć wystąpienia elementu danych i, jeśli to konieczne, aby ją załadować z bazy danych.  
  
     Element danych jest ładować tylko po pierwszym utworzeniu; pamięci podręcznej pozostaje na dokument, i musi zapisać inny kod, aby go zaktualizować.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Do pamięci podręcznej zestawu danych w dokumencie przy użyciu okna właściwości  
  
1.  Dodaj zestaw danych do projektu przy użyciu narzędzi w projektancie programu Visual Studio, na przykład przez dodanie źródła danych do Twój projekt używający **źródeł danych** okna.  
  
2.  Utwórz wystąpienie zestawu danych, jeśli jeszcze nie istnieje i wybierz wystąpienie w projektancie.  
  
3.  W **właściwości** ustaw **CacheInDocument** właściwości **True**.  
  
     Aby uzyskać więcej informacji, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).  
  
4.  W **właściwości** ustaw **Modyfikatory** właściwości **publicznego** (domyślnie jest **wewnętrzne**).  
  
## <a name="see-also"></a>Zobacz też  
 [Buforowanie danych](../vsto/caching-data.md)   
 [Porady: programowane buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Porady: dane w dokumencie chroniony hasłem z pamięci podręcznej](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Zapisywanie danych](/visualstudio/data-tools/saving-data)  
  
  