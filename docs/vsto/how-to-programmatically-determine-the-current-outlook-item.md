---
title: 'Porady: programowane wyznaczanie bieżącego elementu programu Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 519fd1572b3ebb1faf8cc7adc6d5a9ba2773d67b
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257053"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Porady: programowane wyznaczanie bieżącego elementu programu Outlook
  W tym przykładzie użyto `Explorer.SelectionChange` zdarzenie, aby wyświetlić nazwę bieżącego folderu i niektóre informacje na temat wybranego elementu. Następnie kod wyświetla wybrany element.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Termin, skontaktuj się z pomocą i elementów poczty e-mail w programie Microsoft Office Outlook.  
  
## <a name="see-also"></a>Zobacz także  
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Porady: programowane pobieranie folderu według nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Porady: programowane wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  