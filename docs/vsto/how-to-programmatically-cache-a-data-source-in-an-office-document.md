---
title: 'Porady: programowane buforowanie źródła danych w dokumencie pakietu Office | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29451bab5caeeaf3f9de0b9344ae52430ec045a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Porady: programowane buforowanie źródła danych w dokumencie programu Word
  Obiekt danych można programowo dodać do pamięci podręcznej danych w dokumencie, wywołując `StartCaching` metody hosta elementów, takich jak <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, lub <xref:Microsoft.Office.Tools.Excel.Worksheet>. Usuń obiekt danych z pamięci podręcznej danych przez wywołanie metody `StopCaching` metody elementu host.  
  
 `StartCaching` — Metoda i `StopCaching` metody są prywatne, ale są one w IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Jeśli używasz `StartCaching` metodę, aby dodać obiekt danych w pamięci podręcznej danych obiektu danych nie musi być zadeklarowana z <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu. Jednak obiekt danych musi spełniać określone wymagania, które mają zostać dodane do pamięci podręcznej danych. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).  
  
### <a name="to-programmatically-cache-a-data-object"></a>Aby programowo pamięci podręcznej obiektu danych  
  
1.  Deklarowanie obiekt danych na poziomie klasy, nie wewnątrz metody. W tym przykładzie przyjęto założenie, możesz deklarowanie <xref:System.Data.DataSet> o nazwie `dataSet1` przewidzianą do pamięci podręcznej programowo.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Utwórz wystąpienie obiektu danych, a następnie wywołać `StartCaching` metodę wystąpienia dokument lub arkusz i przekaż nazwę obiektu danych.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>Aby zatrzymać buforowanie obiektu danych  
  
1.  Wywołanie `StopCaching` metodę wystąpienia dokument lub arkusz i przekaż nazwę obiektu danych. W tym przykładzie założono, że <xref:System.Data.DataSet> o nazwie `dataSet1` , który chcesz zatrzymać buforowania.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Nie wywołuj `StopCaching` z obsługi zdarzeń dla `Shutdown` zdarzenia dokumentu lub arkusza. W czasie `Shutdown` zdarzenia, jest za późno do modyfikowania pamięci podręcznej danych. Aby uzyskać więcej informacji na temat `Shutdown` zdarzeń, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Buforowanie danych](../vsto/caching-data.md)   
 [Porady: dane z pamięci podręcznej do użycia w trybie Offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Porady: dane w dokumencie chroniony hasłem z pamięci podręcznej](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Zapisywanie danych](/visualstudio/data-tools/saving-data)  
  
  