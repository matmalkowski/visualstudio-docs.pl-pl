---
title: 'Porady: dane w dokumencie chroniony hasłem z pamięci podręcznej | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71ce65cd253ea6473a07a98542449a1e47ae9d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Porady: dane z pamięci podręcznej w dokumentach zabezpieczonych hasłem
  Możesz dodać dane do pamięci podręcznej danych w dokumencie lub skoroszytu, który jest chroniony hasłem, zmiany w pamięci podręcznej danych nie są zapisane automatycznie. Można zapisać zmian w pamięci podręcznej danych przez zastąpienie dwie metody w projekcie.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Buforowanie w dokumentach programu Word  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Do pamięci podręcznej danych w dokumencie programu Word, który jest chroniony hasłem  
  
1.  W `ThisDocument` klasy, oznacz pola publicznego lub właściwości pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).  
  
2.  Zastąpienie <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metoda `ThisDocument` klasy i usuwanie ochrony z dokumentu.  
  
     Po zapisaniu dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby zapewnić możliwość usunięcia ochrony dokumentu. Dzięki temu zmiany mają być zapisywane dane buforowane.  
  
3.  Zastąpienie <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metoda `ThisDocument` klasy i zastosuj je ponownie ochrony dokumentu.  
  
     Po zapisaniu dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby zapewnić możliwość ponownego zastosowania ochrony dokumentu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak dane w dokumencie programu Word, który jest chroniony hasłem z pamięci podręcznej. Przed kod usuwa ochronę w <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metody zapisuje bieżące <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> wartość tak, aby móc ponownie zastosować ten sam typ ochrony w <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metody.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Dodaj ten kod do `ThisDocument` klasy w projekcie. Ten kod przyjęto założenie, że hasło jest przechowywane w pole o nazwie `securelyStoredPassword`.  
  
## <a name="caching-in-excel-workbooks"></a>Buforowanie w skoroszytach programu Excel  
 W projektach programu Excel, ta procedura jest konieczne tylko wtedy, gdy cały skoroszyt za pomocą hasła są chronione przy użyciu <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metody. Ta procedura nie jest konieczne, jeśli chronione konkretnego arkusza za pomocą hasła przy użyciu <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metody.  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Do pamięci podręcznej danych w skoroszycie programu Excel, która jest chroniona hasłem  
  
1.  W `ThisWorkbook` klasy lub jednej z `Sheet` *n* klas, zaznacz pola publicznego lub właściwości pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).  
  
2.  Zastąpienie <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metoda `ThisWorkbook` klasy i usuwanie ochrony z tego skoroszytu.  
  
     Po zapisaniu skoroszytu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby zapewnić możliwość Wyłącz ochronę skoroszytu. Dzięki temu zmiany mają być zapisywane dane buforowane.  
  
3.  Zastąpienie <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metoda `ThisWorkbook` klasy i zastosuj je ponownie ochrony dokumentu.  
  
     Po zapisaniu skoroszytu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby zapewnić możliwość ponownego zastosowania ochrony w skoroszycie.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dane w skoroszycie programu Excel, która jest chroniona hasłem z pamięci podręcznej. Przed kod usuwa ochronę w <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metody zapisuje bieżące <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> i <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> wartości, tak aby ten sam typ ochrony może być stosowana w <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metody.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Dodaj ten kod do `ThisWorkbook` klasy w projekcie. Ten kod przyjęto założenie, że hasło jest przechowywane w pole o nazwie `securelyStoredPassword`.  
  
## <a name="see-also"></a>Zobacz też  
 [Buforowanie danych](../vsto/caching-data.md)   
 [Porady: dane z pamięci podręcznej do użycia w trybie Offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Instrukcje: Programowe buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  