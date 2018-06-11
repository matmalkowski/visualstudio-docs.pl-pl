---
title: 'Porady: programowane przenoszenie elementów w programie Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257725"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Porady: programowane przenoszenie elementów w programie Outlook
  W tym przykładzie przenosi nieprzeczytanych wiadomości e-mail z **skrzynki odbiorczej** do folderu o nazwie **testu**. Przykład tylko przenosi wiadomości, które mają wyraz **testu** w `Subject` pola.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Folderu poczty programu Outlook o nazwie **testu**.  
  
-   Wiadomość e-mail, przychodzący słowem **testu** w `Subject` pola.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z folderami](../vsto/working-with-folders.md)   
 [Porady: programowane pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Porady: programowane wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Porady: programowane wykonywanie akcji po odebraniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  