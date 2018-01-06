---
title: 'Porady: programowane kojarzenie strony sieci Web z folderem programu Outlook | Dokumentacja firmy Microsoft'
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
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d2ce7291b992c4d2952853c502ade8fcd70f3791
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
  