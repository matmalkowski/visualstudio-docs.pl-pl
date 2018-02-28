---
title: "Porady: programowane przenoszenie elementów w programie Outlook | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 72b35bde8775a859ef15c5e18b381615974bccd7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Porady: Programowane przenoszenie elementów w programie Outlook
  W tym przykładzie przenosi nieprzeczytanych wiadomości e-mail z **skrzynki odbiorczej** do folderu o nazwie **testu**. Przykład tylko przenosi wiadomości, które mają wyraz **testu** w `Subject` pola.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Folderu poczty programu Outlook o nazwie **testu**.  
  
-   Wiadomości e-mail, przychodzący słowem **testu** w `Subject` pola.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Porady: programowane pobieranie folderu na podstawie nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Porady: programowane wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Instrukcje: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  