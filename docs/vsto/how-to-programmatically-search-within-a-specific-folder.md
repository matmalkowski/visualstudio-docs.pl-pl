---
title: "Porady: programowane wyszukiwanie w określonym folderze | Dokumentacja firmy Microsoft"
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], searching
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6397f6e90423640697aa57d7fdf2a1c85303d0f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Porady: Programowane wyszukiwanie w określonym folderze
  W tym przykładzie kodu używane `Find` i `FindNext` metody do wyszukiwania tekstu w polu podmiotu wiadomości e-mail, w której znajdują się **skrzynki odbiorczej**. Ta metoda używa filtru ciąg do wyszukania litera T jako początkowa litera `Subject` tekstu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Instrukcje: Programowe pobieranie folderu na podstawie nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  