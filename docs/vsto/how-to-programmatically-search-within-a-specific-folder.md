---
title: 'Porady: programowane wyszukiwanie w określonym folderze'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64df4180e533f254927ae134ed005b0626dfdde8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677300"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Porady: programowane wyszukiwanie w określonym folderze
  W tym przykładzie kodu użyto `Find` i `FindNext` metody, aby wyszukać tekst w polu tematu wiadomości e-mail, które znajdują się w **skrzynki odbiorczej**. Ta metoda używa filtru ciągów pod kątem litera T jako początkowa litera `Subject` tekstu.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Porady: programowane pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  