---
title: 'Porady: programowane kojarzenie strony sieci Web z folderem programu Outlook | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5495066b05ded6fc49dfe92ed489932d8c75b24d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Porady: Programowane kojarzenie strony sieci Web z folderem programu Outlook
  W tym przykładzie sprawdza, czy folder o nazwie `HtmlView` w programie Microsoft Office Outlook. Jeśli folder nie istnieje, kod tworzy folder i przypisuje strony sieci Web. Jeśli folder istnieje, kod wyświetla zawartość folderu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Porady: programowane pobieranie folderu na podstawie nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Instrukcje: Programowe tworzenie niestandardowych elementów folderu](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  