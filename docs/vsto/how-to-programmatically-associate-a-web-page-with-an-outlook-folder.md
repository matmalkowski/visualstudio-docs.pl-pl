---
title: 'Porady: programowane kojarzenie strony sieci web z folderem programu Outlook'
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
ms.openlocfilehash: 2cb1ef525917288dc44609b899611db884da9073
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256468"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Porady: programowane kojarzenie strony sieci web z folderem programu Outlook
  W tym przykładzie sprawdza, czy folder o nazwie `HtmlView` w programie Microsoft Office Outlook. Jeśli folder nie istnieje, kod tworzy folder i przypisuje strony sieci Web. Jeśli folder istnieje, kod wyświetla zawartość folderu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Porady: programowane pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Porady: programowane Tworzenie niestandardowych elementów folderu](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  